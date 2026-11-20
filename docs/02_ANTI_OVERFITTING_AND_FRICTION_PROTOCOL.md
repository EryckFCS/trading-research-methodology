# 02 — Protocolo Anti-Overfitting y Matriz de Fricción

Toda hipótesis cuantitativa se evalúa contra estándares causales uniformes antes de considerarse elegible para observación Shadow en vivo.

---

## 1. Contrato estricto de causalidad en simulación

1. **Cierre completo de barra:** ninguna señal utiliza el precio de cierre ni el volumen de la barra en formación.
2. **Ejecución diferida:** toda señal evaluada en el cierre de barra `t` se ejecuta únicamente al precio de apertura de `t + 1` o con latencia explícita adicional.
3. **Resolución pesimista intrabarra:** cuando el máximo y mínimo de una barra tocan simultáneamente Stop Loss y Take Profit, se asume siempre ejecución previa del Stop Loss.
4. **Llenado pasivo estricto:** una orden límite pasiva solo se considera llenada cuando el precio cruza estrictamente el nivel límite y no por mero contacto superficial.
5. **Universo causal libre de sesgo de supervivencia:** la elegibilidad por volumen diario promedio móvil de `7` días e historia mínima de `14` días se evalúa en cada instante con información pasada únicamente.

---

## 2. Matriz obligatoria de `4` regímenes de fricción

Ningún modelo se valida bajo una única comisión optimista. Cada candidato debe reportar su comportamiento simultáneo frente a degradación progresiva de ejecución:

| Régimen de prueba | Costo ida y vuelta supuesto | Latencia adicional | Propósito del estrés |
| :--- | :--- | :--- | :--- |
| `MAKER_4BPS` | `4.0 bps` | `0` barras | Escenario límite inferior con alta tasa de llenado pasivo |
| `HYBRID_11BPS` | `11.0 bps` | `0` barras | Escenario realista con persecución híbrida pasiva y cierre a mercado |
| `SLIP_15BPS_LAT` | `15.0 bps` | `+1` barra | Sensibilidad a deslizamiento elevado y retraso operativo |
| `TAKER_23BPS` | `23.0 bps` | `0` barras | Escenario pesimista de cruce total a mercado como prueba de quiebre |

### Ejemplo de ablación comparativa `615` días comunes

| Estrategia y universo | `MAKER_4BPS` | `HYBRID_11BPS` | `SLIP_15BPS_LAT` | `TAKER_23BPS` | Diagnóstico |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Carry cross-sectional `120h` en `38` Large-Cap | `+2,775.10 USD` | `+2,621.20 USD` | `+2,739.30 USD` | `+2,357.20 USD` | Resiliente por rotación mínima cada `120h` |
| Multifactor `4h` en `286` perpetuos líquidos | `+7,318.30 USD` | `+6,391.00 USD` | `+5,606.00 USD` | `+4,546.30 USD` | Positivo en los `4` regímenes cuando hay dispersión amplia |
| Multifactor `4h` comprimido a `38` Large-Cap | `-92.40 USD` | `-1,591.20 USD` | `-3,948.90 USD` | `-4,160.50 USD` | Destruido por baja dispersión y costos frecuentes |

---

## 3. Ventanas solapadas vs Episodios Secuenciales y Block Bootstrap

Evaluar políticas de riesgo mediante ventanas móviles desplazadas cada pocos días crea dependencia artificial porque trayectorias adyacentes comparten casi todos sus días. Para medir incertidumbre real sin autoengaño:

1. **Episodios secuenciales estrictamente no solapados:** cada nuevo episodio inicia únicamente el día posterior al cierre o fallo del episodio anterior.
2. **Stationary Block Bootstrap de Politis y Romano:** se generan `5,000` trayectorias re-muestreadas preservando la autocorrelación diaria y los clústeres de volatilidad mediante longitudes de bloque aleatorias con media `L = 5`, `L = 10` y `L = 14` días.
3. **Validación temporal fuera de muestra:** partición cronológica `H1 Train` frente a `H2 OOS Test` más análisis por tercios secuenciales `T1`, `T2` y `T3`.

En pruebas reales sobre series de `615` días, eliminar el solapamiento desplazó la mediana de tiempo observado por fase de `7.0` días en ventanas móviles a un rango más honesto de `8.0` a `11.0` días entre bootstrap y episodios secuenciales, exponiendo de inmediato el riesgo real de quiebre por cohorte.

---

## 4. Transparencia ante múltiples pruebas y Deflated Sharpe Ratio

Cuando se exploran cientos de combinaciones paramétricas sobre la misma historia, parte del rendimiento máximo surge por azar estadístico. El protocolo exige:

- Registrar el conteo de ensayos `K` evaluados en campaña, por ejemplo `288` configuraciones en `EXP_039`.
- Calcular el **Deflated Sharpe Ratio** corrigiendo asimetría, curtosis y el máximo esperado bajo hipótesis nula entre `K` intentos.
- Congelar la configuración candidata mediante etiqueta inmutable antes de iniciar recolección prospectiva en vivo, evitando el sesgo de re-selección post-hoc.

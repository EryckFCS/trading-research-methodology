# 05 — Playbook de Publicación Técnica

Borradores listos para adaptar y publicar mostrando proceso científico, rigor de validación y capturas limpias en modo `?demo=1`. Mantener siempre etiquetado explícito entre backtest histórico y registro prospectivo en demo, evitando promesas de rentabilidad o lenguaje comercial.

---

## 1. Post para LinkedIn — El cementerio de estrategias refutadas

La mayoría en trading algorítmico publica solo curvas subiendo. En mi experiencia auditando estrategias sobre futuros perpetuos cripto, lo que más valor genera es documentar por qué mueren casi todas las ideas antes de tocar dinero real.

Al someter familias enteras de señales a barras de `1m`, ejecución diferida al siguiente abierto, prioridad pesimista de Stop Loss y comisiones realistas de `11` a `23 bps` ida y vuelta:

1. Una estrategia de reversión `5m` pasó de un `Profit Factor` bruto de `1.040` a `0.534` bajo costo Taker.
2. Una sonda real sobre Order Book Imbalance L2 en WebSocket confirmó señal predictiva positiva a `5` segundos con `+0.270 bps` brutos, pero completamente inoperables frente al piso minorista de `4.0 bps` Maker u `11.47 bps` Taker más spread.
3. Un comité ML con `PF 2.336` In-Sample cayó a `PF 0.862` en muestra verdadera fuera de muestra, demostrando sobreajuste.
4. Una cartera cross-sectional de `4h` positiva en `286` activos se volvió negativa al comprimirla a `38` Large-Caps por colapso de dispersión.

Publicar un "cementerio de estrategias refutadas" en un repositorio abierto de metodología disciplina la investigación más que cualquier backtest optimizado.

Proyecto de investigación cuantitativa en entorno simulado y demo. No constituye asesoría financiera.

---

## 2. Post para LinkedIn — Por qué congelé un hash antes de recolectar evidencia en vivo

Cuando alguien prueba docenas de configuraciones sobre `9` meses de datos y elige la mejor, es fácil confundir suerte con ventaja real. Incluso evaluando por ventanas móviles solapadas se sobreestima el tamaño de muestra independiente.

Para corregirlo implementé cuatro reglas:
1. Episodios secuenciales estrictamente no solapados más `5,000` trayectorias de Stationary Block Bootstrap.
2. Pruebas sistemáticas bajo `4` niveles de fricción y latencia creciente.
3. Modo captura anonimizada en mi terminal de monitoreo con saldos ocultos e IDs enmascarados.
4. Congelación del commit de configuración antes de iniciar la recolección semanal en vivo sin editar parámetros sobre la marcha.

En `90` días de seguimiento prospectivo sin ediciones retrospectivas la evidencia habla sola.

---

## 3. Hilo para X — `5` publicaciones

**Post 1 de 5:** Probé decenas de hipótesis de trading algorítmico en cripto con datos de hasta `720` días. Casi todas murieron cuando añadí comisiones reales, latencia y pruebas fuera de muestra. Abro este hilo con lo que realmente aprendí al construir un cementerio de estrategias refutadas.

**Post 2 de 5:** Trampa 1 — Señales microestructurales verdaderas pero invendibles: medir Order Book Imbalance L2 por WebSocket mostró poder predictivo real a `5` segundos con `+0.270 bps`. El problema es matemático: un usuario minorista paga al menos `4.0 bps` Maker y más de `11 bps` Taker. La idea muere por estructura de mercado, no por código.

**Post 3 de 5:** Trampa 2 — Liquidaciones en velas finas: en velas de `15m` un rebote tras cascada de OI parecía marginalmente positivo sin comisiones. Al auditar minuto a minuto en `1m`, todas las variantes empeoraron porque la caída barre primero el Stop Loss antes de rebotar.

**Post 4 de 5:** Trampa 3 — Sobreajuste ML en muestras cortas: un comité con `PF 2.336` dentro de muestra colapsó a `0.862` fuera de muestra. Desde entonces todo candidato exige validación purgada, Deflated Sharpe Ratio, episodios no solapados y `5,000` rutas de Block Bootstrap.

**Post 5 de 5:** En lugar de publicar capturas de dinero, dejé pública solo la metodología y el cementerio de refutaciones, mientras recolecto `90` días de datos en vivo bajo una configuración congelada y un dashboard con modo demo anonimizado. El proceso auditable vale más que el hype.

---

## 4. Guion corto para TikTok e Instagram Reel — `40` segundos

**Visual en pantalla:** grabación limpia de `http://127.0.0.1:8088/?demo=1` sin pestañas ni barras extra, mostrando las pestañas del terminal y el modo demo activo.

- **Segundos `0` a `6` — Gancho:** Así luce por dentro un motor cuantitativo que evalúa criptoactivos cada hora sin tocar un solo saldo real en pantalla.
- **Segundos `6` a `18` — Hallazgo de refutación:** Antes de llegar a esta arquitectura, probé estrategias rápidas de cinco minutos y casi todas murieron cuando apliqué comisiones reales del exchange y auditoría minuto a minuto.
- **Segundos `18` a `30` — Ingeniería del sistema:** Por eso separé el proyecto en tres capas: control de riesgo automático con disyuntor diario, modelos estadísticos validados fuera de muestra y neteo entre motores para no pagar comisiones duplicadas.
- **Segundos `30` a `40` — Cierre y transparencia:** Congelé la configuración en demo para medir noventa días en vivo sin editar parámetros. El enlace al repositorio abierto con las estrategias que fallaron está en mi perfil. Investigación técnica, no asesoría financiera.

---

## 5. Carrusel de Instagram — `5` láminas

1. **Lámina 1 — Portada:** Por qué publico las estrategias de trading que fallaron antes que las que ganan.
2. **Lámina 2 — El filtro de la fricción:** Cómo `4 bps`, `11 bps` y `23 bps` destruyen estrategias rápidas que en bruto parecían ganadoras.
3. **Lámina 3 — Tres errores caros evitados:** Overfitting de ML, cointegración inestable y pérdida de dispersión en universos pequeños.
4. **Lámina 4 — Arquitectura en 3 capas:** Riesgo independiente, validación AFML sin data leakage y monitoreo anonimizado en vivo.
5. **Lámina 5 — Compromiso prospectivo:** Configuración congelada y bitácora semanal abierta sin promesas de rentabilidad ni asesoría financiera.

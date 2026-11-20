# 01 — Cementerio Empírico de Estrategias Refutadas

Publicar únicamente ganadores crea sesgo de supervivencia. Esta bitácora sintetiza familias completas de estrategias evaluadas sobre futuros perpetuos cripto durante ventanas reales de `90` a `720` días, mostrando por qué fallaron al pasar de hipótesis teórica a ejecución realista fuera de muestra.

---

## Resumen comparativo de refutaciones

| Familia investigada | Muestra y frecuencia | Métrica bruta o In-Sample | Resultado realista OOS o con fricción | Diagnóstico raíz de refutación |
| :--- | :--- | :--- | :--- | :--- |
| Cointegración y StatArb de pares intra-sector | `181d` a `241d`, `92` pares | Ventana inicial favorable de `36d` | `C38_INTRA_NO_RF`: `737` trades, `PF 0.75`, `-1,645.67 USD`; `C38_INTRA_RF`: `974` trades, `PF 0.81` y `PF 0.62` Taker | En `240d` la velocidad de reversión en altcoins no compensa `11` a `23 bps` por rotación |
| Walk-Forward mensual en pares cointegrados | `240d` | Ajuste dinámico mensual por cointegración | `C2_Pinza_Homog_MonthlyWF_Top6`: `426` trades, `49.1%` win rate, `PF 0.564`, `-1,289.32 USD` | Inestabilidad estructural de vectores cointegrados tras régimen |
| Comités ML v12 y v13 sobre Dollar Bars | `15` activos, cola OOS `30%` | `committee_v12` In-Sample `PF 2.336`, `+6,560.19` | True OOS `742` trades: `PF 0.862`, `-725.83 USD` Maker; `PF 0.767`, `-1,294.03 USD` Taker; `v13` `1,172` trades: `PF 0.783` Maker y `0.692` Taker | Sobreajuste severo sobre distribuciones de muestra corta y pérdida fuera de muestra |
| Microestructura HFT en velas de `5m` | `9,844` y `6,330` trades | `5M_EXHAUSTION_REVERT` bruto `0 bps`: `PF 1.040`, `+84.81%` | `5M_EXHAUSTION_REVERT`: `PF 0.755` y `-611.49%` en `11 bps`; `PF 0.534` y `-1,371.09%` en `23 bps`; `5M_OFI_MOMENTUM`: `PF 0.496` Taker | Frecuencia minorista devorada por la estructura de comisiones |
| Reversión tras cascadas de liquidación OI | `720d` `15m` en `38` activos más auditoría `1m` `90d` | `LIQ3_EXTREME_1H_FLUSH` bruto `0 bps`: `+8.42 bps`, `PF 1.077` | `4` de `5` variantes pierden antes de comisiones; en `1m` intrabar todas pierden incluso a `0 bps`, hasta `-42.20 bps` por trade | La caída inicial tras liquidaciones continúa antes de estabilizarse y barre los stops |
| Scalping directo sobre Order Book Imbalance L2 | Sonda en vivo WebSocket `357` snapshots | Correlación positiva a `5s`: bruto agregado `+0.270 bps` | Piso mínimo minorista `4.0 bps` Maker y `11.47 bps` Taker más spread | Edge microestructural real en `5s`, pero inalcanzable sin tarifas institucionales `0 bps` o rebate |
| Campaña scalping `1m` y Meta-Labeling ML | Datos reales `1m`, olas `EXP_034` a `EXP_038` | Hipótesis de dislocaciones, mechas, funding clock y BTC Dollar Bars | Dollar Bars BTC `-6.23 bps` neto Hybrid; Ranker ML con Walk-Forward purgado `AUC = 0.508` con todas las carteras negativas | Señal de muy corto horizonte indistinguible de ruido tras costo de cruce |
| Compresión de universo cross-sectional `4h` | `615d` comunes, `38` Large-Caps vs `286` perpetuos líquidos | Sobre `286` activos: `+6,391.00 USD` Hybrid `11 bps` | Restringido a `38` Large-Caps: `-92.40 USD` en `4 bps`, `-1,591.20 USD` en `11 bps`, `-4,160.50 USD` en `23 bps` | La dispersión cross-sectional colapsa en universos estrechos y los rebalanceos cada `4h` anulan el alfa |

---

## Cinco lecciones cuantitativas extraídas

1. **Separar siempre ventaja estadística bruta de viabilidad comercial:** un predictor a `5` segundos con correlación positiva `+0.31` en L2 OBI puede ser científicamente verdadero y económicamente inoperable bajo comisiones minoristas.
2. **Validar intrabar a resolución fina antes de celebrar resultados:** usar barras de `15m` o `1h` oculta colisiones de Stop Loss antes que Take Profit; auditar con velas de `1m` expuso de inmediato que el flush de liquidaciones perfora stops antes del rebote.
3. **Desconfiar de brechas grandes entre In-Sample y True OOS:** una caída desde `PF 2.336` In-Sample hasta `PF 0.862` OOS señala sobreparametrización estructural y obliga a descartar el modelo completo sin rescates cosméticos.
4. **La cobertura beta agresiva puede destruir el factor mismo:** neutralizar beta contra BTC en señales intradía eliminó parte sustancial de la dispersión rentable en `EXP_037`.
5. **El tamaño del universo forma parte inseparable de la hipótesis:** en factores cross-sectional con rotación cada pocas horas, reducir de `286` activos a `38` cambia el signo económico de la estrategia aunque la fórmula del factor sea idéntica.

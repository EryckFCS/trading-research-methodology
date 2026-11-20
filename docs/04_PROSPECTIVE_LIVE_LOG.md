# 04 — Bitácora Prospectiva Congelada

Los resultados en backtest constituyen únicamente hipótesis calibradas. La validez real fuera de muestra se construye acumulando evidencia prospectiva verificable con configuración congelada de antemano.

---

## 1. Reglas de integridad del registro prospectivo

1. **Línea base congelada:** la configuración vigente queda fijada el `19 de noviembre de 2026` bajo la etiqueta privada inmutable `prospective/cft-triple-overlay-live-v14.1` con ejecución única reconciliada por libro neto en cuenta Demo UTA.
2. **Prohibición de edición silenciosa:** durante la ventana de recolección prospectiva no se ajustan pesos de mezcla, umbrales de liquidez ni reglas de salida sobre la marcha; cualquier cambio futuro abre un nuevo ciclo etiquetado desde cero.
3. **Separación de entorno:** los registros reportados aquí provienen de ejecución en vivo sobre cuenta Demo UTA con reconciliación única del portafolio multi-manga y datos reales de mercado. No representan rendimientos con capital real en producción.
4. **Métricas normalizadas:** siguiendo el estándar de transparencia sin ostentación de saldos privados, las actualizaciones semanales reportan retorno porcentual sobre base inicial, drawdown máximo porcentual observado, tasa de cumplimiento de compuertas de riesgo y paridad frente a supuestos de fricción.

---

## 2. Registro semanal acumulativo

| Corte | Fecha UTC | Días acumulados | Retorno neto Demo / Overlay pct | Drawdown máximo pct | Fricción medida o cumplida | Incidencias operativas y estado |
| :--- | :--- | ---: | :--- | :--- | :--- | :--- |
| Semana `0` — Inicio congelado | `2026-11-20` | `0` | `0.00%` base tras apertura inicial | `0.00%` | Gate `< 23 bps` activo | Línea base congelada en `v14.1.0`; portafolio consolidado reconciliado en vivo sin errores en cuenta Demo UTA |

---

## 3. Cómo leer estas actualizaciones

- **Corte semanal honesto:** tanto las semanas positivas como las semanas en pérdida o planas se registran sin omisiones.
- **Horizonte mínimo significativo:** extraer conclusiones estadísticas serias en un portafolio de horizonte `1h` a `120h` requiere acumular al menos de `30` a `90` días continuos de observación prospectiva real.

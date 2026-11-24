
# Brief del proyecto

## 1. Nombre del proyecto

Análisis de eficiencia y productividad industrial.

## 2. Contexto

La eficiencia de los procesos productivos es fundamental
para el aprovechamiento de los recursos, el cumplimiento
de los estándares de producción y la competitividad
de las organizaciones industriales.

Este proyecto busca transformar datos simulados de
producción en información útil para identificar
desviaciones en el desempeño operativo y oportunidades
de mejoramiento continuo.

## 3. Pregunta de negocio

¿Qué líneas de producción, máquinas, turnos y productos
presentan mayores desviaciones frente a las metas de
eficiencia y cómo se relacionan estas desviaciones
con los tiempos improductivos?

### Preguntas secundarias

- ¿Qué máquinas presentan menor eficiencia productiva?
- ¿Qué turnos presentan mayor cumplimiento de las metas?
- ¿Qué productos presentan mayores desviaciones frente
  a la producción esperada?
- ¿Cómo evoluciona la eficiencia durante el año?
- ¿Qué recursos presentan mayores tiempos improductivos?
- ¿Dónde se deberían priorizar las oportunidades de mejora?

## 4. Quién decide

La dirección de producción, con el apoyo de los
supervisores, ingeniería de procesos y el área de
mejoramiento continuo.

Los resultados permitirán priorizar intervenciones,
evaluar estándares productivos e identificar
oportunidades de optimización de los recursos.

## 5. Fuente de datos

La fuente corresponde al archivo
`Dataset_Productividad_.xlsx`, que contiene datos
simulados con fines académicos.

- Formato: Excel (.xlsx).
- Número de hojas: 2.
- Registros productivos: 10.489.
- Columnas productivas: 18.
- Periodo simulado: enero a diciembre de 2026.
- Líneas de producción: 3.
- Máquinas: 12.
- Productos: 12.
- Turnos: 3.
- Identificadores ficticios de operarios: 24.
- Unidad: unidades equivalentes de producción simuladas.

Las líneas productivas son:

- Línea A: Mezclado.
- Línea B: Moldeado.
- Línea C: Acabado.

Según la documentación del dataset, los datos son
100% simulados y no representan una empresa real.

## 6. Alcance

- Análisis exploratorio y validación de calidad de datos.
- Comparación de producción real y esperada.
- Evaluación de la eficiencia productiva.
- Análisis del cumplimiento de metas de eficiencia.
- Análisis por línea, máquina, turno y producto.
- Identificación de tendencias temporales.
- Evaluación de tiempos improductivos eficientes
  e ineficientes.
- Identificación de recursos con mayores desviaciones.
- Priorización de oportunidades de mejoramiento continuo.

## 7. Qué NO incluye

- Evaluación del desempeño de trabajadores reales.
- Análisis de nómina, salarios o incentivos.
- Análisis financiero y costos de producción.
- Predicción de fallas de maquinaria.
- Implementación de mejoras en una planta real.
- Identificación de causas específicas de improductividad.
- Demostración de relaciones causales entre variables.
- Cálculo del OEE completo, debido a la ausencia
  de todas las variables necesarias.

## 8. Indicadores principales

| Indicador | Descripción |
|---|---|
| Producción real | Cantidad de producción registrada. |
| Producción esperada | Cantidad de producción esperada ajustada. |
| Eficiencia productiva | Producción real / esperada * 100. |
| Meta de eficiencia | Objetivo establecido de eficiencia. |
| Brecha de eficiencia | Diferencia entre eficiencia y meta en puntos porcentuales. |
| Cumplimiento de meta | Proporción de registros que alcanzan o superan la meta. |
| Horas improductivas eficientes | Tiempo improductivo clasificado como eficiente. |
| Horas improductivas ineficientes | Tiempo improductivo clasificado como ineficiente. |

## 9. Riesgos de calidad de datos

- Representatividad limitada: los datos son simulados
  y no representan una operación industrial real.
- Diferencia de escalas: la eficiencia se expresa
  en porcentaje y la meta como proporción decimal.
- Agregación incorrecta: promediar porcentajes puede
  generar resultados distorsionados.
- Redundancia temporal: existen varias columnas
  derivadas de la fecha que deben ser consistentes.
- Posibles valores superiores al 100%: deben
  interpretarse como superación del esperado.
- Doble contabilización: las variables de producción
  normal e Inv no deben sumarse entre sí.
- Ausencia de información sobre las causas específicas
  de los tiempos improductivos.
- Posibles inconsistencias en futuras actualizaciones,
  como duplicados, valores nulos o denominadores cero.

## 10. Resultado esperado

Obtener un diagnóstico descriptivo del desempeño
productivo que permita identificar recursos críticos,
desviaciones frente a los estándares y oportunidades
de mejoramiento continuo mediante el análisis de datos.

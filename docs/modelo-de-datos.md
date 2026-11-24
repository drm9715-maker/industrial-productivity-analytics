
# Modelo de datos

## 1. Descripción general

El dataset contiene registros simulados de producción,
eficiencia y tiempos improductivos de una planta
industrial ficticia.

- Archivo: Dataset_Productividad_.xlsx.
- Formato: Excel (.xlsx).
- Número de hojas: 2.
- Registros productivos: 10.489.
- Columnas productivas: 18.
- Fecha inicial: 2026-01-01.
- Fecha final: 2026-12-31.
- Unidad: unidades equivalentes de producción simuladas.

El dataset tiene una estructura tabular plana y no
corresponde a una base de datos relacional.

## 2. Estructura del archivo

| Hoja | Registros | Columnas | Descripción |
|---|---:|---:|---|
| Produccion sintetica | 10489 | 18 | Registros productivos simulados. |
| Acerca del dataset | 6 | 2 | Metadatos y definiciones del dataset. |

## 3. Granularidad

Cada fila de la hoja Produccion sintetica representa
un registro productivo asociado a una fecha, turno,
máquina, identificador ficticio de operario y producto.

Esta granularidad permite analizar el desempeño
productivo por periodo, línea, máquina, turno y producto.

## 4. Diccionario de datos

### 4.1. Hoja Produccion sintetica

| Columna | Tipo lógico | Descripción | Ejemplo |
|---|---|---|---|
| Mes - Año | Texto | Periodo mensual en formato AAAA-MM. | 2026-01 |
| Año | Entero | Año del registro productivo. | 2026 |
| Mes | Entero | Número del mes. | 1 |
| Mes1 | Texto | Número y nombre del mes. | 01_Enero |
| Desc. G. Recursos | Texto | Línea o grupo de recursos productivos. | Linea A - Mezclado |
| Fecha | Fecha | Fecha del registro productivo. | 2026-01-01 |
| Turno | Entero | Identificador del turno de trabajo. | 1 |
| ID Recurso | Texto | Identificador ficticio de la máquina. | MAQ-001 |
| Contrato | Texto | Identificador ficticio del operario. | OP-002 |
| Desc. Referencia | Texto | Nombre del producto fabricado. | Producto 02 |
| Suma Producción | Decimal | Cantidad real producida en unidades equivalentes. | 634.54 |
| Suma Esperado | Decimal | Producción esperada ajustada por horas improductivas justificadas. | 776 |
| Eficiencia % | Decimal | Relación porcentual entre producción real y esperada. | 81.7706 |
| Suma Producción (Inv) | Decimal | Producción registrada en la variante Inv. | 634.54 |
| Suma Esperado (Inv) | Decimal | Capacidad teórica de producción para 8 horas. | 776 |
| Hrs. Improd (Ef.) | Decimal | Horas improductivas clasificadas como eficientes. | 0 |
| Hrs. Improd (Inef.) | Decimal | Horas improductivas clasificadas como ineficientes. | 0 |
| Meta | Decimal | Objetivo de eficiencia expresado como proporción. | 0.85 |

Los ejemplos corresponden al primer registro
de producción del dataset simulado.

No se observaron valores nulos en las 18 columnas.

### 4.2. Hoja Acerca del dataset

| Columna | Tipo lógico | Descripción |
|---|---|---|
| Campo | Texto | Nombre del concepto documentado. |
| Descripción | Texto | Definición o explicación del concepto. |

Esta hoja contiene información sobre:

- Origen de los datos.
- Periodo de análisis.
- Unidad de producción.
- Fórmula de eficiencia.
- Definición del esperado Inv.
- Naturaleza ficticia del identificador Contrato.

## 5. Dominios de las variables

| Variable | Dominio |
|---|---|
| Año | 2026 |
| Mes | 1 a 12 |
| Turno | 1, 2 y 3 |
| ID Recurso | 12 identificadores de máquinas |
| Contrato | 24 identificadores ficticios de operarios |
| Desc. Referencia | 12 productos |
| Meta | 0.85, 0.88 y 0.90 |
| Desc. G. Recursos | Linea A - Mezclado, Linea B - Moldeado, Linea C - Acabado |

## 6. Identificadores y llaves

El dataset no contiene una columna definida
explícitamente como llave primaria.

Se identifica la siguiente clave compuesta candidata:

- Fecha.
- Turno.
- ID Recurso.
- Contrato.
- Desc. Referencia.

Durante la revisión de los 10.489 registros no se
encontraron repeticiones de esta combinación.

Por lo tanto, permite identificar de manera única
los registros del archivo actual.

Su unicidad deberá validarse en futuras actualizaciones.

## 7. Relaciones

No existen relaciones físicas mediante llaves entre
las dos hojas del archivo.

La hoja Acerca del dataset documenta los conceptos
utilizados en la hoja Produccion sintetica.

Dentro de la tabla productiva se identifican
las siguientes agrupaciones conceptuales:

- Tiempo: Fecha, Año, Mes, Mes1 y Mes - Año.
- Recursos: ID Recurso y Desc. G. Recursos.
- Turnos: Turno.
- Operarios ficticios: Contrato.
- Productos: Desc. Referencia.
- Métricas: producción, esperado, eficiencia,
  meta y horas improductivas.

Estas agrupaciones podrían utilizarse posteriormente
para construir un modelo dimensional tipo estrella,
previa validación de las relaciones y cardinalidades.

## 8. Reglas de negocio e indicadores

### 8.1. Eficiencia productiva

Eficiencia (%) = Suma Producción / Suma Esperado * 100

La eficiencia puede superar el 100% cuando la
producción real supera la producción esperada.

Para calcular la eficiencia agregada se recomienda:

Eficiencia agregada (%) =
SUMA(Producción) / SUMA(Esperado) * 100

No se recomienda promediar directamente los porcentajes
cuando los registros tienen diferentes esperados.

### 8.2. Meta de eficiencia

La meta se almacena como proporción decimal.

Meta (%) = Meta * 100

Ejemplo:

- Meta almacenada: 0.85.
- Meta porcentual: 85%.

### 8.3. Brecha de eficiencia

Brecha (pp) = Eficiencia (%) - Meta (%)

Interpretación:

- Brecha positiva: supera la meta.
- Brecha igual a cero: cumple exactamente la meta.
- Brecha negativa: no alcanza la meta.

### 8.4. Cumplimiento de meta

Un registro cumple la meta cuando:

Eficiencia (%) >= Meta * 100

El porcentaje de cumplimiento se calcula dividiendo
la cantidad de registros que cumplen la meta entre
el total de registros evaluados y multiplicando por 100.

### 8.5. Producción esperada Inv

Según la documentación del dataset, el esperado Inv
representa la capacidad teórica de producción para
una jornada de 8 horas.

La producción esperada ajustada descuenta las
horas improductivas justificadas.

Ambas variables deben analizarse por separado.

### 8.6. Horas improductivas

Se propone calcular las horas improductivas totales
como la suma de las horas improductivas eficientes
e ineficientes, previa validación de que ambas
categorías sean excluyentes.

## 9. Diagnóstico inicial de calidad

| Validación | Resultado |
|---|---|
| Registros productivos | 10489 |
| Columnas productivas | 18 |
| Valores nulos | 0 |
| Repeticiones de la clave candidata | 0 |
| Líneas productivas distintas | 3 |
| Máquinas distintas | 12 |
| Productos distintos | 12 |
| Operarios ficticios distintos | 24 |
| Turnos distintos | 3 |

## 10. Reglas de validación

- Verificar que la fecha corresponda al periodo definido.
- Validar la consistencia entre Fecha, Año y Mes.
- Verificar los dominios de turnos y recursos.
- Validar la unicidad de la clave candidata.
- Identificar valores nulos.
- Verificar que la producción esperada sea mayor a cero.
- Validar que los tiempos improductivos sean no negativos.
- Homogeneizar las escalas de eficiencia y meta.
- Evitar la doble contabilización de las columnas Inv.
- Contrastar la eficiencia registrada con la calculada.
- Utilizar denominadores consistentes al agregar datos.

## 11. Limitaciones

- El dataset contiene información simulada.
- No se dispone de causas específicas de improductividad.
- No se cuenta con información de costos de producción.
- No se dispone de variables suficientes para calcular
  el OEE completo.
- Las conclusiones no pueden generalizarse a una
  planta industrial real.

## 12. Confidencialidad

Según la documentación del archivo, los datos son
100% simulados y no representan una empresa real.

Los identificadores de máquinas, productos y operarios
son ficticios y se utilizan con fines académicos.

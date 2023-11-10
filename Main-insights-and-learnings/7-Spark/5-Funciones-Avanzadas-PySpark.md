# Índice del Archivo Funciones-Avanzadas-PySpark

Se resume a continuación lo trabajado en el archivo [5-Funciones-Avanzadas-PySpark.ipynb](/Main-insights-and-learnings/7-Spark/5-Funciones-Avanzadas-PySpark.ipynb). 

1. **Creación de la Sesión de Spark:**
   - Inicio de la sesión de Spark utilizando `SparkSession.builder.getOrCreate()`.

2. **Creación de DataFrames:**
   - Creación de DataFrames para empleados (`emp`) y departamentos (`dept`).

3. **Creación de Tablas Temporales:**
   - Uso de `createOrReplaceTempView` para crear tablas temporales para DataFrames.

4. **Expresiones SQL:**
   - Demostración del uso de expresiones SQL para manipulación de datos.
   - Categorización de salarios en bajo, medio y alto mediante `expr` y `selectExpr`.

5. **Funciones Definidas por el Usuario (UDF):**
   - Implementación de una función Python para determinar niveles salariales.
   - Registro de la función como UDF (`udf`) y aplicación en el DataFrame.

6. **Trabajo con Valores NULL:**
   - Utilización de funciones como `isNull()`, `isNotNull()`, `fillna()`, y `dropna()` para manejar valores nulos.

7. **Particionamiento:**
   - Exploración del particionamiento para controlar el paralelismo de la aplicación Spark.
   - Ejemplos de incremento y disminución del número de particiones.

8. **Configuración de Particiones a Nivel de Aplicación:**
   - Configuración del número de particiones a nivel de aplicación Spark mediante `spark.conf.set`.

Este archivo PySpark abarca desde la creación de sesiones hasta la optimización del rendimiento con técnicas como particionamiento.
# Fundamentos de Spark SQL

Se resume a continuación lo trabajado en el archivo [4-DataFrames-Spark-SQL.ipynb](/Main-insights-and-learnings/7-Spark/4-DataFrames-Spark-SQL.ipynb).

1. **Inicio de la Sesión de Spark:** Creamos una sesión de Spark usando `SparkSession.builder.getOrCreate()`.

2. **Creación de DataFrames:** Creamos DataFrames a partir de listas y también a partir de un archivo CSV usando `spark.read.csv()`.

3. **Operaciones Básicas:** Realizamos operaciones básicas como contar filas, obtener columnas, obtener tipos de datos y ver el esquema del DataFrame.

4. **Operaciones en DataFrames:** Realizamos operaciones como `select`, `filter`, y `drop` para manipular el DataFrame.

5. **Agregaciones:** Utilizamos la función `groupBy` para realizar agregaciones como contar, sumar, encontrar el máximo, mínimo y el promedio.

6. **Ordenamiento:** Ordenamos el DataFrame en orden ascendente y descendente.

7. **Columnas Derivadas:** Creamos una nueva columna derivada de las columnas existentes usando `withColumn`.

8. **Joins:** Realizamos diferentes tipos de joins entre DataFrames.

9. **Consultas SQL:** Registramos un DataFrame como una vista temporal y ejecutaste consultas SQL en él.

10. **Creación y Guardado de DataFrames a partir de CSV:** Creamos un DataFrame a partir de un archivo CSV y también guardamos un DataFrame como un archivo CSV.

**Nota: Puedes obtener el csv que se ha trabajo en este ejemplo a través del siguiente enlace: [WorldCupPlayers.csv](https://drive.google.com/file/d/1-lZ-6ImOtP0N1s-dCbMdp4EEpJk1ZThU/view?usp=sharing)**

## Enlaces de interés 🔗

- [Spark SQL](https://spark.apache.org/sql/)
- [Spark SQL Guide](https://spark.apache.org/docs/latest/sql-programming-guide.html)
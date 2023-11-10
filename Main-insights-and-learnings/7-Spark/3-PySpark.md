# Guía para Trabajar con PySpark en Jupyter Notebook

En esta guía, aprenderás cómo trabajar con PySpark en Jupyter Notebook para el análisis de datos y procesamiento a gran escala. PySpark es la interfaz de Python para el framework de procesamiento de datos distribuidos Apache Spark.

**Nota: También puedes ver el archivo de [PySpark en Jupyter Notebook](3-PySpark-JupyterNotebook.ipynb). Puedes obtener el csv que se ha trabajo en este ejemplo a través del siguiente enlace: [cereal.csv](https://drive.google.com/file/d/1fEkBoacXZLnz2kl2OZyG1xjhrl0vbRAC/view?usp=sharing)**

![Comprobación Spark](/Main-insights-and-learnings/7-Spark/img/test_spark.png)

## Paso 1: Instalar PySpark

Antes de comenzar, asegúrate de tener instalado PySpark. Puedes instalarlo a través de pip:

```bash
pip install pyspark
```

## Paso 2: Iniciar una Sesión de Spark

Para trabajar con PySpark, primero debes iniciar una sesión de Spark. Esto se hace utilizando `SparkSession`. Aquí está el código para iniciar una sesión de Spark:

```python
import org.apache.spark.sql.SparkSession

# Iniciar una sesión de Spark
spark = SparkSession.builder.appName("pysparkdf").getOrCreate()
```

## Paso 3: Cargar un Conjunto de Datos

Puedes cargar conjuntos de datos en formato CSV o Parquet utilizando PySpark. A continuación se muestra un ejemplo de cómo cargar un archivo CSV:

```python
# Leer un archivo CSV y crear un DataFrame
df = spark.read.option("header", "true").csv("ruta/del/archivo.csv")
```

## Paso 4: Explorar el Conjunto de Datos

### Mostrar los primeros registros:

```python
# Mostrar los primeros 10 registros del DataFrame
df.show(10)
```

### Ver el esquema de los datos:

```python
# Ver el esquema del DataFrame
df.printSchema()
```

## Paso 5: Realizar Operaciones en el DataFrame

### Seleccionar columnas:

```python
# Seleccionar columnas "name", "mfr" y "rating"
df.select('name', 'mfr', 'rating').show(10)
```

### Cambiar el tipo de datos de una columna:

```python
# Cambiar el tipo de datos de la columna "calories" a entero
df.withColumn("Calories", df['calories'].cast("Integer")).printSchema()
```

## Paso 6: Operaciones Avanzadas

### Agrupar y realizar funciones de agregación:

```python
# Agrupar por "name" y "calories" y contar las filas en cada grupo
df.groupBy("name", "calories").count().show()
```

### Ordenar el DataFrame:

```python
# Ordenar el DataFrame por la columna "protein"
df.orderBy("protein").show()
```

### Realizar operaciones condicionales:

```python
from pyspark.sql.functions import when

# Crear una nueva columna que indica si el valor de "vitamins" es mayor o igual a 25
df.select("name", when(df.vitamins >= "25", "rich in vitamins")).show()
```

## Paso 7: Filtrar Datos

### Filtrar filas según una condición:

```python
# Filtrar las filas donde la columna "calories" sea igual a 100
from pyspark.sql.functions import filter
df.filter(df.calories == "100").show()
```

### Filtrar filas que contengan valores nulos:

```python
# Filtrar las filas que contienen un valor nulo en la columna "name"
val filteredDF = df.filter(df("name").isNotNull())

filteredDF.show()
```

### Filtrar filas que no contengan valores nulos:

```python
# Filtrar las filas que no contienen un valor nulo en la columna "name"
df.filter(df.name.isNull()).show()
```

## Paso 8: Conclusiones

- Hemos aprendido cómo trabajar con PySpark en Jupyter Notebook.
- Hemos realizado operaciones básicas y avanzadas en un DataFrame de PySpark, incluyendo selección, cambio de tipo de datos, agregación, ordenación y filtrado de datos.
- También hemos explorado cómo manejar valores nulos en un DataFrame.

![Archivo PySpark en Jupyter notebook](/Main-insights-and-learnings/7-Spark/img/pyspark-jupyter-notebook.png)
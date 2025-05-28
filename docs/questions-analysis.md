# Análisis de Preguntas: Informe de Felicidad Mundial

Este documento responde a una serie de preguntas analíticas utilizando los **datos del World Happiness Report de 2020 y 2021**. Cada ejercicio se enfoca en una pregunta específica relacionada con la felicidad, el Producto Interno Bruto (GDP), y la expectativa de vida, entre otros indicadores.

## 1. ¿Cuál fue el país más feliz del mundo en 2021?

**Respuesta:**

- El país con el mayor `Ladder score` en 2021 fue **Finlandia**.

**Método:**

- Se filtró el DataFrame por el año 2021.
- Se usó `max()` sobre la columna `Ladder score` para obtener el país con el valor más alto.

## 2. ¿Cuál fue el país más feliz por continente?

**Respuesta:**

- **Finlandia** es el país más feliz en Europa, **Israel** en África, **Nueva Zelanda** en América y **Taiwán** en Asia.

**Método:**

- Obtención de valores únicos de la columna `Regional indicator` en la data del año 2021. Estos valores representan las regiones geográficas.
- Creación de un diccionario auxiliar (`region_to_country`) para mapear las regiones a sus respectivos continentes.
- Creación de una nueva columna (`Continent`) en la data del año 2021, basada en la columna `Regional indicator`. Esto permitió asignar a cada país su continente correspondiente.
- Agrupar los datos por continente y encontrar el país con el mayor `Ladder score` en cada uno.

## 3. ¿Qué país ocupó más veces el primer lugar entre 2005 y 2021?

**Respuesta:**

- **Finlandia y Dinamarca han compartido el primer lugar en siete ocasiones cada una entre 2005 y 2021,** empatando como los países más felices en este período..

**Método:**

- Con `groupby()` e `idxmax()`: agrupando los datos por año y seleccionando el país con el mayor valor de `Life Ladder`.
- Con `max()`, `lambda` y `.items()`: extrayendo manualmente los valores máximos de felicidad por año y asociándolos con sus respectivos países.
- Con columna de `Rank`: generando un ranking por año según el valor de `Life Ladder` y filtrando por rango igual a 1.

## 4. ¿En qué posición del ranking de felicidad estaba el país con mayor GDP per cápita en 2020?

**Respuesta:**

- El país con mayor GDP per cápita en 2020 fue **Irlanda**, con un `Life Ladder` de 7.035.

**Método:**

- Se filtró el DataFrame por el año 2020.
- Se usó `max()` sobre la columna `Log GDP per capita` para obtener el país con el valor más alto.
- Se usó `idxmax()` sobre la columna `Life Ladder` para obtener el puesto de felicidad del país con el mayor GDP per cápita.

## 5. ¿Cuál fue la variación del GDP promedio mundial entre 2020 y 2021?

**Resultado:**

- La variación del GDP promedio mundial entre 2020 y 2021 fue de **+3.38%**.

**Método:**

- Se filtró el DataFrame por el año 2020 y 2021.
- Se usó `mean()` sobre la columna `Log GDP per capita` para obtener el GDP promedio mundial.
- Se calculó la variación porcentual del GDP promedio mundial entre 2020 y 2021.

## 6. ¿Qué país tuvo la mayor expectativa de vida en 2019, 2020 y 2021?

**Respuesta:**

- **Singapur** fue el país con la mayor expectativa de vida en 2019, 2020 y 2021.

**Método:**

- Se filtró el DataFrame por el año 2019, 2020 y 2021.
- Se usó `max()` sobre la columna `Healthy life expectancy` para obtener el país con la mayor expectativa de vida.

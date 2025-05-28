# Happiness Index Analysis

Este repositorio contiene un proyecto de análisis de datos sobre el informe de felicidad mundial, combinando técnicas de preprocesamiento, análisis exploratorio y visualización utilizando Jupyter Notebooks.

**El objetivo es explorar la relación entre el índice de felicidad, el GDP per cápita, la expectativa de vida y otros indicadores a lo largo de los años**.

## Objetivos del Proyecto

- Explorar la felicidad mundial utilizando conjuntos de datos reales (2020-2021).
- Comparar el índice de felicidad por país, región y año.
- Relacionar variables socioeconómicas (GDP, expectativa de vida) con la percepción de bienestar.
- Aplicar técnicas básicas de análisis de datos usando Python (pandas, matplotlib, seaborn).

## Estructura del Repositorio

```
.
├── docs/
│   └── questions-analysis.md
├── notebooks/
│   ├── data-analysis.ipynb
│   └── data-visualization.ipynb
├── data/
│   ├── world-happiness-report-2021.csv
│   └── world-happiness-report.csv
```

## Ejercicios y Análisis

El cuaderno Jupyter analiza los siguientes puntos clave:

1. **País más feliz del mundo en 2021**  
   Se determina mediante el mayor `Ladder score`.

2. **País más feliz por continente**  
   A partir del mapeo entre regiones y continentes se identifica el país líder en cada uno.

3. **País que más veces ocupó el primer lugar entre 2005 y 2021**  
   Se evalúa con varias estrategias (`idxmax()`, `apply()`, rankings).

4. **Relación entre GDP y felicidad**  
   Se analiza la posición en el ranking de felicidad del país con mayor GDP en 2020.

5. **Variación del GDP promedio mundial entre 2020 y 2021**  
   Se calcula la variación porcentual y se analizan sus implicaciones.

6. **País con mayor expectativa de vida**  
   Se compara el indicador en los años 2019, 2020 y 2021.

> Ver detalles completos en [`docs/questions-analysis.md`](docs/questions-analysis.md)

## Uso del repositorio

1. Clona o descarga este repositorio:

```bash
git clone git@github.com:rociobenitez/happiness-index-data-processing.git
cd happiness-index-data-processing
```

2. Instala las dependencias:

```bash
pip install -r requirements.txt
```

3. Abre los notebooks utilizando [Jupyter Notebook](https://jupyter.org/) o [Jupyter Lab](https://jupyterlab.readthedocs.io/en/latest/).

4. Explora y analiza los datos ejecutando los cuadernos disponibles, especialmente `data-visualization.ipynb` para visualizaciones y `questions-analysis.ipynb` para insights.

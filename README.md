# 🎧 Spotify Data Analysis Project

## Descripción del proyecto

Este proyecto consiste en un **Análisis Exploratorio de Datos (EDA)** sobre canciones de Spotify, con el objetivo de entender cómo se distribuye la popularidad y qué factores pueden estar relacionados con el éxito de una canción.

Para ello, se han utilizado dos datasets distintos que han sido limpiados, transformados y combinados en un dataset final sobre el que se ha realizado todo el análisis.

---

## Objetivos

* Analizar la distribución de la popularidad
* Identificar patrones según el género musical
* Estudiar el impacto de características como la bailabilidad
* Detectar la concentración del éxito en el catálogo
* Construir un dashboard interactivo en Power BI

---

## Herramientas utilizadas

* **Python (Pandas, NumPy)** → limpieza y análisis
* **Visual Studio Code** → desarrollo
* **Power BI Desktop** → visualización

## Estructura del proyecto
├── data/

│   ├── raw/ 

│   ├── processed/ 

│   ├── notebooks/  

├── dashboard/  

├── README.md/ 

---

## Limpieza y transformación de datos

Durante esta fase se han realizado distintas tareas para asegurar la calidad del dataset:

* Eliminación de columnas innecesarias (`Unnamed: 0`)
* Eliminación de valores duplicados
* Tratamiento de valores nulos
* Conversión de variables a formato adecuado

### Conversión de la variable Streams

Una de las transformaciones más importantes fue la conversión de la variable `Streams`, que inicialmente se encontraba en formato texto.

```python
df['Streams'] = df['Streams'].astype(str).str.replace(',', '')
df['Streams'] = pd.to_numeric(df['Streams'], errors='coerce')
```

---

## Creación de nuevas variables

### Grupo de bailabilidad (`dance_group`)

```python
df['dance_group'] = pd.cut(
    df['danceability'],
    bins=[0, 0.3, 0.6, 1],
    labels=['Baja', 'Media', 'Alta'],
    include_lowest=True
)
```

---

### Grupo de canciones Top (`top_group`)

```python
df['top_group'] = df['popularity'].apply(
    lambda x: 'Top (>=70)' if x >= 70 else 'Resto'
)
```

---

## Análisis exploratorio de los datos

A lo largo del análisis se han planteado distintas líneas de estudio con el objetivo de entender cómo se comporta la popularidad en Spotify y qué factores pueden estar relacionados con el éxito de una canción.

---

### Distribución de la popularidad

Para el primer análisis se ha estudiado cómo se distribuye la popularidad entre todas las canciones del dataset.

Los resultados muestran que aproximadamente un **60–70%** de las canciones se sitúan en niveles bajos o medios de popularidad, mientras que menos de un **10%** alcanza valores altos.

**Conclusión:** El éxito está claramente concentrado en una minoría de canciones.

---

### Popularidad según género musical

En este análisis se ha evaluado si el género musical tiene impacto en la popularidad.

Se observan diferencias entre géneros, con algunos que presentan valores superiores a la media y otros que se mantienen por debajo.

**Conclusión:** El género influye en el rendimiento de las canciones.

---

### Análisis de las canciones más populares

Se ha analizado el conjunto de canciones con mayor popularidad para entender cómo se distribuye el éxito en el ranking.

El Top está dominado por un número reducido de artistas, con presencia repetida de algunos de ellos.

**Conclusión:** El éxito se concentra en pocos artistas.

---

### Bailabilidad y popularidad

Se ha estudiado la relación entre la bailabilidad y la popularidad agrupando las canciones en tres niveles.

Los resultados indican que las canciones con mayor bailabilidad presentan niveles de popularidad más elevados.

**Conclusión:** Las canciones más bailables tienden a ser más populares.

---

### Concentración del éxito (Top vs resto)

Se ha analizado qué proporción de canciones alcanza niveles altos de popularidad.

Menos del **15%** de las canciones pertenece a la categoría “Top”, mientras que más del **85%** forma parte del resto.

**Conclusión:** El éxito está altamente concentrado en una pequeña parte del catálogo.

---

## Dashboard en Power BI

El dashboard desarrollado incluye:

* KPIs principales:

  * Popularidad media
  * Popularidad máxima
  * Número de canciones

* Visualizaciones:

  * Distribución de la popularidad
  * Popularidad por género
  * Top canciones
  * Bailabilidad vs popularidad
  * Proporción Top vs resto

---

## Diseño del dashboard

* Paleta de colores inspirada en Spotify
* Diseño limpio y visual
* Distribución clara de la información

---

## Conclusiones

* El éxito en Spotify está altamente concentrado: la mayoría de las canciones se sitúa en niveles bajos o medios, mientras que solo una pequeña parte alcanza valores altos.

* El género musical influye en la popularidad, observándose diferencias claras entre categorías.

* La bailabilidad es un factor relevante, ya que las canciones más bailables tienden a presentar mayor popularidad.

* La mayoría de las canciones presenta un rendimiento medio o bajo, lo que confirma que alcanzar altos niveles de popularidad es poco frecuente.

En conjunto, el mercado musical en Spotify funciona de forma desigual, donde un número reducido de canciones y artistas concentra la mayor parte de la atención.

---

## Posibles mejoras

* Incorporar análisis temporal
* Desarrollar modelos predictivos
* Profundizar en análisis por artista

---

## 👤 Autor

Proyecto desarrollado por Andrea García como parte de una actividad de Data Analytics. 

---

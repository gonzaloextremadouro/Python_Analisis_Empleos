# Resumen

Bienvenidos a mi análisis del mercado laboral en el mundo de los datos. Este dataset contiene cuantiosa información al respecto, con mi enfoque puesto en investigar las skills mejores pagas y/o más buscadas en los empleos, para poder encontrar las oportunidades de trabajo más óptimas en este caso para un analista de datos, que es el trabajo de interés de este proyecto.

Las columnas contienen detallada información sobre cada rol, salario, ubicaciones y skills esenciales. El dataset tiene como fuente al repositorio de [Luke Barousse](https://huggingface.co/datasets/lukebarousse/data_jobs) en [Hugging Face](https://huggingface.co), una plataforma que uso asiduamente para obtener información en la cual poder realizar análisis de datos.

Para lograr los objetivos del proyecto, realizaré el análisis a través de unos scripts de Python. La obtención y visualización de la información de interés será usando este lenguaje y sus librerías.

# Incógnitas a resolver
1. ¿Ubicaciones de las búsquedas laborales de Analistas de Datos en Argentina?
2. ¿Qué compañías lideran las búsquedas de Analistas de Datos en Argentina?
3. ¿Cuántas de las búsquedas laborales en Argentina permiten el trabajo remoto? ¿Cuántas búsquedas laborales en Argentina mencionan el requerimiento de un título universitario?
4. ¿Cuáles son las skills más requeridas en el mundo de los datos?
5. ¿Cuál es la distribución salarial en los trabajos remotos?
6. ¿Qué skills son las más requeridas y/o mejores pagas en los trabajos remotos?


# Preparación y limpieza

En esta sección describo los pasos esenciales para preparar los datos para el análisis, para lograr precisión y utilidad de los mismos.

## Importación y limpieza de datos

El primer paso es importar cada una de las librerías necesarias (con su respectivo alias) y cargar el dataset, junto a algunos pasos de limpieza para asegurar la calidad de los datos.

```python
# Importamos librerías
import ast
import pandas as pd
import seaborn as sns
from datasets import load_dataset
import matplotlib.pyplot as plt

# Cargamos los datos
dataset = load_dataset('lukebarousse/data_jobs')
df = dataset['train'].to_pandas()

# Limpiamos los datos
df['job_posted_date'] = pd.to_datetime(df['job_posted_date']) # Usamos una función de Pandas para transformar la columna de 'str' a 'datetime'
df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x) # Usamos un módulo de Python para transformar la columna de 'str' a 'list'
```

# Análisis

Cada cuaderno Jupyter de este proyecto está dirigido a investigar aspectos específicos del mercado laboral de los datos.

Como aspirante a analista de datos, focalicé sobre dos mercados laborales que me podrían ser de interés:

1. Trabajos en Argentina
2. Trabajos de manera remota global

# Trabajos en Argentina

Creamos un DataFrame que contenga sólo los trabajos ubicados en Argentina.

```python
df_ARG = df[(df['job_country'] == 'Argentina')]
```

## 1. ¿Ubicaciones de las búsquedas laborales de Analistas de Datos?

Para encontrar las ubicaciones más comunes en búsqueda de un analista de datos, agrupamos y ordenamos el df según la ubicación. Como resultado de esta consulta obtenemos las top 10 ubicaciones con avisos de empleo, que posteriormente visualizamos utilizando las librerías Matplotlib y Seaborn.

Los pasos detallados de esta consulta se pueden observar en este cuaderno: [1_Análisis de ]

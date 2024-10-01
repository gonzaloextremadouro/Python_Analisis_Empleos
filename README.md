# Resumen

Bienvenidos a mi análisis del mercado laboral en el mundo de los datos. Este dataset contiene cuantiosa información al respecto, con mi enfoque puesto en investigar las skills mejores pagas y/o más buscadas en los empleos, para poder encontrar las oportunidades de trabajo más óptimas en este caso para un analista de datos, que es el trabajo de interés de este proyecto.

Las columnas contienen detallada información sobre cada rol, salario, ubicaciones y skills esenciales. El dataset tiene como fuente al repositorio de [Luke Barousse](https://huggingface.co/datasets/lukebarousse/data_jobs) en [Hugging Face](https://huggingface.co), una plataforma que uso asiduamente para obtener información en la cual poder realizar análisis de datos.

Para lograr los objetivos del proyecto, realizaré el análisis a través de unos scripts de Python.

# Objetivos principales
1. Entender el mercado laboral en el mundo de los datos
2. Comprender qué skills son las más importantes para un analista de datos
3. Obtener información salarial sobre trabajos en Argentina o de manera remota
4. Obtener y visualizar toda la información de interés utilizando Python y sus librerías


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

Como aspirante a analista de datos, focalicé sobre dos mercados laborales que me podrían ser de interés:

1. Trabajos físicos en Argentina
2. Trabajos de manera remota

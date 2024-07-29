# LLM-FineTuning_GDJF_2024
Fine Tuning for LLM 

## Borrador
El proyecto conciste en hacer un ajuste fino o "fine tuning" de un LLM (Large Language Model) para su posterior uso como un asistente de investigación en un tema determinado, buscando referencias exactas en forma de "Digital Object Identifiers" o "DOIs" con el fin de disminuir o incluso eliminar problemas de halucinación del modelo. Para realizar este proyecto, se dividen las tareas en 3 áreas principales:

1. Extracción y formateado de datos de entrenamiento
2. Fine-Tuning del modelo
3. Evaluación del modelo ajustado

A su vez, estas tareas pueden dividirse en sub-tareas:
1. Extracción y formateado de datos de entrenamiento.
    1. Descarga de PDFs de ArXiv a partir de palabras clave.
    2. Curado manual (opcional).
    3. Extractor de datos del PDF a XML con CERMINE.
    4. Extractor de frases y de sus respectivas refs de XML a CSV.
    5. Unido de CSVs (para tratar con un solo archivo) y limpieza de CSV (eliminación automática de entradas vacías por errores de pareo, de relación de referencias, etc). También se puede realizar un pre-formateado de los datos para prepararlos para su posterior uso (separador de lineas en el CSV, ya que en ocasiones hay frases que contienen mas de 1 referencia).
    6. Uso de API de Crossref para asociar las referencias (títulos y años de publicación) con sus respectivos DOIs.
    7. Formateado de las frases y los DOIs como pares pregunta-respuesta. Se hará uso de una herramienta externa (RelevanceAI). Tras este paso se obtiene una coleccion en formato CSV con formato adecuado para el fine-tuning (formato input-output).

2. Fine-Tuning.
    1. Se carga el modelo.
    2. Se cargan los parametros.
    3. Se carga el dataset que se usara para el fine-tuning.
    4. Se especifica el formato que usa el modelo para adaptar el dataset a este mismo.
    5. Se realiza el Fine-Tuning. Pueden realizarse varios modelos con el fin de estudiar la "utilidad" que tienen con distintos parametros y épocas de entrenamiento.

3. Evaluación del modelo
    1. Creación de un dataset de evaluación.
    2. Ejecución de los distintos modelos con un número específico de prompts.
    3. Con las referencias obtenidas en el paso anterior, búsqueda del artículo en Google Scholar.
    4. Evaluación de presencia de palabres clave en los resúmenes de los artículos científicos.

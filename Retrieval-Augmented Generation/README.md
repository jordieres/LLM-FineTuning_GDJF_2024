# Implementaciones de Retrieval-Augmented Generation (RAG)

## Introducción
En las **técnicas RAG**, se realiza una búsqueda previa en una base de datos, y se inyectan los resultados más relevantes en el prompt del modelo de lenguaje, al que se le pide que tome una decisión acerca de qué contextos (y qué referencias asociadas a dichos contextos) son los más relevantes para la pregunta del usuario.

En este caso, para la búsqueda previa a la generación del modelo de lenguaje se hace uso de un modelo de "vector embeddings". Estos modelos son capaces de proyectar en vectores de altas dimensiones el significado semántico de una oración, lo que será útil a la hora de buscar las preguntas del usuario.

Para la identificación de las preguntas encontradas en el dataset que sean más relevantes a la pregunta del usuario, se hace un cálculo de máxima similitud entre el vector extraído de la pregunta del usuario y cada uno de los vectores extraídos de las preguntas del dataset.

Finalmente, se inyectan los resultados más relevantes en el prompt del modelo, que se encargará de tomar la decisión final de si el contexto proporcionado es útil para el usuario o no.

## Metodología
La metodología del RAG coincide con la del Fine-Tuning en la extracción de datos para el uso del modelo, por lo que se obviará esta parte. En cuanto a los siguientes pasos, se proporciona el código de 3 implementaciones distintas de RAG:

### 1. Implementación 1:
1. Búsqueda por similitud semántica de la pregunta del usuario en el dataset de preguntas y referencias.
2. Inyectado de las 3 preguntas del dataset más similares y sus respectivas referencias en el LLM.

### 2. Implementación 2:
1. Generación con LLM de 2 preguntas extra similares a la del usuario.
2. Búsqueda por similitud semántica de las 3 preguntas en el dataset de preguntas y referencias.
3. Inyectado de las 3 preguntas del dataset más similares y sus respectivas referencias en el LLM.

### 3. Implementación 3:
1. Extracción con LLM de los temas principales de la pregunta del usuario.
2. Búsqueda por similitud semántica de los temas de la pregunta del usuario en el dataset de oraciones originales extraídas de artículos.
3. Inyectado de las 3 oraciones más similares y sus respectivas referencias en el LLM.

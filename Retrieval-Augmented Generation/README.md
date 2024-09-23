# Implementaciones de Retrieval-Augmented Generation

Se proporciona el código de 3 implementaciones distintas de RAG:

## 1. Implementación 1:
1.1. Búsqueda por similitud semántica de la pregunta del usuario en el dataset de preguntas y referencias.
1.2. Inyectado de las 3 preguntas del dataset más similares y sus respectivas referencias en el LLM.

## 2. Implementación 2:
2.1. Generación con LLM de 2 preguntas extra similares a la del usuario.
2.2. Búsqueda por similitud semántica de las 3 preguntas en el dataset de preguntas y referencias.
2.3. Inyectado de las 3 preguntas del dataset más similares y sus respectivas referencias en el LLM.

## 3. Implementación 3:
3.1. Extracción con LLM de los temas principales de la pregunta del usuario.
3.2. Búsqueda por similitud semántica de los temas de la pregunta del usuario en el dataset de oraciones originales extraídas de artículos.
3.3. Inyectado de las 3 oraciones más similares y sus respectivas referencias en el LLM.

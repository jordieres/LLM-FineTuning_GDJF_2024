# Desarrollo de un Asistente de Investigación: Análisis Comparativo de Técnicas de Fine-Tuning y Retrieval-Augmented Generation (RAG)

## Introducción
Con motivo de facilitar la creación y el uso de modelos como asistentes de investigación, se proporciona todo el código comentado en el trabajo **Desarrollo de un Asistente de Investigación: Análisis Comparativo de Técnicas de Fine-Tuning y Retrieval-Augmented Generation (RAG)**, desarrollado como TFG para la obtención del título de grado en Ingeniería en Tecnologías Industriales en la Universidad Politécnica de Madrid, con las instrucciones necesarias para replicar el trabajo realizado.

Consiste en comparar las técnicas de **Fine-Tuning** de un modelo de lenguaje y varias implementaciones de técnicas de **Retrieval-Augmented Generation**, con el fín de evaluar la viabilidad de uso de ambas alternativas en un asistente de investigación en un tema determinado. Este deberá buscar referencias exactas en forma de "Digital Object Identifiers" o "DOIs" con el fin de disminuir o incluso eliminar problemas de halucinación del modelo.

Se recomienda el uso de la técnica RAG para el desarrollo de un asistente de investigación, debido a que los resultados obtenidos con el Fine-Tuning del modelo Llama3.1 8B Instruct cuantizado a 4-bits no proporcionaba resultados relevantes al usuario de forma consistente.
# Extractor de Referencias de XMLs
El script busca y segmenta todas las oraciones (separadas por puntos, cierre de signos de interrogación o exclamación, etc.) y las asocia a sus respectivas referencias, presentes en el cuerpo de texto del archivo XML con sus etiquetas NLM JATS respectivas.

Debido al método de extracción de DOIs que se usará posteriormente, sólo se extrae el título del artículo y el año en el que fue publicado.

Finalmente, escribe las oraciones, títulos y años "línea a línea" en un archivo CSV (una línea por cada oración, independientemente de cuantas referencias tenga. En caso de tener más de una referencia, las separa con el caracter de nueva línea "\n").
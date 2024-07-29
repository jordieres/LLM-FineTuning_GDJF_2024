# Unido y limpieza.
Se hace uso de 2 scripts con el fin de preparar las frases y las referencias para el siguiente paso.

1. CSV Merger
Se encarga de unir los distintos CSVs exportados en el paso anterior (localizados en la carpeta "CSVs") en uno solo.

2. CSV Cleaner
Se encarga de "limpiar" las filas del CSV unido, esto es, si falta alguna celda (ya sea porque el extractor de referencias no encontró título o año para una frase específica, o porque no había referencia que respaldase la frase en primer lugar), se borra la línea entera (debido a que no es útil para el entrenamiento del modelo).
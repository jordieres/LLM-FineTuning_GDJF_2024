# Búsqueda de DOIs con API de Crossref
Este script se encarga de ir fila a fila del CSV obtenido en el paso anterior (el CSV unido y "limpio"), buscando para cada fila las distintas entradas de título y año del artículo científico (separadas en una misma celda por el caracter de nueva línea "\n").
Posteriormente, se usa la API de Crossref para obtener el "Digital Object Identifier" o "DOI" del artículo, que es añadido en una nueva columna en el CSV.

>[!NOTE]
> En este caso se ha optado por usar la versión **"Polite"** de la API, que requiere autentificación opcional con un correo electrónico. En el script se ha dejado como parámetro a ser cambiado por el usuario para evitar el filtrado de datos personales.
> Se remite a la documentación proporcionada en las referencias para más información acerca del uso de la API.

## Referencias
https://api.crossref.org/swagger-ui/index.html
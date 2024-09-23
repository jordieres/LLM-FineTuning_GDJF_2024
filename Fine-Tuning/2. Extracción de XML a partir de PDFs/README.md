# 2. Extracción de XML a partir de PDFs
Para el tratamiento uniforme de los distintos formatos de PDF, se usará CERMINE. Este paquete ejecutable de Java permite extraer en formato único en XML la metadata e información de los distintos PDFs independientemente del formato bibliográfico que use, evitando así tener que particularizar y escribir código para cada uno de los distintos tipos de formatos.

### Formato
El paquete procesa los PDF y proporciona diversas opciones de "outputs". Para nuestro uso, la más adecuada es la que proporciona archivos de extensión .cermxml con formato XML usando los "tags" o etiquetas establecidos en el estandar NLM JATS por la NISO (National Information Standards Organization).

### Código Fuente
Puede encontrarse en el repositorio del proyecto en GitHub, en el enlace https://github.com/CeON/CERMINE?tab=readme-ov-file

### Instrucciones de Ejecución
Para la ejecución del paquete, se ejecuta el comando
>java -cp cermine-impl-1.14-jar-with-dependencies.jar pl.edu.icm.cermine.ContentExtractor -path PDFs\ Recopilados -outputs jats

El flag "-path" especifica el directorio que contiene los PDF a procesar ("PDFs Recopilados"), mientras que "-outputs" especifica el tipo de output que se busca ("jats").

### Referencias
Dominika Tkaczyk, Pawel Szostek, Mateusz Fedoryszak, Piotr Jan Dendek and Lukasz Bolikowski. 
CERMINE: automatic extraction of structured metadata from scientific literature. 
In International Journal on Document Analysis and Recognition (IJDAR), 2015, 
vol. 18, no. 4, pp. 317-335, doi: 10.1007/s10032-015-0249-8.

https://jats.nlm.nih.gov
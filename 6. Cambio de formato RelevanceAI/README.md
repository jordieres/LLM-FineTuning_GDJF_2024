# Modificación de estructura gramatical de las oraciones referenciadas
Para el fine-tuning de modelos LLM es habitual el método de Supervised fine-tuning (o SFT), en la que se proporcionan pares input-output como ejemplo los esperados del modelo, para así ajustar a lo largo de un número de "pasadas" los pesos del modelo y conseguir tras el entreno una respuesta mas cercana a lo esperado.

El principal inconveniente que encontramos con los datos que disponemos es que las oraciones están escritas en forma de afirmaciones acerca de un tema específico (debido a la naturaleza de la fuente de los datos, textos científicos), mientras que al usar LLMs suele usarse como "prompt" oraciones en forma de preguntas o peticiones.

Para solucionar esto y obtener información con el formato que buscamos, haremos uso de modelos de lenguaje al estilo de ChatGPT de OpenAI o Llama3 de Meta, mediante herramientas externas como RelevanceAI.

## Motivación del uso
Como ya se ha explicado, se necesitan los datos expresados en una forma natural que simule una conversación con la estructura de pregunta-respuesta. Ya que contamos con las afirmaciones adquiridas de la extracción y procesado de los artículos científicos, bastaría con convertir la afirmación extraída en una oración equivalente en forma de pregunta o solicitud (los formatos de entrada más habituales en el uso de los modelos de lenguaje).

Debido a la dificultad y a la naturaleza manual (no automatizable por medios habituales) de la labor de conversión, se ha optado por usar ChatGPT para la asistencia de esta tarea, mediante el uso de "prompt engineering", técnicas mediante las cuales se diseña un prompt con una serie de instrucciones para ser "interpretado" por modelos de lenguaje.

**Ejemplos en inglés:**
Afirmación: However, in the same year, the number of firms seeking to capitalize on big data utilization decreased by about 6.1 percent (Van der Meulen, 2016) .
Solicitud: Find me research relating big data utilization and the decrease of firms looking to capitalize on it.

Afirmación: With the increasingly digital economy, the open and collaborative models become economically more viable `[2]`.
Solicitud: Where can I learn about the economic viability of open and collaborative models?

Afirmación: Borrowing from industrial organization economics, the theories adhered to suggest that, unless otherwise impeded, competitive forces should drive abnormally high profits toward more normal levels (Jacobson, 1988; Mueller, 1986; Rumelt, 1987, 1991).
Solicitud: Can you recommend any textbooks about competition driving price drops?

## RelevanceAI
Mediante el uso de la herramienta RelevanceAI y técnicas de prompt engineering, podemos automatizar la ejecución de prompts con parametros variables en modelos como ChatGPT 4o con el fin de convertir una afirmación en solicitud. Esto permite ejecutar la conversión de todas las oraciones o afirmaciones que se obtienen de la extracción de PDFs para obtener solicitudes aptas para el fine-tuning de un LLM, esto es, solicitudes "naturales" que podría escribir una persona al usar un modelo de lenguaje para buscar referencias acerca de distintos temas.

Para esto, se usará el archivo CSV con las oraciones y DOIs recopilados, y cada celda que contenga una afirmación se pasará como parámetro al prompt, que será ejecutado por el modelo y "responderá" con la afirmación convertida en solicitud.

## Prompt propuesto
Se propone el siguiente prompt de ejemplo, que incluye las instrucciones de la tarea, da ejemplos de solicitudes o preguntas que se consideran válidas (preguntas al estilo de lo que sería "normal" preguntar al modelo al investigar acerca de un tema específico), y finalmente da 3 ejemplos de afirmaciones y sus respectivas conversiones a solicitudes.
Tras el último ejemplo, se incluye el parámetro que será reemplazado por cada afirmación del archivo CSV (en el ejemplo, marcado en negrita), seguido del inicio de la respuesta del modelo ("bot:").
Al ejecutarse, el modelo completará el prompt con el texto faltante (la solicitud), que será guardado en una columna nueva creada para almacenar las respuestas de cada una de las filas.

>For the following text extract, engineer a prompt asking for the reference/research for the text extract given. Write ONLY ONE SENTENCE. If you find abbreviations of words or phrases that can’t be deduced from the context don’t make them up, use them as is. Keep the main subject of the topic (paraphrasing is allowed). Remove any text mentioning or pointing to a source found in the original sentence. Openings can include (but shouldn't be limited to, be creative!): ‘Where can I find more information about…’, ‘Could you recommend some articles on…’, ‘I'm looking for scholarly papers about…’, ‘Do you know of any sources that compare…’, ‘I need references for a paper comparing…’, ‘What are the latest studies on…’, ‘What are some authoritative books on…’, ‘I'm interested in X. What sources should I look at?’, ‘Where can I find technical details about…’, ‘I need data on…’, ‘I'm looking for expert opinions on…’, ‘Where can I find information about…’, ‘Can you recommend any textbooks for…’, or anything else you come up with, finding the best alternative for each sentence. For example:
prompt: However, in the same year, the number of firms seeking to capitalize on big data utilization decreased by about 6.1 percent (Van der Meulen, 2016) .
bot: Find me research relating big data utilization and the decrease of firms looking to capitalize on it.
prompt: With the increasingly digital economy, the open and collaborative models become economically more viable `[ 2 ]`.
bot: Where can I learn about the economic viability of open and collaborative models?
prompt: Borrowing from industrial organization economics, the theories adhered to suggest that, unless otherwise impeded, competitive forces should drive abnormally high profits toward more normal levels (Jacobson, 1988; Mueller, 1986; Rumelt, 1987, 1991).
bot: Can you recommend any textbooks about competition driving price drops?
prompt:
**{{
text
}}**
bot:

## Referencias
1. https://relevanceai.com
2. https://github.blog/ai-and-ml/generative-ai/prompt-engineering-guide-generative-ai-llms/
3. https://en.wikipedia.org/wiki/Prompt_engineering

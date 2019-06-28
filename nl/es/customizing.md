---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Personalización del modelo
{: #customizing}

La mayoría de los modelos de traducción que se proporcionan en {{site.data.keyword.languagetranslatorshort}} se pueden ampliar para que aprendan términos y frases personalizados o un estilo general derivado de los datos de la traducción. Siga estas instrucciones para crear su propio modelo de traducción personalizado.
{: shortdesc}

## Antes de empezar
{: #before-you-begin}

1. Asegúrese de que la instancia de servicio de {{site.data.keyword.languagetranslatorshort}} está en un plan de precios Avanzado o Premium. Los planes Lite y Estándar no dan soporte a la personalización.
1. Busque un modelo base personalizable para su par de idiomas. Necesitará el ID del modelo base para poder entrenar el modelo personalizado.
    - Busque en los modelos mostrados en la página [Modelos de traducción](/docs/services/language-translator?topic=language-translator-translation-models). Localice el valor "**true**" en la columna **Customizable** y asegúrese de que los idiomas de origen (**Source**) y de destino (**Target**) del modelo coinciden con su par de idiomas.
    - Como alternativa, puede utilizar el método de API [Listar modelos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/apidocs/language-translator#list-models) para buscar modelos mediante programación. Puede filtrar los resultados por idioma con los parámetros `source` y `target`.

## Paso 1: Crear sus datos de entrenamiento
{: #create-your-training-data}

El servicio requiere que se suministren datos de entrenamiento en el [formato de archivo Translation Memory Exchange (TMX)](#creating-tmx-files). Puede almacenar hasta 10 personalizaciones para cada par de idiomas en una instancia de servicio. El servicio da soporte a dos tipos de solicitudes de personalización. Puede personalizar un modelo con un glosario forzado o con un corpus que contenga sentencias paralelas.

- Utilice un [glosario forzado](#forced-glossary-customization) para obligar a que determinados términos y frases se traduzcan de una forma específica.
- Utilice un [corpus paralelo](#parallel-corpus-customization) cuando desee que el modelo personalizado aprenda de los patrones de traducción generales de sus ejemplos. Lo que aprende el modelo de un corpus paralelo puede mejorar los resultados de la traducción para texto de entrada sobre el que no se ha entrenado el modelo.

Después de haber creado los [archivos Translation Memory Exchange (TMX)](#creating-tmx-files), estará listo para entrenar el modelo.

## Paso 2: Entrenar el modelo
{: #train-your-model}

Utilice el método [Crear modelo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/apidocs/language-translator#create-model) para entrenar el modelo. En la solicitud, especifique el ID de un modelo base personalizable y los datos de entrenamiento en los parámetros `forced_glossary` o `parallel_corpus`.

### Solicitud de ejemplo
{: #train-model-example-request}

En la solicitud de ejemplo siguiente se utiliza un archivo de glosario forzado, _glossary.tmx_, para personalizar el modelo base `en-es`. Consulte la sección [Personalización de glosario forzado](#forced-glossary) para ver un archivo TMX de glosario forzado de ejemplo.

```bash
curl --user apikey:{apikey} -X POST --form forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

La respuesta de la API contendrá detalles sobre el modelo personalizado, incluido su ID de modelo. Utilice el ID del modelo para comprobar el estado del modelo y para traducir frases una vez que el estado del modelo pase a ser "available".

```json
{
  "model_id": "96221b69-8e46-42e4-a3c1-808e17c787ca",
  "source": "en",
  "target": "es",
  "base_model_id": "en-es",
  "domain": "general",
  "customizable": false,
  "default_model": false,
  "owner": "4937aab7-0f3a-4a75-bee1-0b7a12b6b8",
  "status": "uploaded",
  "name": "custom-english-to-spanish",
  "train_log": null
}
```
{: codeblock}

## Paso 3: Comprobar el estado del modelo
{: #check-model-status}

El entrenamiento de un modelo puede llevar desde un par de minutos (para glosarios forzados) hasta varias horas (para grandes corpus paralelos), en función de la cantidad de datos de entrenamiento que intervengan. Para ver si el modelo está disponible, utilice el método [Obtener modelo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/apidocs/language-translator#get-model-details) y especifique el ID del modelo que ha recibido en la respuesta del servicio en el Paso 2. También puede comprobar el estado de todos sus modelos con el método [Listar modelos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/apidocs/language-translator#list-models).

El atributo de respuesta `status` describe el estado del modelo en el proceso de entrenamiento:

- `uploading` (cargando)
- `uploaded` (cargado)
- `dispatching` (asignando)
- `queued` (en cola)
- `training` (entrenando)
- `trained` (entrenado)
- `publishing` (publicando)
- `available` (disponible)

Cuando el estado del modelo es `available` (disponible), el modelo está listo para utilizar con su instancia de servicio. Si el modelo se suprime, o si se encuentra un error en el proceso de entrenamiento, puede ver uno de los estados siguientes:

- `deleted` (suprimido)
- `error`

### Solicitud de ejemplo
{: #check-model-example-request}

En el ejemplo siguiente se obtiene información para el modelo identificado por el ID de modelo `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```bash
curl --user apikey:{apikey_value} "https://gateway.watsonplatform.net/language-translator/api/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## Paso 4: Traducir el texto con el modelo personalizado
{: #translate-text}

Para utilizar el modelo personalizado, especifique el texto que desea traducir y el ID del modelo personalizado en el método [Traducir ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/apidocs/language-translator#translate).

### Solicitud de ejemplo
{: #translate-text-example-request}

El siguiente ejemplo traduce el texto con el modelo personalizado identificado por el ID de modelo `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data '{"text":"Hello","model_id":"96221b69-8e46-42e4-a3c1-808e17c787ca"}' https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}


## Personalización de glosario forzado
{: #forced-glossary-customization}

Utilice un **glosario forzado** para establecer traducciones obligatorias para determinados términos y frases. Si desea mantener un control específico sobre el comportamiento de una traducción, utilice un glosario forzado.

- Formato de los datos de entrenamiento: [TMX](#creating-tmx-files) (codificado en UTF-8)
- Tamaño máximo de archivo: 10 MB
- Puede aplicar un glosario forzado a un modelo base o a un modelo que se ha personalizado con un corpus paralelo
- Límite de un glosario forzado por modelo

Los ejemplos de glosario forzado distinguen entre mayúsculas y minúsculas, así que asegúrese de que los datos de entrenamiento reflejen las mayúsculas del contenido que encontrará la aplicación.
{: tip}

### Ejemplo de glosario forzado
{: #forced-glossary-example}

En el ejemplo siguiente se muestra un archivo TMX con dos pares de traducciones. El primer par obliga que "international business machines" se mantenga en inglés durante la traducción. Este tipo de traducción forzada puede resultar útil si desea mantener nombres de empresas en los que no se han puesto mayúsculas correctamente en comunicaciones informales. El segundo par obliga al modelo a utilizar siempre "brevet" cuando tiene que traducir "patent".

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="phrase" o-tmf="" adminlang="en"
    srclang="en" datatype="PlainText" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>International Business Machines</seg>
      </tuv>
    </tu>
    <tu>
      <tuv xml:lang="en">
        <seg>patent</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>brevet</seg>
      </tuv>
    </tu>
  </body>
</tmx>
```
{: codeblock}



## Personalización de corpus paralelo
{: #parallel-corpus-customization}

Utilice un **corpus paralelo** para proporcionar traducciones adicionales de las que aprende el modelo base. Esto ayuda a adaptar el modelo base a un dominio específico. La forma en que el modelo personalizado resultante traduce el texto depende de la comprensión combinada del modelo del corpus paralelo y del modelo base.

- Formato de los datos de entrenamiento: [TMX](#creating-tmx-files) (codificado en UTF-8)
- Longitud máxima de pares de traducción: 80 palabras de origen
- Número mínimo de pares de traducción: 5.000
- Tamaño máximo de archivo: 250 MB
- Puede enviar varios archivos de corpus paralelo repitiendo el parámetro de formato de varias partes `parallel_corpus`, siempre que el tamaño acumulado de los archivos no supere los 250 MB.

### Ejemplo de corpus paralelo
{: #parallel-corpus-example}

A continuación encontrará una pequeña parte de un corpus paralelo de inglés a francés descargado de la [recopilación MultiUN ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://opus.nlpl.eu/MultiUN.php), disponible en el sitio web abierto de corpus paralelo de OPUS. Puede descargar una versión comprimida del archivo TMX completo [aquí ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz).


```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
<header creationdate="Tue Jan 29 12:49:40 2013"
          srclang="en"
          adminlang="en"
          o-tmf="unknown"
          segtype="sentence"
          creationtool="Uplug"
          creationtoolversion="unknown"
          datatype="PlainText" />
  <body>
    <tu>
      <tuv xml:lang="en"><seg>RESOLUTION 55/100</seg></tuv>
      <tuv xml:lang="fr"><seg>RÉSOLUTION 55/100</seg></tuv>
    </tu>
    <tu>
      <tuv xml:lang="en"><seg>Adopted at the 81st plenary meeting, on 4 December 2000, on the recommendation of the Committee (A/55/602/Add.2 and Corr.1, para. 94),The draft resolution recommended in the report was sponsored in the Committee by: Bolivia, Cuba, El Salvador, Ghana and Honduras. by a recorded vote of 106 to 1, with 67 abstentions, as follows:</seg></tuv>
      <tuv xml:lang="fr"><seg>Adoptée à la 81e séance plénière, le 4 décembre 2000, sur la recommandation de la Commission (A/55/602/Add.2, par. 94)Le projet de résolution recommandé dans le rapport de la Commission avait pour auteurs les pays suivants: Bolivie, Cuba, El Salvador, Ghana et Honduras., par 106 voix contre une, avec 67 abstentions, à la suite d'un vote enregistré, les voix s'étant réparties comme suit:</seg></tuv>
    </tu>
    ...
```
{: codeblock}

Las mejoras generales de la personalización del corpus paralelo son menos predecibles que los resultados obligatorios que obtiene de la personalización del glosario forzado. Por ejemplo, supongamos que tiene la siguiente unidad de traducción del corpus paralelo de ejemplo (líneas 172-175).

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

Si traduce "55/102. Globalization and its impact on the full enjoyment of all human rights" con el modelo `en-fr` base, el servicio responde con la siguiente traducción.

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

Cuando un modelo personalizado entrenado con el corpus de ejemplo traduce la misma frase de entrada, el servicio responde con una traducción distinta, que no es idéntica a la traducción de ejemplo proporcionada en los datos de entrenamiento.

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- El modelo personalizado traduce "the full enjoyment" como "le plein exercice" en lugar de como "la pleine jouissance". La explicación probable de esta desviación del comportamiento del modelo base es que hay muchos ejemplos en el corpus donde "enjoyment" se ha traducido como "exercice".
- El modelo personalizado traduce "of all human rights" como "de tous les droits de l'homme" en lugar de reproducir el resultado de la unidad de traducción, "des droits de l'homme". Este comportamiento refleja la comprensión cohesiva del modelo entrenado del modelo base y de todos los ejemplos de traducción relacionados con "of all human rights" del corpus paralelo.

En algunos casos, podría parecer que un modelo personalizado entrenado con un corpus paralelo está ignorando un ejemplo específico que ha proporcionado. En estos casos, intente buscar en sus datos de entrenamiento otras frases que puedan estar influyendo en el comportamiento de la traducción, o bien considere la posibilidad de utilizar un glosario forzado si desea controlar una traducción específica.


## Creación de archivos TMX
{: #creating-tmx-files}

Para proporcionar un corpus o glosario de términos para entrenar el servicio {{site.data.keyword.languagetranslatorshort}}, cree un documento codificado en UTF-8 válido que sea conforme con la especificación TMX (Translation Memory Exchange) [versión 1.4 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ttt.org/oscarStandards/tmx/){: new_window}. TMX es una especificación XML que diseñada para las herramientas de traducción automática. El ejemplo siguiente es un archivo de glosario con formato TMX con dos unidades de traducción (elementos `<tu>`):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>International Business Machines</seg>
      </tuv>
    </tu>
    <tu>
      <tuv xml:lang="en">
        <seg>patent</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>brevet</seg>
      </tuv>
    </tu>
  </body>
</tmx>
```
{: codeblock}

Cada par de término y traducción se debe especificar entre códigos `<tu>`:

```xml
<tu>
  <tuv xml:lang="en">
    <seg>international business machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

El atributo `xml:lang` de la etiqueta `<tuv>` identifica el idioma en el que está expresado un término, mientras que la etiqueta `<seg>` contiene el término o la traducción.

El servicio {{site.data.keyword.languagetranslatorshort}} solo utiliza los elementos `<tu>`, `<tuv>` y `<seg>`. Todos los demás elementos del ejemplo son necesarios para que el archivo TMX sea válido, o son informativos, pero el servicio no los utiliza.



### Utilización del ejemplo como plantilla
{: #using-the-example-template}

Para utilizar el ejemplo proporcionado como una plantilla para su propio glosario o corpus, siga estos pasos:

1. Copie y pegue el ejemplo en un editor de texto.

2. Cambie el atributo `srclang` de la etiqueta `<header>` por el [código de idioma ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} del idioma de origen que utiliza su glosario o corpus paralelo.

3. Cambie el atributo `xml:lang` de las etiquetas `<tuv>` por el [código de idioma ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} correcto para cada término o traducción.

4. Guarde el documento con la extensión `.tmx` y codificación UTF-8.

### Cambio de un archivo TMX a la codificación UTF-8
{: #changing-tmx-file-to-utf-8}

Puede utilizar varias herramientas para crear o generar archivos TMX. A menudo, los archivos TMX generados están codificados en UTF-16 de forma predeterminada. El servicio {{site.data.keyword.languagetranslatorshort}} acepta sólo archivos TMX codificados en UTF-8. Para cambiar la codificación de un archivo TMX, siga los siguientes pasos:

1. Abra el archivo TMX en un editor de texto.

1. Cambie la cabecera XML (si existe) de `<?xml ... encoding="utf-16"?>` a `<?xml ... encoding="utf-8"?>`.

1. Guarde el archivo con un nuevo nombre y con codificación UTF-8.

Los usuarios de Mac también pueden cambiar la codificación de archivo actualizando la cabecera XML del documento tal como se describe en el paso 2 y, a continuación, ejecutando el siguiente mandato en el Terminal:

```bash
iconv -f utf-16 -t utf-8 <nombre_archivo_utf-16.tmx> <nuevo_nombre_archivo_utf-8.tmx>
```
{: pre}


## Supresión de un modelo de traducción personalizado
{: #deleting-a-custom-model}

Para suprimir un modelo de traducción personalizado, utilice el método [Suprimir un modelo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/apidocs/language-translator#delete-model).

El mandato siguiente suprime el modelo de traducción con ID `3e7dfdbe-f757-4150-afee-458e71eb93fb`.

```curl
curl --user apikey:{apikey_value} --request DELETE "https://gateway.watsonplatform.net/language-translator/api/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: codeblock}

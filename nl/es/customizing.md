---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

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

¿Está creando un traductor para que lo utilice el soporte al cliente, y tiene términos específicos de la empresa que desea tratar de un cierto modo en las conversaciones? ¿Está creando una forma para que los ingenieros de un país busquen datos de patentes en otro idioma, y generalmente registra patentes sobre una tecnología específica? Utilice sus propios datos para crear un diccionario personalizado y un modelo de traducción personalizado en la API de {{site.data.keyword.languagetranslatorshort}}.
{: shortdesc}

Puede personalizar el modelo de {{site.data.keyword.languagetranslatorshort}} de las siguientes maneras:

- Enseñe al servicio mediante pares de términos o frases coincidentes en un idioma de origen y de destino. Proporcione un *glosario forzado*, que contiene pares de términos o frases que son absolutos, términos definitivos que desea que el servicio de traducción trate como obligatorios. O bien, proporcione un *corpus paralelo*, que contiene pares de términos o frases que sirven como sugerencias de traducción alternativa que desea que considere el servicio de traducción.
- Cargue un gran cuerpo de texto en un idioma de destino (se conoce como *corpus monolingüe*) para que sirva como ejemplo de idioma que el servicio pueda evaluar y utilizar para mejorar la calidad general de la traducción.

Para ver la lista de los modelos que puede personalizar, utilice el método `GET /v2/models` y busque el parámetro de respuesta `customizable=true` en la respuesta de cada modelo de idioma.

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

Cada modelo personalizable puede almacenar hasta 10 personalizaciones por instancia de servicio.

## Estructura de los datos de entrenamiento
{: #structure}

Para proporcionar un corpus o glosario de términos para entrenar el servicio {{site.data.keyword.languagetranslatorshort}}, cree un documento codificado en UTF-8 válido que sea conforme con la especificación TMX (Translation Memory Exchange) [versión 1.4 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ttt.org/oscarstandards/tmx/tmx14.dtd){: new_window}. TMX es una especificación XML que diseñada para las herramientas de traducción automática. El ejemplo siguiente es un archivo de glosario en formato TMX con dos pares de términos y traducción:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>International Business Machines</seg>
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

Cada par de término y traducción debe estar dentro de las etiquetas `<tu>`:

```xml
<tu>
  <tuv xml:lang="en">
    <seg>International Business Machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

El atributo `xml:lang` de la etiqueta `<tuv>` identifica el idioma en el que está expresado un término, mientras que la etiqueta `<seg>` contiene el término o la traducción.

El servicio {{site.data.keyword.languagetranslatorshort}} solo utiliza los elementos `<tu>`, `<tuv>` y `<seg>`. Todos los demás elementos del ejemplo son necesarios para que el archivo TMX sea válido, o son informativos, pero el servicio no los utiliza.

El ejemplo anterior muestra cómo estandarizar definitivamente la traducción de un término técnico, como 'patente', y cómo personalizar la traducción de un nombre de empresa como 'International Business Machines'. En el modelo estándar, 'International Business Machines' podría traducirse como 'Machines Commerciales Internationales', pero en realidad no debería traducirse porque es el nombre de una empresa.

## Utilización del ejemplo como plantilla

Para utilizar el ejemplo proporcionado como una plantilla para su propio glosario o corpus, siga estos pasos:

1.  Copie y pegue el ejemplo en un editor de texto.

1.  Cambie el atributo `srclang` de la etiqueta `<header>` por el [código de idioma ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} del idioma de origen que utiliza su glosario o corpus paralelo.

1.  Cambie el atributo `xml:lang` de las etiquetas `<tuv>` por el [código de idioma ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} correcto para cada término o traducción.

    El servicio {{site.data.keyword.languagetranslatorshort}} utiliza códigos de idioma ISO 639-1 para todos los idiomas excepto el árabe, que utiliza el código ISO 639-3.

1.  Guarde el documento con la extensión `.tmx` y codificación UTF-8.

### Cambio de un archivo TMX a la codificación UTF-8

Puede utilizar varias herramientas para crear o generar archivos TMX. A menudo, los archivos TMX generados están codificados en UTF-16 de forma predeterminada. El servicio {{site.data.keyword.languagetranslatorshort}} acepta sólo archivos TMX codificados en UTF-8. Para cambiar la codificación de un archivo TMX, siga los siguientes pasos:

1.  Abra el archivo TMX en un editor de texto.

1.  Cambie la cabecera XML (si existe) de `<?xml ... encoding="utf-16"?>` a `<?xml ... encoding="utf-8"?>`.

1.  Guarde el archivo con un nuevo nombre y con codificación UTF-8.

Los usuarios de Mac también pueden cambiar la codificación de archivo actualizando la cabecera XML del documento tal como se describe en el paso 2 y, a continuación, ejecutando el siguiente mandato en el Terminal:

```bash
iconv -f utf-16 -t utf-8 <nombre_archivo_utf-16.tmx> <nuevo_nombre_archivo_utf-8.tmx>
```
{: pre}

## Entrenamiento de un modelo de traducción personalizado
{: #training}

Utilice el método `POST /v2/models` para cargar su archivo TMX y entrenar el modelo de traducción. Especifique como mínimo una de las siguientes opciones de archivo para entrenar su modelo personalizado:

- `forced_glossary`: Un archivo TMX codificado en UTF-8 que contiene pares de términos coincidentes en el idioma de origen y de destino que el sistema debe considerar como absolutos. Este archivo sobrescribe completamente los datos originales del dominio.

    Los glosarios forzados están limitados a un tamaño de archivo de 10 MB. Actualmente solo puede cargar un archivo de glosario forzado por modelo de traducción.
    
- `parallel_corpus`: Un archivo TMX codificado en UTF-8 que contiene frases coincidentes en el idioma de origen y de destino que sirven como ejemplos para Watson. Los corpus paralelos difieren de los glosarios forzados porque no sobrescriben los datos originales del dominio.

    Para entrenar satisfactoriamente un modelo personalizado, un documento de corpus paralelo debe contener un mínimo de 5.000 pares de términos y de traducción.
    
- `monolingual_corpus`: Un archivo de texto sin formato codificado en UTF-8 que contiene un cuerpo de texto en el idioma de destino que está relacionado con lo que se traduce. Proporcionar un corpus monolingüe mejora las traducciones literales proporcionando una traducción más fluida y natural.

    Para entrenar satisfactoriamente un modelo personalizado, un documento de corpus monolingüe debe contener un mínimo de 1.000 frases.

El tamaño total de todos los archivos de glosario y de corpus cargados está limitado a 250 MB. Dependiendo del tamaño de los archivos cargados, el entrenamiento puede durar desde minutos para un glosario hasta varias horas para un gran corpus.

El ejemplo de curl siguiente utiliza la opción de archivo `forced_glossary`.
1. Descargue el archivo TMX de ejemplo de la sección [Estructura de los datos de entrenamiento](#structure).
1. Utilice el dominio de noticias en francés (en-fr) como modelo base. Todo lo que se especifica en el archivo TMX sobrescribe completamente los datos originales del dominio.

    Para buscar todos los modelo de dominio a los que el servicio {{site.data.keyword.languagetranslatorshort}} da soporte, utilice el método `GET v2/models`:

```curl
curl -u "{username}":"{password}" -X POST -F base_model_id=en-fr -F name="test_glossary" -F forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

El método `POST /v2/models` responde con un código `200` y un nuevo `model_id`. Utilice el `model_id` cuando traduzca texto con este nuevo modelo personalizado.

## Supervisión del entrenamiento

El tamaño del archivo TMX de entrenamiento afecta al tiempo de entrenamiento de una solicitud `POST /v2/models`. Para supervisar el progreso del entrenamiento y si finaliza correctamente, utilice el método `GET /v2/models/<model_id>` y observe el valor del parámetro `status` en la respuesta.

Este mandato de ejemplo proporciona información sobre el modelo y comprueba el estado del entrenamiento que se inició en la sesión [Entrenamiento del modelo de traducción](#training). Este mandato utiliza una solicitud de cuerpo vacío.

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}

El parámetro de respuesta `STATUS` describe el estado del modelo en el proceso de entrenamiento:

- `uploading` (cargando)
- `uploaded` (cargado)
- `dispatching` (asignando)
- `queued@<#>` (en cola)
- `training` (entrenando)
- `trained` (entrenado)
- `publishing` (publicando)
- `available` (disponible)

Cuando el estado del modelo es `available` (disponible), el modelo está listo para utilizar con su instancia de servicio. Si el modelo se suprime, o si se encuentra un error en el proceso de entrenamiento, puede ver uno de los errores siguientes:

- `deleted` (suprimido)
- `error`

## Utilización de un modelo de traducción personalizado

Después de entrenar un modelo de traducción personalizado, especifique el model\_id de ese modelo de traducción para utilizarlo con los métodos `POST /v2/translate` o `GET /v2/translate`.

El ejemplo siguiente invoca el modelo del inglés al francés que se personalizó en la sección [Entrenamiento de un modelo de traducción personalizado](#training).

```curl
curl -u "{username}":"{password}" --header "Content-Type: application/json" -X POST --data "{\"model_id\": \"3e7dfdbe-f757-4150-afee-458e71eb93fb\",\"text\": \"Hello, my name is Watson, and I work for International Business Machines. How can I help you today?\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate 
```
{: codeblock}

El servicio {{site.data.keyword.languagetranslatorshort}} evalúa la calidad de la traducción utilizando los estándares BLEU (BiLingual Evaluation Understudy), así como los estándares desarrollados por IBM. Los resultados pueden variar dependiendo del par de idiomas, de la lengua vernácula utilizada o del dominio de sus datos.

## Supresión de un modelo de traducción personalizado

Cuando un modelo de traducción es obsoleto, es posible que desee suprimirlo. Para suprimir un modelo de traducción personalizado, utilice el método `DELETE /v2/models/<model_id>`. Para recuperar los ID de modelo de todos los modelos de traducción, ya sean personalizados o predeterminados, utilice el método `GET /v2/models`.

El mandato siguiente suprime el modelo de traducción que se ha creado en estos ejemplos.

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}


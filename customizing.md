---

copyright:
  years: 2015, 2017
lastupdated: "2018-04-18"

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

# Customizing your model
{: #customizing}

Some of the provided translation models in {{site.data.keyword.languagetranslatorshort}} can be extended to learn custom terms and phrases or a general style that's derived from your translation data. Follow these instructions to create your own custom translation model.
{: shortdesc}

## Before you begin
{: #before-you-begin}

1. Make sure that your {{site.data.keyword.languagetranslatorshort}} service instance is on an Advanced or Premium pricing plan. The Lite and Standard plans do not support customization.
1. Find a customizable base model for your language pair. You will need the model ID of the base model in order to train your custom model.
    - Search the models listed on the [Translation models](translation-models.html) page. Look for the value "**true**" in the **Customizable** column, and make sure the **Source** and **Target** languages of the model match your language pair.
    - Alternatively, you can use the [List models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models) API method to search models programmatically. You can filter results by language with the `source` and `target` parameters.

## Step 1: Create your training data
{: #create-your-training-data}

The training data format you need to provide depends on which of the following customization options you choose. You can store up to 10 customizations per service instance, and the cumulative file size of all uploaded glossary and corpus files is limited to 250 MB.

- Use a [forced glossary](#forced-glossary) to force certain terms and phrases to be translated in a specific way.
- Use a [parallel corpus](#parallel-corpus) when you want your custom model to learn from general translation patterns in your samples. What your model learns from a parallel corpus can improve translation results for input text that the model hasn't been trained on.
- Use a [monolingual corpus](#monolingual-corpus) to improve the general style of translations without providing explicit translation examples.

The base models are trained to perform best on factual content with proper grammar and capitalization. If you plan to translate informal content, make sure to provide examples of informal language, slang, commands, exclamatory phrases, or types of questions that you wouldn't expect to find in formal publications.
{: tip}

After you have created either a [Translation Memory Exchange (TMX) file](#tmx-files) for forced glossary or parallel corpus customization,
or a plain text file for monolingual corpus customization, you're ready to train your model.

## Step 2: Train your model
{: #train-your-model}

Use the [Create model ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#create-model) method to train your model. In your request, specify the model ID of a customizable base model, and training data in one or more of the `forced_glossary`, `parallel_corpus`, or `monolingual_corpus` parameters.

### Example request
The following example request uses a forced glossary file, _glossary.tmx_, to customize the `en-fr` base model. See the [Forced glossary customization](#forced-glossary) section for an example forced glossary TMX file. 

```bash
curl --user "{username}":"{password}" -X POST --form base_model_id="en-fr" --form forced_glossary=@glossary.tmx https://gateway.watsonplatform.net/language-translator/api/v2/models
```
{: pre}

The API response will contain details about your custom model, including its model ID. Use the model ID to check the status of your model, and to translate sentences once the model is available.

```json
{
  "model_id": "96221b69-8e46-42e4-a3c1-808e17c787ca",
  "source": "en",
  "target": "es",
  "base_model_id": "en-es",
  "domain": "news",
  "customizable": false,
  "default_model": false,
  "owner": "4937aab7-0f3a-4a75-bee1-0b7a12b6b8",
  "status": "uploaded",
  "name": "custom-english-to-spanish",
  "train_log": null
}
```
{: codeblock}

## Step 3: Check the status of your model
{: #check-model-status}

Model training might take anywhere from a couple of minutes to several hours depending on how much training data is involved. To see if your model is available, use the [Get model ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#get-model) method and specify the model ID that you saw in Step 2. Also, you can check the status of all of your models with the [List models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/curl.html#list-models) method.

The `status` response attribute describes the state of the model in the training process:

- `uploading`
- `uploaded`
- `dispatching`
- `queued`
- `training`
- `trained`
- `publishing`
- `available`

When the model status is `available`, your model is ready to use with your service instance. If your model is deleted, or if it encounters an error in the training process, you might see one of the following statuses:

- `deleted`
- `error`

### Example request
The following example gets information for the model identified by the model ID `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```bash
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/96221b69-8e46-42e4-a3c1-808e17c787ca"
```
{: pre}

## Step 4: Translate text with your custom model
{: #translate-text}

To use your custom model, specify the text that you want to translate and the custom model's model ID in the [Translate ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/curl.html#translate) method.

### Example request
The following example translates text with the custom model identified by the model ID `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```bash
curl -u "{username}":"{password}" -X POST -H "Accept: application/json" -d "{\"text\":\"Hello\",\"model_id\":\"96221b69-8e46-42e4-a3c1-808e17c787ca\"}" "https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: pre}


## Forced glossary customization
{: #forced-glossary}

Use a **forced glossary** to set mandatory translations for specific terms and phrases. If you want specific control over translation behavior, use a forced glossary.

- Training data format: [TMX](#tmx-files) (UTF-8 encoded)
- Maximum file size: 10 MB

Forced glossary examples are sensitive to capitalization, so make sure that your training data reflects the capitalization of content that your application will encounter.
{: tip}

### Forced glossary example

The following example shows a TMX file with two translation pairs. The first pair forces "international business machines" to be preserved in English during translation. This type of forced translation might be useful if you want to preserve improperly capitalized company names in informal communications. The second pair forces the model to always use "brevet" when translating "patent".

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



## Parallel corpus customization
{: #parallel-corpus}

Use a **parallel corpus** to provide additional translations for the base model to learn from. How the resulting custom model translates text depends on the model's combined understanding of the parallel corpus and the base model.

- Training data format: [TMX](#tmx-files) (UTF-8 encoded)
- Minimum number of translation pairs: 5,000
- Maximum file size: 250 MB

### Parallel corpus example

The following is a small piece of an English to French parallel corpus that was downloaded from the [MultiUN collection ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://opus.nlpl.eu/MultiUN.php) available on the OPUS open parallel corpus website. You can download a compressed version of the entire TMX file [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz).


```xml
<?xml version="1.0" encoding="UTF-8" ?>
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

The general improvements from parallel corpus customization are less predictable than the mandatory results you get from forced glossary customization. For example, consider the following translation unit from the example parallel corpus (lines 172-175).

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

If you translate "55/102. Globalization and its impact on the full enjoyment of all human rights" with the base `en-fr` model, the service responds with the following translation.

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

When the same input sentence is translated by a custom model trained with the example corpus, the service responds with a different translation that is not identical to the sample translation provided in the training data.

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- The custom model translates "the full enjoyment" to "le plein exercice" instead of "la pleine jouissance". The likely explanation for this deviation from the base model behavior is that there are many examples in the corpus where "enjoyment" is translated to "exercice".
- The custom model translates "of all human rights" to "de tous les droits de l'homme" instead of reproducing the result from the translation unit, "des droits de l'homme". This behavior reflects the trained model's cohesive understanding of the base model, and all of the translation samples that are related "of all human rights" from the parallel corpus.

In some cases it might seem that a custom model trained with a parallel corpus is ignoring a specific example that you provided. In these cases, try searching your training data for other sentences that might be influencing the translation behavior, or consider using a forced glossary if you want to control a specific translation.

## Monolingual corpus customization
{: #monolingual-corpus}

Use a **monolingual corpus** to improve the general translation style of your model. Provide a plain text file in the target language, and the service will supplement the base model with general patterns and style that it learns from the text.

- Training data format: plain text (UTF-8 encoded)
- Minimum number of sentences: 1,000

## Creating TMX files
{: #tmx-files}

To provide a glossary or corpus of terms for training the {{site.data.keyword.languagetranslatorshort}} service, create a valid UTF-8 encoded document that conforms to the Translation Memory Exchange (TMX) [version 1.4 ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ttt.org/oscarStandards/tmx/){: new_window} specification. TMX is an XML specification that is designed for machine-translation tools. The following example is a TMX-formatted glossary file with two translation units (`<tu>` elements):

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

Each term and translation pair must be enclosed in `<tu>` tags:

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

The`xml:lang` attribute in the `<tuv>` tag identifies the language in which a term is expressed, while the `<seg>` tag contains the term or the translation.

The {{site.data.keyword.languagetranslatorshort}} service uses only the `<tu>`, `<tuv>`, and `<seg>` elements. All other elements in the example are required to make a valid TMX file, or are informational, but are not used by the service.



### Using the example as a template

To use the provided example as a template for your own glossary or corpus, complete the following steps:

1. Copy and paste the example into a text editor.

1. Change the `srclang` attribute of the `<header>` tag to the [language code ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} of the source language that your glossary or parallel corpus uses.

1. Change the `xml:lang` attribute of the `<tuv>` tags to the correct [language code ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} for each term or translation.

1. Save the document with the extension `.tmx` and UTF-8 encoding.

### Changing a TMX file to UTF-8 encoding

You can use a number of tools to create or generate TMX files. Often, generated TMX files are UTF-16 encoded by default. The {{site.data.keyword.languagetranslatorshort}} service accepts only UTF-8 encoded TMX files. To change the encoding of a TMX file, complete the following steps:

1. Open the TMX file in a text editor.

1. Change the XML header (if present) from `<?xml ... encoding="utf-16"?>` to `<?xml ... encoding="utf-8"?>`.

1. Save the file with a new name and with UTF-8 encoding output.

Mac users can also change file encoding by updating the XML header of the document as described in step 2, and then running the following command in the Terminal:

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}


## Deleting a custom translation model
{: #deleting-a-custom-model}

To delete a custom translation model, use the [Delete model ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/curl.html#delete-model) method.

The following command deletes the translation model with model ID `3e7dfdbe-f757-4150-afee-458e71eb93fb`.

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}




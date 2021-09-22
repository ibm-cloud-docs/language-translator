---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-22"

keywords: customize,custom models

subcollection: language-translator

---

{{site.data.keyword.attribute-definition-list}}

# Customizing your model
{: #customizing}

Most of the provided translation models in {{site.data.keyword.languagetranslatorshort}} can be extended to learn custom terms and phrases or a general style that's derived from your translation data. Follow these instructions to create your own custom translation model.
{: shortdesc}

## Before you begin
{: #before-you-begin}

1.  Make sure that your {{site.data.keyword.languagetranslatorshort}} service instance is on an Advanced or Premium pricing plan. The Lite and Standard plans do not support customization.
1.  Copy the `API Key` and `URL` values for your service instance. For more information about finding the values, see [Getting started with {{site.data.keyword.languagetranslatorshort}}](/docs/language-translator?topic=language-translator-gettingstarted).
1.  Find a customizable base model for your language pair. You need the model ID of the base model in order to train your custom model.
    -   Search the customizable models listed on the [Supported languages for translation](/docs/language-translator?topic=language-translator-translation-models) page. Look for the value "**true**" in the **Customizable** column, and make sure the **Source** and **Target** languages of the model match your language pair.
    -   Alternatively, you can use the [List models](https://{DomainName}/apidocs/language-translator#listmodels){: external} method to search models programmatically. You can filter results by language with the `source` and `target` parameters.

## Step 1: Create your training data
{: #create-your-training-data}

The service supports two types of customization:

-   Use a [forced glossary](#forced-glossary-customization) to force certain terms and phrases to be translated in a specific way.
-   Use a [parallel corpus](#parallel-corpus-customization) when you want your custom model to learn from general translation patterns from parallel sentences in your samples. What your model learns from a parallel corpus can improve translation results for input text that the model hasn't been trained on.

To create a model that is customized with both parallel corpora and a forced glossary, proceed in two steps:

1.  Customize with at least one parallel corpus file. You can upload multiple parallel corpus files with a single request. To successfully train with parallel corpora, all corpus files combined must contain at least 5000 parallel sentences. The cumulative size of all uploaded corpus files for a custom model is limited to 250 MB.
1.  Customize the resulting model with a forced glossary. You can upload a single forced glossary file for a custom model. The size of a forced glossary for a custom model is limited to 10 MB.

You can store a maximum of 10 custom models for each language pair in a service instance.

The service supports multiple document formats for uploading training data. The following examples use Translation Memory eXchange (TMX), an XML-based specification for the exchange of translation memories. For more information about all supported formats, see [Supported document formats for training data](#supported-document-formats-for-training-data).

After you create your training data documents, you're ready to train your model.

## Step 2: Train your model
{: #train-your-model}

Use the [Create model](https://{DomainName}/apidocs/language-translator#createmodel){: external} method to train your model. In your request, specify the model ID of a customizable base model and the training data in either the `forced_glossary` or `parallel_corpus` parameters.

### Example request
{: #train-model-example-request}

The following example request uses a forced glossary file, **glossary.tmx**, to customize the `en-es` base model. For an example of the forced glossary TMX file, see [Forced glossary customization](#forced-glossary-customization).

Replace `{apikey}` and `{url}` with the service credentials you copied in the first step.

```sh
curl -X POST --user "apikey:{apikey}" \
--form forced_glossary=@glossary.tmx \
"{url}/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

The API response contains details about your custom model, including its model ID. Use the model ID to check the status of your model and to translate sentences once the status of the model becomes `available`.

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

## Step 3: Check the status of your model
{: #check-model-status}

Model training might take anywhere from a couple of minutes (for forced glossaries) to several hours (for large parallel corpora) depending on how much training data is involved. To see if your model is available, use the [Get model details](https://{DomainName}/apidocs/language-translator/language-translator#getmodel){: external} method and specify the model ID that you received in the service response in Step 2. Also, you can check the status of all of your models with the [List models](https://{DomainName}/apidocs/language-translator/language-translator#listmodels){: external} method.

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
{: #check-model-example-request}

The following example gets information for the model identified by the model ID `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```sh
curl -X GET --user "apikey:{apikey}" \
"{url}/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## Step 4: Translate text with your custom model
{: #customize-translate-text}

To use your custom model, specify the text that you want to translate and the custom model's model ID in the [Translate](https://{DomainName}/apidocs/language-translator/language-translator#translate){: external} method.

### Example request
{: #translate-text-example-request}

The following example translates text with the custom model identified by the model ID `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```sh
curl -X POST --user "apikey:{apikey}" \
--header "Content-Type: application/json" \
--data "{\"text\":\"Hello\",\"model_id\":\"96221b69-8e46-42e4-a3c1-808e17c787ca\"}" \
"{url}/v3/translate?version=2018-05-01"
```
{: pre}

The `/v3/translate` method accepts a maximum of 50 KB of input text encoded in UTF-8 format for translation.
{: note}

## Forced glossary customization
{: #forced-glossary-customization}

Use a forced glossary to set mandatory translations for specific terms and phrases. If you want specific control over translation behavior, use a forced glossary.

- Encoding: UTF-8.
- Maximum file size: 10 MB.
- You can apply a forced glossary to a base model or to a model that has been customized with parallel corpora.
- You are limited to one forced glossary per custom model.
- You can submit a single forced glossary by using the `forced_glossary` multipart form parameter.

Forced glossary translations are case-sensitive. Make sure that your training data reflects the capitalization of the content that your application will encounter.
{: tip}

### Forced glossary example
{: #forced-glossary-example}

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
{: #parallel-corpus-customization}

Use a parallel corpus to provide additional translations for the base model to learn from. This helps to adapt the base model to a specific domain. How the resulting custom model translates text depends on the model's combined understanding of the parallel corpus and the base model.

- Encoding: UTF-8.
- Maximum length of translation pairs: 80 source words (longer input is ignored).
- Minimum number of translation pairs: 5000 for all corpora combined.
- Maximum number of translation pairs: 500,000 for all corpora combined.
- Maximum (cumulative) file size: 250 MB for all corpora combined.
- You can submit multiple parallel corpus files by repeating the `parallel_corpus` multipart form parameter.

### Parallel corpus example
{: #parallel-corpus-example}

The following is a small piece of an English to French parallel corpus that was downloaded from the [MultiUN collection](http://opus.nlpl.eu/MultiUN.php){: external} available on the OPUS open parallel corpus website. You can download a compressed version of the entire TMX file: [en-fr.tmx.gz](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz){: external}.

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
    . . .
  </body>
</tmx>
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

```text
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

When the same input sentence is translated by a custom model trained with the example corpus, the service responds with a different translation that is not identical to the sample translation provided in the training data.

```text
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- The custom model translates "the full enjoyment" to "le plein exercice" instead of "la pleine jouissance". The likely explanation for this deviation from the base model behavior is that there are many examples in the corpus where "enjoyment" is translated to "exercice".
- The custom model translates "of all human rights" to "de tous les droits de l'homme" instead of reproducing the result from the translation unit, "des droits de l'homme". This behavior reflects the trained model's cohesive understanding of the base model, and all of the translation samples that are related "of all human rights" from the parallel corpus.

In some cases, it might seem that a custom model trained with a parallel corpus is ignoring a specific example that you provided. In these cases, try searching your training data for other sentences that might be influencing the translation behavior, or consider using a forced glossary if you want to control a specific translation.

## Supported document formats for training data
{: #supported-document-formats-for-training-data}

You can provide your training data for customization in the following document formats.

| Format | Extension | Description |
|---|---|---|
| [TMX](#tmx) | `.tmx` | Translation Memory eXchange (TMX) is an XML specification for the exchange of translation memories. |
| [XLIFF](#xliff) | `.xliff` | XML Localization Interchange File Format (XLIFF) is an XML specification for the exchange of translation memories. |
| [CSV](#csv)  | `.csv` | Comma-separated values (CSV) file with two columns for aligned sentences and phrases. The first row contains the language code.  |
| [TSV](#tsv)  | `.tsv`, `.tab`  | Tab-separated values (TSV) file with two columns for aligned sentences and phrases. The first row contains the language code.  |
| [JSON](#json) | `.json` | Custom JSON format for specifying aligned sentences and phrases.  |
| [Microsoft Excel](#excel) | `.xls`, `.xlsx` | Excel file with the first two columns for aligned sentences and phrases. The first row contains the language code. |
{: caption="Table 1. Document formats for training data"}

All formats have in common that they specify an alignment of translated text segments (sentences or phrases). You must encode all text data in UTF-8 format. For an example of how to convert a TMX file to UTF-8 format, see [Changing a TMX file to UTF-8 encoding](#changing-tmx-file-to-utf-8).

You upload all training data files to the service as part of a `multipart/form-data` request. To indicate the type of the format (for example, TMX or CSV), either use the correct file extension (for example, `.tmx` or `.csv`) in the file name or set the `content-type` parameter for the respective part of the `multipart/form-data` request (for example, to `--form "forced_glossary=@glossary;type=text/csv"` for a CSV file).

### TMX
{: #tmx}

One option to provide a glossary or corpus of aligned text segments for training the {{site.data.keyword.languagetranslatorshort}} service is to create a valid UTF-8 encoded document that conforms to the [Translation Memory Exchange (TMX) version 1.4 specification](http://www.ttt.org/oscarStandards/tmx/){: external}. TMX is an XML specification that is designed for machine-translation tools. Submit files to the service either with the file extension `.tmx` or a `content-type` of `application/x-tmx+xml`. The following example is a TMX-formatted glossary file with two translation units (`<tu>` elements):

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

Each term and translation pair must be enclosed in `<tu>` tags. The `xml:lang` attribute in the `<tuv>` tag identifies the language in which a term is expressed. The `<seg>` tag contains the term or the translation.

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

The {{site.data.keyword.languagetranslatorshort}} service uses only the `<tu>`, `<tuv>`, and `<seg>` elements. All other elements in the example are required to make a valid TMX file, or are informational, but are not used by the service.

#### Escaping XML control characters
{: #tmx-xml-characters}

The following characters are reserved as control characters in XML. You must escape these reserved characters by replacing them with equivalent XML entities.

-   `&` must be replaced with `&amp;`.
-   `<` must be replaced with `&lt;`.
-   `>` must be replaced with `&gt;`.

For example, the `<seg>` element can contain an inline `<subtag>` element. You need to escape the characters in this inline element by specifying it as `&lt;subtag&gt;`.

#### Using the example as a template
{: #using-the-example-template}

To use the provided example as a template for your own glossary or corpus, complete the following steps:

1. Copy and paste the example into a text editor.

2. Change the `srclang` attribute of the `<header>` tag to the [language code](http://www-01.sil.org/iso639-3/codes.asp){: external} of the source language that your glossary or parallel corpus uses.

3. Change the `xml:lang` attribute of the `<tuv>` tags to the correct [language code](http://www-01.sil.org/iso639-3/codes.asp){: external} for each term or translation.

4. Save the document with the extension `.tmx` and UTF-8 encoding.

#### Changing a TMX file to UTF-8 encoding
{: #changing-tmx-file-to-utf-8}

You can use a number of tools to create or generate TMX files. Often, generated TMX files are UTF-16 encoded by default. The {{site.data.keyword.languagetranslatorshort}} service accepts only UTF-8 encoded TMX files. To change the encoding of a TMX file, complete the following steps:

1. Open the TMX file in a text editor.

1. Change the XML header (if present) from `<?xml ... encoding="utf-16"?>` to `<?xml ... encoding="utf-8"?>`.

1. Save the file with a new name and with UTF-8 encoding output.

Mac users can also change file encoding by updating the XML header of the document as described in step 2, and then running the `iconv` command as shown in the following example:

```sh
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}

### XLIFF
{: #xliff}

The service supports [XLIFF version 1.2](http://docs.oasis-open.org/xliff/v1.2/os/xliff-core.html). Submit files to the service either with the file extension `.xliff` or a `content-type` of `application/xliff+xml`. The service interprets only the part of XLIFF that can be used to encode aligned text segments. You must ensure that your data has a structure like the following example:

```xml
<xliff version='1.2' xmlns='urn:oasis:names:tc:xliff:document:1.2'>
  <file original='original.txt' source-language='en' target-language='es' datatype='plaintext'>
    <body>
      <group>
        <trans-unit id='sentence1'>
          <source>Hello World</source>
          <target>Hola mundo</target>
        </trans-unit>
        . . .
      </group>
    </body>
  </file>
</xliff>
```
{: codeblock}

You must escape the reserved XML control characters `&`, `<`, and `>` with equivalent XML entities. For more information, see [Escaping XML control characters](#tmx-xml-characters).

### CSV
{: #csv}

The service supports comma-separated values (CSV) files that follow the [RFC 4180 specification](https://tools.ietf.org/html/rfc4180). Submit files to the service with either the file extension `.csv` or a `content-type` of `text/csv`. You must structure the CSV file as follows:

- The first row must have two language codes. The first column is for the source language code, and the second column is for the target language code.
- All subsequent rows must have translation pairs, and each row must have two columns. The first column is for the source sentence, and the second column is for the translated sentence. The value in the second column must not be followed by a comma.
- Spaces are considered part of a field and are not ignored.
- Fields that contain line breaks (CRLF), double-quotes, and commas must be enclosed in double-quotes.
- If double-quotes are used to enclose fields, then a double-quote appearing inside a field must be escaped by preceding it with another double quote. For example, `"Hello, following is an escaped double quote ""."`

#### Example
{: #csv-example}

The following simple example shows alignment between English and Spanish text segments. The second line shows how to escape a comma that appears in the text segment by using double-quotes.

```text
en,es
Hello World,Hola mundo
"Hello, World!","Hola, mundo!"
```
{: codeblock}

### TSV
{: #tsv}

The service supports tab-separated values (TSV) files. Submit files to the service with either the file extension `.tsv, .tab` or a `content-type` of `text/tab-separated-values`. You must structure the TSV file like a CSV file, except for using a tab character as the separator instead of a comma.

### JSON
{: #json}

The service supports a simple JSON format for submitting aligned text segments. Submit files to the service with either the file extension `.json` or a `content-type` of `application/json`. You must structure the JSON file as follows:

```json
{
  "sentences": [
    [
      {
        "language": "en",
        "sentence": "Hello"
      },
      {
        "language": "es",
        "sentence": "Hola"
      },
      . . .
    ],
    . . .
  ]
}
```
{: codeblock}

### Microsoft Excel
{: #excel}

The service supports Microsoft Excel files. Submit files to the service either with the file extension `.xlsx` or `.xls` or with a `content-type` of `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet`. Like CSV, a file must be structured as follows:

- The first row must have language codes in two columns. The first column is for the source language code. The second column is for the target language code.
- All subsequent rows must have translation pairs. Each row must have two columns. The first column is for the source sentence. The second column is for the translated sentence.

## Deleting a custom translation model
{: #deleting-a-custom-model}

To delete a custom translation model, use the [Delete model](https://cloud.ibm.com/language-translator#delete-model){: external} method. The following example deletes the translation model with the model ID `3e7dfdbe-f757-4150-afee-458e71eb93fb`.

```sh
curl -X DELETE --user "apikey:{apikey}" \
"{url}/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: pre}

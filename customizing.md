---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-31"

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

Are you creating a translator for use by customer support, and have company-specific terms that you want dealt with in a certain way in conversations? Are you creating a way for your engineers in one country to look up patent data in another language, and you usually file patents on a specific technology? Use your own data to create a custom dictionary and a custom translation model in the {{site.data.keyword.languagetranslatorshort}} API.
{: shortdesc}

You can customize the {{site.data.keyword.languagetranslatorshort}} model in the following ways:

- Teach the service about pairs of matching terms or phrases in a source and target language. Provide a *forced glossary*, which contains pairs of terms or phrases that are absolute, definitive terms that you want the translation service to treat as mandatory. Or provide a *parallel corpus*, which contains pairs of terms or phrases that serve as alternate translation suggestions that you want the translation service to consider.
- Upload a large body of text in a target language (referred to as a *monolingual corpus*) to serve as a language sample that the service can evaluate and use to improve overall translation quality.

To see the list of models that you can customize, use the `GET /v2/models` method and look for the response parameter `customizable=true` in the response for each language model.

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

Each customizable model can store up to 10 customizations per service instance.

## Structure of the training data
{: #structure}

To provide a glossary or corpus of terms for training the {{site.data.keyword.languagetranslatorshort}} service, create a valid UTF-8 encoded document that conforms to the Translation Memory Exchange (TMX) [version 1.4 ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ttt.org/oscarstandards/tmx/tmx14.dtd){: new_window} specification. TMX is an XML specification that is designed for machine-translation tools. The following example is a TMX-formatted glossary file with two term and translation pairs:

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
        <seg>brevent</seg>
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
    <seg>International Business Machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

The`xml:lang` attribute in the `<tuv>` tag identifies the language in which a term is expressed, while the `<seg>` tag contains the term or the translation.

The {{site.data.keyword.languagetranslatorshort}} service uses only the `<tu>`, `<tuv>`, and `<seg>` elements. All other elements in the example are required to make a valid TMX file, or are informational, but are not used by the service.

The previous example shows how to definitively standardize the translation of a technical term, like 'patent', and how to customize the translation of a company name like 'International Business Machines'. Under the standard model, 'International Business Machines' might translate to 'Machines Commerciales Internationales', but it should actually not be translated because it is the name of a company.

## Using the example as a template

To use the provided example as a template for your own glossary or corpus, complete the following steps:

1.  Copy and paste the example into a text editor.

1.  Change the `srclang` attribute of the `<header>` tag to the [language code ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} of the source language that your glossary or parallel corpus uses.

1.  Change the `xml:lang` attribute of the `<tuv>` tags to the correct [language code ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} for each term or translation.

    The {{site.data.keyword.languagetranslatorshort}} service uses ISO 639-1 language codes for all languages except Egyptian Arabic, which uses the ISO 639-3 code.

1.  Save the document with the extension `.tmx` and UTF-8 encoding.

### Changing a TMX file to UTF-8 encoding

You can use a number of tools to create or generate TMX files. Often, generated TMX files are UTF-16 encoded by default. The {{site.data.keyword.languagetranslatorshort}} service accepts only UTF-8 encoded TMX files. To change the encoding of a TMX file, complete the following steps:

1.  Open the TMX file in a text editor.

1.  Change the XML header (if present) from `<?xml ... encoding="utf-16"?>` to `<?xml ... encoding="utf-8"?>`.

1.  Save the file with a new name and with UTF-8 encoding output.

Mac users can also change file encoding by updating the XML header of the document as described in step 2, and then running the following command in the Terminal:

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}

## Training a custom translation model
{: #training}

Use the `POST /v2/models` method to upload your TMX file and train your translation model. Specify at least one of the following file options to train your custom model:

- `forced_glossary`: A UTF-8 encoded TMX file that contains pairs of matching terms in the source and target language that are seen as absolute by the system. This file completely overwrites the original domain data.

    Forced glossaries are limited to a file size of 10 MB. You can currently only upload one forced glossary file per translation model.
    
- `parallel_corpus`: A UTF-8 encoded TMX file that contains matching phrases in the source and target language that serve as examples for Watson. Parallel corpora differ from forced glossaries because they do not overwrite the original domain data.

    To successfully train a custom model, a parallel corpus document must contain a minimum of 5,000 term and translation pairs.
    
- `monolingual_corpus`: A UTF-8 encoded plain text file that contains a body of text in the target language that is related to what you are translating. Providing a monolingual corpus improves literal translations by making the translation more fluent and natural.

    To successfully train a custom model, a monolingual corpus document must contain a minimum of 1,000 sentences.

The cumulative file size of all uploaded glossary and corpus files is limited to 250MB. Depending on the size of the uploaded files, training can range from minutes for a glossary to several hours for a large corpus.

The following curl example uses the `forced_glossary` file option.
1. Download the TMX file sample from the [Structure of the training data](#structure) section
1. Use the French news domain (en-fr) as the base model. Anything that is specified in the TMX file completely overwrites the original domain data.

    To look up all of the model domains that the {{site.data.keyword.languagetranslatorshort}} service supports, use the `GET v2/models` method:

```curl
curl -u "{username}":"{password}" -X POST -F base_model_id=en-fr -F name="test_glossary" -F forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

The `POST /v2/models` method responds with a `200` code and a new `model_id`. Use the `model_id` when you translate text with this newly customized model.

## Monitoring training

The size of your TMX training file affects the training time of a `POST /v2/models` request. To monitor the progress of the training and whether the training completes successfully, use the `GET /v2/models/<model_id>` method and look at the value of the `status` parameter in the response.

This example command gives information about the model, and checks the status of the training that was begun in the [Training your translation model](#training) section. This command uses an empty body request.

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}

The `STATUS` response parameter describes the state of the model in the training process:

- `uploading`
- `uploaded`
- `dispatching`
- `queued@<#>`
- `training`
- `trained`
- `publishing`
- `available`

When the model status is `available`, your model is ready to use with your service instance. If your model is deleted, or if it encounters an error in the training process, you might see one of the following errors:

- `deleted`
- `error`

## Using a custom translation model

After you train a custom translation model, specify the model\_id of that translation model to use it with the `POST /v2/translate` or the `GET /v2/translate` methods.

The following example invokes the English to French model that was customized in the [Training a custom translation model](#training) section.

```curl
curl -u "{username}":"{password}" --header "Content-Type: application/json" -X POST --data {"model_id": "3e7dfdbe-f757-4150-afee-458e71eb93fb","text": ["Hello, my name is Watson, and I work for International Business Machines. How can I help you today?"]}
```
{: codeblock}

The {{site.data.keyword.languagetranslatorshort}} service evaluates the quality of the translation by using the BLEU (bilingual evaluation understudy) standards, as well as IBM-developed standards. Results may vary depending on the language pair, vernacular used, or the domain of your data.

## Deleting a custom translation model

When a translation model becomes outdated, you might want to delete it. To delete a custom translation model, use the `DELETE /v2/models/<model_id>` method. To retrieve the model IDs of all translation models, whether custom or default, use the `GET /v2/models` method.

The following command deletes the translation model that was created in these examples.

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}


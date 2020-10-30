---

copyright:
  years: 2015, 2020
lastupdated: "2020-10-30"

subcollection: language-translator

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:pre: .pre}
{:beta: .beta}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Translating documents (Beta)
{: #document-translator-tutorial}

You can use the {{site.data.keyword.languagetranslatorfull}} service to translate files from one language to another while preserving the original document format. The service supports translation of many file formats, including Microsoft Office, Open Office, subtitles, PDF, and other formats such as HTML, XML, and JSON.
{:shortdesc}

Document translation is currently a beta feature. Translation of PDF documents is experimental.
{: beta}

## Before you begin
{: #translate-prerequisites}

Make sure that you have the following information and meet the following requirements:

-   You need your {{site.data.keyword.languagetranslatorshort}} service credentials (`apikey` and `url`). For more information, see [Getting started with {{site.data.keyword.languagetranslatorshort}}](/docs/language-translator?topic=language-translator-gettingstarted).
-   The document that you want to translate must not exceed the following size limits:
    -   **20 MB** for service instances on the Standard, Advanced, and Premium plans
    -   **2 MB** for service instances on the Lite plan
-   The document must be in one of the [Supported file formats (Beta)](#supported-file-formats) or [Supported file formats (Experimental)](#supported-file-formats-experimental).
-   The source and target languages must be among the [Supported translation models](/docs/language-translator?topic=language-translator-translation-models).

This tutorial walks you through translating documents from the command line with `curl`. You can also use the {{site.data.keyword.watson}} SDKs to translate documents with a number of programming languages. For more information, see the methods in the [API & SDK reference](https://{DomainName}/apidocs/language-translator){: external}.

## Step 1: Submit a document to translate
{: #submit-document-to-translate}

The following example request submits the file **curriculum.html** to the service and translates it from English to French. Replace `{apikey}` and `{url}` with your service credentials, and replace `curriculum.html` with a relative path to your file. The `source` and `target` parameters specify the languages for the translation.

```sh
curl -X POST --user "apikey:{apikey}" \
--form "file=@curriculum.html" \
--form "source=en" \
--form "target=fr" \
"{url}/v3/documents?version=2018-05-01"
```
{: pre}

Microsoft Windows users, replace the backslash (`\`) at the end of each line with a caret (`^`). Make sure there are no trailing spaces after the caret.
{: tip}

To translate a document with a [custom model](/docs/language-translator?topic=language-translator-customizing), use the `model_id` parameter. The following request translates the document with the custom model identified by the model ID `96221b69-8e46-42e4-a3c1-808e17c787ca`. The custom model is defined for `en-fr` translation, so the `source` and `target` parameters are not needed.

```sh
curl -X POST --user "apikey:{apikey}" \
--form "file=@curriculum.html" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
"{url}/v3/documents?version=2018-05-01"
```
{: pre}

A successful translation request returns a document ID in the response. In the following example, the ID is `bae02796-0d28-435c-9115-888359fdde62`. The `status` of `processing` indicates that the service is translating the document.

```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.html",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "processing",
  "created": "2018-10-11T03:31:25"
}
```
{: codeblock}

## Step 2: Check the translation status
{: #check-translation-status}

After you have submitted a document for translation, you can check the translation status to find out when the translated document is available to download. The following example request checks the translation status of the document with ID `bae02796-0d28-435c-9115-888359fdde62`. When the `status` in the response is `available`, the translated document is ready to download.

```sh
curl -X GET --user "apikey:{apikey}" \
"{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01"
```
{: pre}

```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.html",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "available",
  "created": "2018-10-11T03:31:25",
  "completed": "2018-10-11T03:31:38"
}
```
{: codeblock}

## Step 3: Download the translated document
{: #download-translated-document}

The following example request saves the translated document with ID `bae02796-0d28-435c-9115-888359fdde62` to a file named `curriculum-fr.html`.

```sh
curl -X GET --user "apikey:{apikey}" \
--output "curriculum-fr.html" \
"{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01"
```
{: pre}

## Step 4: Translate a previously submitted document
{: #translate-document-by-reference}

The following example request translates the original English file **curriculum.html**, which has document ID `bae02796-0d28-435c-9115-888359fdde62`, to Portuguese.

```sh
curl -X POST --user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
"{url}/v3/documents?version=2018-05-01"
```
{: pre}

```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

The response contains a new document ID. Repeat step two with the new document ID to check the status of the translation. When the status becomes `available`, use the new document ID to download the translated file as shown in step three.

## Step 5: Delete documents
{: #delete-documents}

The service automatically deletes original documents and any associated translated documents after they have not been used for a certain period of time. For more information, see [Information security](/docs/language-translator?topic=language-translator-information-security).

To delete documents manually, use the **Delete document** method. In this tutorial, the English file **curriculum.html** was involved with two translations, so two requests are required to delete all copies of the original document.

Delete the original submission of **curriculum.html** and the French translation by using the document ID for that translation, `bae02796-0d28-435c-9115-888359fdde621`:

```sh
curl -X DELETE --user "apikey:{apikey}" \
"{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01"
```
{: pre}

Delete the duplicate of the original **curriculum.html** file and the Portuguese translation by the using the document ID for that translation, `a0ge2746-ad38-7d5c-7025-4cd3g9f451ab`:

```sh
curl -X DELETE --user "apikey:{apikey}" \
"{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01"
```
{: pre}

## Supported file formats (Beta)
{: #supported-file-formats}

Translation of the following file formats is beta functionality:

-   Microsoft Office formats:
    - Word: `.doc`, `.docx`
    - PowerPoint: `.ppt`, `.pptx`
    - Excel: `.xls`, `.xlsx`
    - Rich Text Format: `.rtf`
-   Open Office formats:
    - Writer: `.odt`
    - Impress: `.odp`
    - Calc: `.ods`
-   Other formats:
    - HTML: `.htm`, `.html`
    - XML: `.xml`
    - JSON: `.json` (values with type `string` or `string array` are translated)
    - Text: `.txt`

### Subtitle formats (Beta)
{: #supported-file-formats-subtitles}

Translation of the following subtitle (or caption) formats is beta functionality:

-   SubRip: `.srt`
-   SubViewer: `.sbv`
-   DirectVobSub or VSFilter: `.sub`
-   MicroDVD: `.sub`
-   WebVTT: `.vtt`

These textual formats contain the transcript of a sound track or video source. The formats provide plain text that is intuitively comprehensible with minimal syntax. They include a list of cues that contain synchronization information for the media source. They can also include metadata that is not intended for display.

The following information qualifies some of the nuances of subtitle translation:

-   *Character encoding* - Subtitles can be presented in different character sets. The service supports only UTF-8 input and produces only UTF-8 output. The results maintain the line separation and optional Byte Order Mark (BOM) from the original source.
-   *Markup* - The service attempts to preserve markup in the translated document, but preservation is not guaranteed. The service can silently remove markup from a particular cue.
-   *Names* - By convention, speaker names can be marked with `-..:`, parentheses, or both. The service extracts and translates speaker names separately to guarantee consistent translation.
-   *Paragraphs* - The text to be translated is grouped into paragraphs. Each paragraph can span multiple cues, but it always consists of a full set of cue lines. In other words, each paragraph consists of one or more cues in their entirety, with each cue contained fully in a single paragraph.

    A single cue can contain one or more lines of text (for example, two short sentences). The service creates paragraph breaks only at cue line boundaries to preserve the count of lines in the cue. For languages with punctuation, a paragraph generally maps to a complete sentence. For languages without punctuation, a paragraph can contain multiple sentences, which can adversely affect the distribution of lines into cues in the translated document.
-   *Comments, notes, and titles* - For formats that permit these elements, the service preserves the original text and adds translation that is prefixed by language code. Because this information is intended for use by the author, the service maintains the text in both its original and translated forms.

## Supported file formats (Experimental)
{: #supported-file-formats-experimental}

Translation of the following file format is experimental functionality:

- PDF: `.pdf`

The quality of PDF translation is still largely an Alpha release. The translation works best for single-column PDF documents that do not include many tables or images. Quality is expected to evolve and improve with future releases.

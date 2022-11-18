---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-18"

subcollection: language-translator

---

{{site.data.keyword.attribute-definition-list}}

# Translating documents
{: #document-translator-tutorial}

You can use the {{site.data.keyword.languagetranslatorfull}} service to translate files from one language to another while preserving the original document format. The service supports translation of many file formats, including Microsoft® Office®, Open Office, subtitles, and many other common formats such as HTML, JSON, XML, and Adobe® PDF.
{: shortdesc}

## Before you begin
{: #translate-prerequisites}

Make sure that you have the following information and meet the following requirements:

-   You need your {{site.data.keyword.languagetranslatorshort}} service credentials (`apikey` and `url`). For more information, see [Getting started with {{site.data.keyword.languagetranslatorshort}}](/docs/language-translator?topic=language-translator-gettingstarted).
-   The document that you want to translate must not exceed the following size limits:
    -   **2 MB** for service instances on the Lite plan
    -   **20 MB** for service instances on the Standard plan
    -   **50 MB** for service instances on the Advanced plan
    -   **150 MB** for service instances on the Premium plan
-   The document must be in one of the supported file formats. Use the correct file extension for the format of the document or specify the content type (MIME type) of the format with the request. For more information, see [Supported file formats](#supported-file-formats).
-   The source and target languages must be among the [List of supported languages](/docs/language-translator?topic=language-translator-translation-models#list-languages-supported).
-   The service correctly translates from and to bidirectional languages that are written left-to-right and right-to-left (for example, Arabic, Hebrew, and Urdu).

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

When translating a previously submitted document, the target language must be different from the target language of the original request when the document was initially submitted.
{: note}

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

## Supported file formats
{: #supported-file-formats}

The service supports translation of Microsoft Office, Open Office, subtitle, and many other common formats. To translate a file, you must identify the format of the file in one of the following ways:

-   By specifying the appropriate file extension for the format. For example, to translate an HTML file named `example.html` from English to French, you would use the following command:

    ```sh
    curl -X POST --user "apikey:{apikey}" \
    --form "file=@example.html" \
    --form "source=en" \
    --form "target=fr" \
    "{url}/v3/documents?version=2018-05-01"
    ```
    {: pre}

-   By specifying the content type (MIME type) of the format as the `type` of the `file` parameter. For example, to translate an HTML file named just `example` from English to French, you would use the following request:

    ```sh
    curl -X POST --user "apikey:{apikey}" \
    --form "file=@example;type=text/html" \
    --form "source=en" \
    --form "target=fr" \
    "{url}/v3/documents?version=2018-05-01"
    ```
    {: pre}

The tables in the following sections list the valid file extensions and content types for each supported format. In most cases, specifying the correct file extension is preferred because it can eliminate ambiguity and is simpler. For subtitles, the table makes clear where the file extension or the content type is needed.

All file formats other than Adobe® PDF (Portable Document Format) are generally available. PDF is currently experimental functionality.
{: note}

### Microsoft Office file formats
{: #supported-file-formats-microsoft-office}

Table 1 lists the Microsoft Office file formats that the service supports for translation.

| File format | File extension | Content type |
|-------------|----------------|--------------|
| Microsoft Excel | `.xls` | `application/vnd.ms-excel` |
|                 | `.xlsx` | `application/vnd.openxmlformats-officedocument.spreadsheetml.sheet` |
| Microsoft PowerPoint | `.ppt` | `application/vnd.ms-powerpoint` |
|                      | `.pptx` | `application/vnd.openxmlformats-officedocument.presentationml.presentation` |
| Microsoft Word | `.doc` | `application/msword` |
|                | `.docx` | `application/vnd.openxmlformats-officedocument.wordprocessingml.document` |
{: caption="Table 1. Microsoft Office file formats"}

Microsoft, Microsoft Excel, Microsoft Office, Microsoft PowerPoint, and Microsoft Word are trademarks of the Microsoft group of companies.
{: note}

### Open Office file formats
{: #supported-file-formats-open-office}

Table 2 lists the Open Office file formats that the service supports for translation.

| File format | File extension | Content type |
|-------------|----------------|--------------|
| Open Office Calc | `.ods` | `application/vnd.oasis.opendocument.spreadsheet` |
| Open Office Impress | `.odp` | `application/vnd.oasis.opendocument.presentation` |
| Open Office Writer | `.odt` | `application/vnd.oasis.opendocument.text` |
{: caption="Table 2. Open Office file formats"}

### Subtitle file formats
{: #supported-file-formats-subtitles}

Table 3 lists the subtitle (or caption) formats that service supports for translation. These textual formats contain the transcript of a sound track or video source. The formats provide plain text that is intuitively comprehensible with minimal syntax. They include a list of cues that contain synchronization information for the media source. They can also include metadata that is not intended for display.

The table shows both the file extension and the content type for all subtitle formats. However, in some cases you must specify one or the other. The table makes clear where the file extension or the content type is needed. Also, for the `.sub` file extension, which is used for multiple formats, the service parses the file to determine the exact subtitle format of the file.

| File format | File extension | Content type |
|-------------|----------------|--------------|
| Apple® iTunes® Timed Text | `.itt`  \n The file extension is required | `application/xml` |
| DirectVobSub | `.sub`  \n The file extension is required | `text/plain` |
| Distribution Format Exchange Profile | `.dxfp`  \n The file extension is sufficient | `application/ttaf+xml` |
| | `.xml` | `application/ttaf+xml`  \n The content type is required |
| MicroDVD | `.sub`  \n The file extension is required | `text/plain` |
| Source Code Control | `.scc`  \n The file extension is required | `application/octet-stream` |
| SubRip | `.srt` | `text/srt` |
| SubStation Alpha | `.ssa`  \n The file extension is required | `text/plain` |
| SubViewer | `.sbv` | `text/sbv` |
| Synchronized Accessible Media Interchange | `.sami`  \n The file extension is required | `application/xml` |
|  | `.smi`  \n The file extension is required | `application/xml` |
| Time Text Markup Language | `.ttml` | `application/ttml+xml` |
| VSFilter | `.sub`  \n The file extension is required | `text/plain` |
| WebVTT | `.vtt` | `text/vtt` |
{: caption="Table 3. Subtitle file formats"}

The following information qualifies some of the nuances of subtitle translation:

-   *Character encoding* - Subtitles can be presented in different character sets. The service supports only UTF-8 input and produces only UTF-8 output. The results maintain the line separation and optional Byte Order Mark (BOM) from the original source.
-   *Markup* - The service attempts to preserve markup in the translated document, but preservation is not guaranteed. The service can silently remove markup from a particular cue.
-   *Names* - By convention, speaker names can be marked with `-..:`, parentheses, or both. The service extracts and translates speaker names separately to guarantee consistent translation.
-   *Paragraphs* - The text to be translated is grouped into paragraphs. Each paragraph can span multiple cues, but it always consists of a full set of cue lines. In other words, each paragraph consists of one or more cues in their entirety, with each cue contained fully in a single paragraph.

    A single cue can contain one or more lines of text (for example, two short sentences). The service creates paragraph breaks only at cue line boundaries to preserve the count of lines in the cue. For languages with punctuation, a paragraph generally maps to a complete sentence. For languages without punctuation, a paragraph can contain multiple sentences, which can adversely affect the distribution of lines into cues in the translated document.
-   *Comments, notes, and titles* - For formats that permit these elements, the service preserves the original text and adds translation that is prefixed by language code. Because this information is intended for use by the author, the service maintains the text in both its original and translated forms.

### Other file formats
{: #supported-file-formats-other}

Table 4 lists all other file formats that the service supports for translation.

| File format | File extension | Content type |
|-------------|----------------|--------------|
| Adobe® Portable Document Format [**1**] | `pdf` | `application/pdf` |
| Extensible Markup Language | `.xml` | `text/xml` |
| HyperText Markup Language | `.htm` | `text/html` |
| | `.html` | `text/html` |
| | `.xhtml` | `text/html` |
| JavaScript Object Notation [**2**] | `.json` | `text/json` |
| Plain text | `.txt` | `text/plain` |
| Rich Text Format | `.rtf` | `application/rtf` |
{: caption="Table 4. Other file formats"}

**Notes:**

1.  For PDF files, translation is experimental functionality. The quality of PDF translation is still largely an alpha release. The translation works best for single-column PDF documents that do not include many tables or images.
2.  For JSON files, values with type `string` or `string array` are translated.

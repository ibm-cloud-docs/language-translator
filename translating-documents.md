---

copyright:
  years: 2015, 2020
lastupdated: "2020-05-22"

subcollection: language-translator

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Translating documents (Beta)
{: #document-translator-tutorial}

Translate files from one language to another while preserving the original format. More than 12 different file formats can be translated, including MS Office, Open Office, and PDF.
{:shortdesc}

## Before you begin
{: #prerequisites}

- [Get started](/docs/language-translator?topic=language-translator-gettingstarted) with {{site.data.keyword.languagetranslatorshort}}. You will need your {{site.data.keyword.languagetranslatorshort}} service credentials (`apikey` and `url`).
- Make sure the document you want to translate meets the following requirements:
    - Maximum file size: 
      - **20 MB** for service instances on Standard, Advanced, and Premium plans
      - **2 MB** for service instances on the Lite plan
    - [Supported file formats](#supported-file-formats)
    - [Supported translation models](/docs/language-translator?topic=language-translator-translation-models)

## Step 1: Submit a document to translate
{: #submit-document-to-translate}

The following example request submits an example file *curriculum.pdf* to the service and translates it from English to French. Replace `{apikey}` and `{url}` with your service credentials, and replace `curriculum.pdf` with a relative path to your file.

Example request:
```sh
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
"{url}/v3/documents?version=2018-05-01"
```
{: pre}

Windows users: Replace the backslash (`\`) at the end of each line with a caret (`^`). Make sure that there are no trailing spaces.
{: tip}

To translate a document with a [custom model](/docs/language-translator?topic=language-translator-customizing), use the **model_id** parameter. The following request translates the document with the custom model identified by the model ID `96221b69-8e46-42e4-a3c1-808e17c787ca`.

Example request:
```sh
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
"{url}/v3/documents?version=2018-05-01"
```
{: pre}

A successful request will return a `document_id` in the response.

Example response:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
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

After you have submitted a document for translation, you can check the translation status to find out when the translated document is available to download. The following example request checks the translation status of the document with document ID  `bae02796-0d28-435c-9115-888359fdde62`.

Example request:
```sh
curl -X GET \
--user "apikey:{apikey}" \
"{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01"
```
{: pre}

Example response:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "available",
  "created": "2018-10-11T03:31:25",
  "completed": "2018-10-11T03:31:38"
}
```
{: codeblock}

When the `status` in the response is `available`, the translated document is ready to download.

## Step 3: Download the translated document
{: #download-translated-document}

The following example request saves the translated document with document ID `bae02796-0d28-435c-9115-888359fdde62` to the file *curriculum-fr.pdf*.

Example request:
```sh
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
"{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01"
```
{: pre}

## Step 4: Translate a previously submitted document
{: #translate-document-by-reference}

The following example request references the original English *curriculum.pdf* file with the `document_id` `bae02796-0d28-435c-9115-888359fdde62` and translates it to Portuguese.

Example request:
```sh
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
"{url}/v3/documents?version=2018-05-01"
```
{: pre}

Example response:
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

The response contains a new `document_id`. Repeat steps two and three with your new `document_id` to check the status of the translation, and to download the translated file once it is available.

## Step 5: Delete documents
{: #delete-documents}

Original documents and any associated translated documents are deleted automatically after they have not been used for a certain period of time. See [Information security](/docs/language-translator?topic=language-translator-information-security) for more details.
{: tip}

To delete documents manually, use the **Delete document** method. In this tutorial, the English *curriculum.pdf* file was involved with two translations, so two requests are required to delete all copies of the original document.

Delete the original submission of *curriculum.pdf* and the French translation:
```sh
curl -X DELETE \
--user "apikey:{apikey}" \
"{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01"
```
{: pre}

Delete the duplicate of the original *curriculum.pdf* file and the Portuguese translation:
```sh
curl -X DELETE \
--user "apikey:{apikey}" \
"{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01"
```
{: pre}

## Supported file formats
{: #supported-file-formats}

- Microsoft Office
    - Word: `.doc`, `.docx`
    - PowerPoint: `.ppt`, `.pptx`
    - Excel: `.xls`, `.xlsx`
    - Rich Text Format: `.rtf`
- Open Office
    - Writer: `.odt`
    - Impress: `.odp`
    - Calc: `.ods`
- Other formats
    - PDF: `.pdf`
    - HTML: `.htm`, `.html`
    - XML: `.xml`
    - JSON: `.json` (values with type `string` or `string array` are translated)
    - Text: `.txt`

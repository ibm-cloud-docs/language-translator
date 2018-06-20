---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-20"

---
<!-- Attribute definitions -->
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Using the Document Translator
{: #doc-translator-tutorial}

The {{site.data.keyword.ibmwatson}} Document Translator allows you to translate documents from one language to another while it preserves the formatting in the file. Translate 12 different file formats, including MS Office, Open Office, and PDF files. In this tutorial, you learn how to translate a document with the tool.
{:shortdesc}

## Before you begin
{: #prerequisites}

You need either your {{site.data.keyword.languagetranslatorshort}} service credentials or your {{site.data.keyword.Bluemix_notm}} account credentials to log into the Document Translator.

To find out which authentication to use, view the service credentials by clicking the service instance on the [Dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/dashboard/apps?watson){: new_window}.

## Step 1: Log into Document Translator

1.  Go to [Document Translator ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/doc-translator){: new_window}.
1.  Use the service credentials that you found earlier. To log in with an API key, enter `apikey` as the username and the value of the key as the password. Click **Login**.

## Step 2: Send a document for translation

1.  Select **Browse**, and locate a document on your system to translate. The maximum file size in this preview release is 100 MB. Document Translator supports the following file types:
    -  Microsoft Office
        - Word (.doc, .docx)
        - PowerPoint (.ppt, .pptx)
        - Excel (.xls, .xlsx)
        - Rich Text Format (.rtf)
    - Open Office
        - Writer (.odt)
        - Impress (.odp)
        - Calc (.ods)
    - Other supported file types
        - PDF (.pdf). Translated files are returned as both .docx and .pdf files.
        - HTML (.htm, .html)
        - XML (.xml)
        - JSON (.json). All values of type `string` and `string array` are translated.
        - TEXT (.txt)

1.  Choose the language of the document in **From** and then select a target language in **To**.
1.  Click **Translate**.

## Step 3: Review your translated document

1.  Select *Show Documents List* to see the status of documents you translated. The translation status follows this sequence:
    1.  Initial
    1.  Extracted
    1.  Segmented
    1.  Translated
    1.  Inserted
    1.  Done

1.  When the translation status is `Done`, select **Get** to download the translated document. Or select **Del** to delete the document.

## Next steps

Experiment with other source and target languages.

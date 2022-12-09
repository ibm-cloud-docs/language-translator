---

copyright:
  years: 2015, 2022
lastupdated: "2022-12-09"

keywords: language translator,getting started,translate,identify language,translate document,translation

subcollection: language-translator

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with {{site.data.keyword.languagetranslatorshort}}
{: #gettingstarted}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

{{site.data.keyword.languagetranslatorfull}} allows you to translate text programmatically from one language into another language.  This tutorial walks you through the commands to translate text from English to Spanish, and to identify the language of a text sample.
{: shortdesc}

The tutorial uses the `curl` command-line utility to demonstrate REST API calls. For more information about `curl`, see [Using curl with Watson examples](/docs/watson?topic=watson-using-curl).
{: note}

## Before you begin
{: #prerequisites}

- Create an instance of the service: {: hide-dashboard}
    1.  Go to the [{{site.data.keyword.languagetranslatorshort}}](https://{DomainName}/catalog/language-translator){: external} page in the {{site.data.keyword.cloud_notm}} catalog.
    1.  Sign up for a free {{site.data.keyword.cloud_notm}} account or log in.
    1.  Read and agree to the terms of the license agreement.
    1.  Click **Create**.
- Copy the credentials to authenticate to your service instance: {: hide-dashboard}
    1.  View the **Manage** page for the service instance:

        -   If you are on the **Getting started** page for your service instance, click the **Manage** entry in the list of topics.
        -   If you are on the **Resource list** page, expand the **AI / Machine Learning** grouping in the **Name** column, and click the name of your service instance.

    1.  On the **Manage** page, click **Show Credentials** in the **Credentials** box.
    1.  Copy the `API Key` and `URL` values for the service instance.

This tutorial uses an API key to authenticate. In production, use an IAM token. For more information see [Authenticating to IBM Cloud](/docs/watson?topic=watson-iam#gs-credential-cloud).
{: tip}

## Translate text
{: #translate-text}
{: step}

Use the following example to translate two phrases, "Hello, world" and "How are you?" from English to Spanish.

-   In the command, `model_id` identifies the model to be used for translation, in this case `en-es`.
-   Replace `{apikey}` and `{url}` with your service credentials. {: hide-dashboard}

```sh
curl -X POST --user "apikey:{apikey}" \
--header "Content-Type: application/json" \
--data '{"text": ["Hello, world.", "How are you?"], "model_id":"en-es"}' \
"{url}/v3/translate?version=2018-05-01"
```
{: pre}

The `/v3/translate` method accepts a maximum of 50 KB of input text encoded in UTF-8 format for translation.
{: note}

## Identify language
{: #identify-language}
{: step}

Use the following example to identify the language of text.

-   Replace `{apikey}` and `{url}` with your service credentials. {: hide-dashboard}

```sh
curl -X POST --user "apikey:{apikey}" \
--header "Content-Type: text/plain" \
--data "Language Translator translates text from one language to another" \
"{url}/v3/identify?version=2018-05-01"
```
{: pre}

## Translate a document
{: #translate-a-document}
{: step}

{{site.data.keyword.languagetranslatorshort}} allows you to translate documents, such as markup files that use XML or HTML, or Microsoft Office and Open Office files, while retaining the original formatting. For a tutorial, check out [Translating documents](/docs/language-translator?topic=language-translator-document-translator-tutorial).

## Next steps
{: #next-steps}

- Learn how to [customize](/docs/language-translator?topic=language-translator-customizing) {{site.data.keyword.languagetranslatorshort}} to work for your use case
- View the [API & SDK reference](https://{DomainName}/apidocs/language-translator)
- Explore [sample applications](/docs/language-translator?topic=language-translator-sample-apps)
- View language support information:
    - [Supported languages for translation](/docs/language-translator?topic=language-translator-translation-models)
    - [Identifiable languages](/docs/language-translator?topic=language-translator-identifiable-languages)

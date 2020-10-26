---

copyright:
  years: 2015, 2020
lastupdated: "2020-10-24"

keywords: language translator,getting started,translate,identify language,translate document,translation

subcollection: language-translator

content-type: tutorial
account-plan: lite
completion-time: 10m

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:step: data-tutorial-type='step'}

# Getting started with {{site.data.keyword.languagetranslatorshort}}
{: #gettingstarted}
{: toc-content-type="tutorial"}
{: toc-completion-time="10m"}

{{site.data.keyword.languagetranslatorfull}} allows you to translate text programmatically from one language into another language.
{:shortdesc}
{: hide-dashboard}

This tutorial walks you through the commands to translate text from English to Spanish, and to identify the language of a text sample.

## Before you begin
{: #prerequisites}

- {: hide-dashboard} Create an instance of the service:
    1.  Go to the [{{site.data.keyword.languagetranslatorshort}}](https://{DomainName}/catalog/language-translator){: external} page in the {{site.data.keyword.cloud_notm}} catalog.
    1.  Sign up for a free {{site.data.keyword.cloud_notm}} account or log in.
    1.  Click **Create**.
- {: hide-dashboard} Copy the credentials to authenticate to your service instance:
    1.  On the **Manage** page, click **Show Credentials**.
    1.  Copy the `API Key` and `URL` values.

This tutorial uses an API key to authenticate. In production, use an IAM token. For more information see [Authenticating to Watson services](/docs/watson?topic=watson-iam).
{: tip}

### Using the curl examples
{: #getting-started-curl}

This tutorial uses the `curl` command to call methods of the service's HTTP interface. Make sure that you have the `curl` command installed on your system.

1.  To test whether `curl` is installed, run the following command on the command line. If the output lists the `curl` version that supports Secure Sockets Layer (SSL), you are set for the tutorial.

    ```bash
    curl -V
    ```
    {: pre}

1.  If necessary, install the version of `curl` with SSL enabled for your operating system from [curl.haxx.se](https://curl.haxx.se/){: external}.

Omit the braces (`{ }`) from the examples. They indicate variable values.
{: tip}

## Translate text
{: #translate-text}
{: step}

Use the following example to translate two phrases, "Hello, world" and "How are you?" from English to Spanish. <span class="hide-dashboard">Replace `{apikey}` and `{url}` with your service credentials.</span> In the command, `model_id` identifies the model to be used for translation, in this case `en-es`.

```sh
curl -X POST --user "apikey:{apikey}"{: apikey} \
--header "Content-Type: application/json" \
--data '{"text": ["Hello, world.", "How are you?"], "model_id":"en-es"}' \
"{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

The `/v3/translate` method accepts a maximum of 50 KB of input text encoded in UTF-8 format for translation.
{: note}

## Identify language
{: #identify-language}
{: step}

Use the following example to identify the language of text. <span class="hide-dashboard">Replace `{apikey}` and `{url}` with your service credentials.</span>

```sh
curl -X POST --user "apikey:{apikey}"{: apikey} \
--header "Content-Type: text/plain" \
--data "Language Translator translates text from one language to another" \
"{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## Translate a document (Beta)
{: #translate-a-document}
{: step}

{{site.data.keyword.languagetranslatorshort}} allows you to translate documents, such as markup files that use XML or HTML, or Microsoft Office and Open Office files, while retaining the original formatting. For a tutorial, check out [Translating documents (Beta)](/docs/language-translator?topic=language-translator-document-translator-tutorial).

## Next steps
{: #next-steps}

- Learn how to [customize](/docs/language-translator?topic=language-translator-customizing) {{site.data.keyword.languagetranslatorshort}} to work for your use case
- View the [API & SDK reference](https://{DomainName}/apidocs/language-translator)
- Explore [sample applications](/docs/language-translator?topic=language-translator-sample-apps)
- View language support information:
    - [Supported languages for translation](/docs/language-translator?topic=language-translator-translation-models)
    - [Identifiable languages](/docs/language-translator?topic=language-translator-identifiable-languages)

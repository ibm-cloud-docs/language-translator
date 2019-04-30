---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-04"

---
<!-- Attribute definitions -->
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
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
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Getting started tutorial
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} allows you to translate text programmatically from one language into another language.
{:shortdesc}
{: hide-dashboard}

This tutorial walks you through the commands to translate text from English to Spanish, and to identify the language of a text sample.

## Before you begin
{: #prerequisites}

- {: hide-dashboard} Create an instance of the service:
    1.  {: hide-dashboard} Go to the [{{site.data.keyword.languagetranslatorshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/catalog/services/language-translator){: new_window} page in the {{site.data.keyword.Bluemix_notm}} Catalog.
    2.  Sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
    3.  Click **Create**.
- Copy the credentials to authenticate to your service instance:
    1.  On the **Manage** page, click **Show** to view your credentials.
    2.  Copy the `API Key` and `URL` values.
- Make sure that you have the `curl` command:
    - The examples use `curl` command to call methods of the HTTP interface. Install the version for your operating system from [curl.haxx.se ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://curl.haxx.se/){: new_window}. Install the version that supports the Secure Sockets Layer (SSL) protocol. Make sure to include the installed binary file on your `PATH` environment variable.

This tutorial uses an API key to authenticate. For production uses, make sure that you review the API key [best practices](/docs/services/watson/apikey-bp.html#api-bp).
{: tip}

## Step 1: Translate text
{: #translate-text}

Use the following example to translate two phrases, "Hello, world!" and "How are you?" from English to Spanish. <span class="hide-dashboard">Replace `{apikey}` and `{url}` with your service credentials.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## Step 2: Identify language
{: #identify-language}

Use the following example to identify the language of text. <span class="hide-dashboard">Replace `{apikey}` and `{url}` with your service credentials.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## Next steps
{: #next-steps}

- Learn how to [customize](/docs/services/language-translator?topic=language-translator-customizing) {{site.data.keyword.languagetranslatorshort}} to work for your use case
- Try [translating documents (Beta)](/docs/services/language-translator?topic=language-translator-translating-documents)
- View the [API reference](https://{DomainName}/apidocs/language-translator)
- Explore [sample applications](/docs/services/language-translator?topic=language-translator-sample-applications)
- View language support information:
    - [Translation models](/docs/services/language-translator?topic=language-translator-translation-models)
    - [Identifiable languages](/docs/services/language-translator?topic=language-translator-identifiable-languages)

---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-15"

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

# Getting started tutorial
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} allows you to translate text programmatically from one language into another language. This tutorial walks you through the commands to translate text from English to Spanish, and to identify the language of a text sample.
{:shortdesc}

## Before you begin
{: #prerequisites}

- {: download} If you're seeing this, you created your service instance. Now get your credentials.
- Create an instance of the service:
    1.  Go to the [{{site.data.keyword.languagetranslatorshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/catalog/services/language-translator){: new_window} page in the {{site.data.keyword.Bluemix_notm}} Catalog.
    1.  Sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
    1.  Select a service plan, e.g. select the free lite plan for testing the service.
    1.  Click **Create**.
- Copy the credentials to authenticate to your service instance:
    1.  On the service dashboard, click the **Service credentials** tab.
    1.  Click **View credentials** under **Actions**.
    2.  Copy the `apikey`, and `url` values.
    
    With some service instances, you authenticate by providing a username and password. If you see `username` and `password` in the credentials, use those values instead of `apikey` and `{apikey_value}` in the examples in this tutorial.

- Make sure you have cURL:
    - The examples use cURL to call methods of the HTTP interface. Install the version for your operating system from [curl.haxx.se ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://curl.haxx.se/){: new_window}. Install the version that supports the Secure Sockets Layer (SSL) protocol. Make sure to include the installed binary file on your `PATH` environment variable.

This tutorial uses an API key to authenticate. For production uses, make sure that you review the API key [best practices](/docs/services/watson/apikey-bp.html#api-bp).
{: tip}

## Step 1: Translate text
{: #translate-text}

Use the following example to translate two phrases, "Hello, world!" and "How are you?", from English to Spanish. Replace `{apikey_value}` with the API key that you copied in the previous step.

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world!\", \"How are you?\"], \"model_id\":\"en-es\"}" https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}

The host in the example URL is `gateway.watsonplatform.net`. Your host might be different depending on your {{site.data.keyword.cloud_notm}} region or dedicated deployment. You can view the URL for your service instance from the **Service credentials** tab in your service dashboard. 
{: tip}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  version: 'v2',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
});
language_translator.translate({
    text: 'Hello, world!',
    source: 'en',
    target: 'es'
  },
  function(err, translation) {
    if (err)
      console.log(err)
    else
      console.log(translation);
});
```
{:node}
{:codeblock} -->

<!-- ```java
LanguageTranslator service = new LanguageTranslator();
service.setUsernameAndPassword("username","password");

TranslationResult result = service.translate("Hello, world!", "en", "es");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
    username="username",
    password="password")

translation = language_translator.translate(
    text="Hello, world!",
    source="en",
    target="es"
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->

## Step 2: Identify language

Use the following example to identify the language of text. Replace `{apikey_value}` with the API key that you copied in the previous step.

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" https://gateway.watsonplatform.net/language-translator/api/v3/identify?version=2018-05-01
```
{: pre}


## Next steps
{: #next-steps}

- Learn how to [customize](/docs/services/language-translator/customizing.html) {{site.data.keyword.languagetranslatorshort}} to work for your use case.
- View the [API reference](https://www.ibm.com/watson/developercloud/language-translator/api/v3/).
- Interact with the API in the [API Explorer](https://watson-api-explorer.mybluemix.net/apis/language-translator-v3).
- Explore [sample applications](sample-applications.html).
- View language support information:
  - [Translation models](translation-models.html)
  - [Identifiable languages](identifiable-languages.html)

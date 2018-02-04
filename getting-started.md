---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-23"

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

{{site.data.keyword.languagetranslatorfull}} allows you to programmatically translate text in news, conversational, and patent domains. This tutorial walks you through the commands to translate some sample content from English to Spanish and to choose the domain.
{:shortdesc}

## Before you begin
{: #prerequisites}

- Create an instance of the service:
    - {: download} If you're seeing this, you created your service instance. Now get your credentials.
    - Create a project from a service:
        1.  Go to the {{site.data.keyword.watson}} Developer Console [Services ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/developer/watson/services){: new_window} page.
        1.  Select {{site.data.keyword.languagetranslatorshort}}, click **Add Services**, and either sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
        1.  Type `language-tutorial` as the project name and click **Create Project**.
- Copy the credentials to authenticate to your service instance:
    - {: download} From the service dashboard (what you're looking at):
        1.  Click the **Service credentials** tab.
        1.  Click **View credentials** under **Actions**.
        1.  Copy the `username`, `password`, and `url` values.
        {: download}
    - From your **language-tutorial** project in the Developer Console, copy the `username`,  `password`, and `url` values for `"language_translator"` from the  **Credentials** section.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

If you use {{site.data.keyword.Bluemix_dedicated_notm}}, create your service instance from the [{{site.data.keyword.languagetranslatorshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/catalog/services/language-translator/){: new_window} page in the Catalog. For details about how to find your service credentials, see [Service credentials for Watson services ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Step 1: Translate text
{: #translate-text}

Use the following example to translate "Hello, world!" from English to Spanish. Replace `{username}` and `{password}` with the service credentials you copied in the previous step.

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-d '{"text":"Hello, world", "source":"en", "target":"es"}' \
https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{:codeblock}

A preview of new Neural Machine Translation models that offer improved translations is now available. For more details, see the [release notes](release-notes.html#12-january-2018).

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


## Step 2: Try a domain-specific model
{: #specify-model}

{{site.data.keyword.languagetranslatorshort}} has specialized models for news, conversational, and patent domains. When you specify `source` and `target` languages as in Step 2, the service usually defaults to the news domain model for that translation path. To use a domain-specific model, specify the `model_id` instead of the `source` and `target` languages. You can also use a [custom model](https://www.ibm.com/watson/developercloud/doc/language-translator/customizing.html){: new_window} if you created one.

The following example translates "Hey world, whats up?" with the English-to-Spanish conversational model. Replace `{username}` and `{password}` with your information:

```bash
curl -X POST --user {username}:{password} --header "Content-Type: application/json" --header "Accept: application/json" --data "{\"text\":\"Hey world, whats up?\",\"model_id\":\"en-es-conversational\"}" "https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{:codeblock}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
  version: 'v2',
});
language_translator.translate({
    text: 'Hey, world! What's up?',
    model_id: 'en-es-conversational'
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

TranslationResult result = service.translate("Hey, world! What's up?", "en-es-conversational");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```python
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
  username="username",
  password="password"
)

translation = language_translator.translate(
  text="Hey, world! What's up?",
  model_id="en-es-conversational"
)
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->

You can use the [List models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models){: new_window} method to view the available models for your service instance.
{:tip}

## Next steps
{: #next-steps}

- Learn how to [customize](/docs/services/language-translator/customizing.html) {{site.data.keyword.languagetranslatorshort}} to work for your use case.
- View the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){:new_window}.
- Interact with the API in the [API explorer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){:new_window}.
- Try the [Node.js sample app ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/language-translator-nodejs){:new_window}.

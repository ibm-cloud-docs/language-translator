---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

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

# Einführung - Lernprogramm
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} ermöglicht die programmgestützte Übersetzung von Text in den Domänen 'News', 'Dialog' und 'Patent'. Anhand dieses Lernprogramms können Sie die Befehle zur Übersetzung von Beispielinhalten aus der englischen in die spanische Sprache und zur Auswahl der Domäne schrittweise durcharbeiten.
{:shortdesc}

## Vorbereitungen
{: #prerequisites}

- Eine Instanz des Service erstellen:
    - {: download} Wenn Sie diese Anzeige sehen, haben Sie die Serviceinstanz erstellt. Jetzt können Sie die Berechtigungsnachweise abrufen.
    - Ein Projekt auf der Basis eines Service erstellen:
        1.  Rufen Sie die Seite [Services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/developer/watson/services){: new_window} der {{site.data.keyword.watson}}-Entwicklerkonsole auf.
        1.  Wählen Sie {{site.data.keyword.languagetranslatorshort}} aus, klicken Sie auf **Services hinzufügen** und melden Sie sich entweder an oder fordern Sie ein kostenfreies {{site.data.keyword.Bluemix_notm}}-Konto an.
        1.  Geben Sie `language-tutorial` als Projektnamen an und klicken Sie auf **Projekt erstellen**.
- Berechtigungsnachweise für die Authentifizierung bei der Serviceinstanz kopieren:
    - {: download} Führen Sie im Service-Dashboard (aktuelle Anzeige) die folgenden Schritte aus:
        1.  Klicken Sie auf die Registerkarte **Serviceberechtigungsnachweise**.
        1.  Klicken Sie auf **Berechtigungsnachweise anzeigen** unter **Aktionen**.
        1.  Kopieren Sie die Werte für `username`, `password` und `url`.
        {: download}
    - Kopieren Sie im Projekt **language-tutorial** in der Entwicklerkonsole die Werte von `username`, `password` und `url` für `"language_translator"` im Abschnitt **Berechtigungsnachweise**.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Wenn Sie {{site.data.keyword.Bluemix_dedicated_notm}} verwenden, erstellen Sie die Serviceinstanz über die Seite von [{{site.data.keyword.languagetranslatorshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/catalog/services/language-translator/){: new_window} im Katalog. Details zum Abrufen der Serviceberechtigungsnachweise finden Sie in [Serviceberechtigungsnachweise für Watson-Services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Schritt 1: Text übersetzen
{: #translate-text}

Mit dem folgenden Beispiel wird der Text "Hello, world!" aus der englischen Sprache in die spanische Sprache übersetzt. Ersetzen Sie `{username}` und `{password}` durch die Serviceberechtigungsnachweise, die Sie im vorherigen Schritt kopiert haben.

```bash
curl -X POST --user {username}:{password} --header "Accept: application/json" --data "{\"text\":\"Hello, world\",\"source\":\"en\",\"target\":\"es\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{:codeblock}

Eine Vorschau neuer NMT-Modelle (Neural Machine Translation) für noch bessere Übersetzungen ist nun verfügbar. Weitere Details finden Sie in den [Releaseinformationen](release-notes.html#12-january-2018).
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


## Schritt 2: Domänenspezifisches Modell testen
{: #specify-model}

{{site.data.keyword.languagetranslatorshort}} enthält spezialisierte Modelle für die Domänen 'News', 'Dialog' und 'Patent'. Wenn Sie die Quellensprache (`source`) und die Zielsprache (`target`) wie in Schritt 2 beschrieben angeben, verwendet der Service normalerweise standardmäßig das Domänenmodell 'News' für diesen Übersetzungspfad. Wenn Sie ein domänenspezifisches Modell verwenden möchten, geben Sie anstelle der Quellensprache (`source`) und der Zielsprache (`target`) die Modell-ID (`model_id`) an. Sie können auch ein [angepasstes Modell](customizing.html) verwenden, falls ein solches erstellt wurde.

_Domänenspezifische Modelle werden in Anforderungen, die den [NMT-Vorschauheader](release-notes.html#12-january-2018) enthalten, nicht unterstützt._

Im folgenden Beispiel wird der Text "Hey world, whats up?" mit dem Dialogmodell für die Übersetzung aus dem Englischen ins Spanische übersetzt. Ersetzen Sie `{username}` und `{password}` durch Ihre eigenen Informationen.

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

Mit der Methode zum [Auflisten von Modellen![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models){: new_window} können Sie die verfügbaren Modelle für Ihre Serviceinstanz anzeigen.
{:tip}

## Weitere Schritte
{: #next-steps}

- {{site.data.keyword.languagetranslatorshort}} zur Verwendung für einen eigenen Anwendungsfall [anpassen](/docs/services/language-translator/customizing.html).
- [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){:new_window} anzeigen.
- Mit der API im [API-Explorer ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){:new_window} interagieren.
- [Node.js-Beispiel-App ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/watson-developer-cloud/language-translator-nodejs){:new_window} testen.

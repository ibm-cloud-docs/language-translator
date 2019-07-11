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

# Einführung - Lernprogramm
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} ermöglicht die programmgestützte Übersetzung von Text aus einer Sprache in eine andere.
{:shortdesc}
{: hide-dashboard}

Anhand dieses Lernprogramms können Sie die Befehle zur Übersetzung von Text aus der englischen in die spanische Sprache und zur Erkennung der Sprache eines Textbeispiels durcharbeiten.

## Vorbereitungen
{: #prerequisites}

- {: hide-dashboard} Eine Instanz des Service erstellen:
    1.  {: hide-dashboard} Rufen Sie die Seite von [{{site.data.keyword.languagetranslatorshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/catalog/services/language-translator){: new_window} im Katalog von {{site.data.keyword.Bluemix_notm}} auf.
    2.  Melden Sie sich entweder an oder fordern Sie ein kostenfreies {{site.data.keyword.Bluemix_notm}}-Konto an.
    3.  Klicken Sie auf **Erstellen**.
- Berechtigungsnachweise für die Authentifizierung bei der Serviceinstanz kopieren:
    1.  Klicken Sie auf der Seite **Verwalten** auf **Anzeigen**, um Ihre Berechtigungsnachweise anzuzeigen.
    2.  Kopieren Sie die Werte für `API-Schlüssel` und `URL`.
- Stellen Sie sicher, dass der Befehl `curl` zur Verfügung steht:
    - In den Beispielen wird der Befehl `curl` verwendet, um Methoden der HTTP-Schnittstelle aufzurufen. Installieren Sie die Version für Ihr Betriebssystem von [curl.haxx.se ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://curl.haxx.se/){: new_window}. Installieren Sie die Version, die das SSL-Protokoll (SSL = Secure Sockets Layer) unterstützt. Geben Sie die installierte Binärdatei in der Umgebungsvariablen `PATH` an.

Dieses Lernprogramm verwendet einen API-Schlüssel für die Authentifizierung. Machen Sie sich für den Produktionseinsatz mit den [bewährten Verfahren](/docs/services/watson/apikey-bp.html#api-bp) für API-Schlüssel vertraut.
{: tip}

## Schritt 1: Text übersetzen
{: #translate-text}

Mit dem folgenden Beispiel werden die Texte "Hello, world!" und "How are you?" aus der englischen Sprache in die spanische Sprache übersetzt. <span class="hide-dashboard">Ersetzen Sie `{apikey}` und `{url}` durch Ihre Serviceberechtigungsnachweise.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## Schritt 2: Sprache erkennen
{: #identify-language}

Verwenden Sie das folgende Beispiel, um die Sprache des Texts zu ermitteln. <span class="hide-dashboard">Ersetzen Sie `{apikey}` und `{url}` durch Ihre Serviceberechtigungsnachweise.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## Weitere Schritte
{: #next-steps}

- {{site.data.keyword.languagetranslatorshort}} zur Verwendung für einen eigenen Anwendungsfall [anpassen](/docs/services/language-translator?topic=language-translator-customizing)
- [Dokumente übersetzen (Beta)](/docs/services/language-translator?topic=language-translator-document-translator-tutorial)
- [API-Referenz](https://{DomainName}/apidocs/language-translator) anzeigen
- [Beispielanwendungen](/docs/services/language-translator?topic=language-translator-sample-applications) erkunden
- Sprachunterstützungsinformationen:
    - [Übersetzungsmodelle](/docs/services/language-translator?topic=language-translator-translation-models)
    - [Sprachen, für die eine Erkennung möglich ist](/docs/services/language-translator?topic=language-translator-identifiable-languages)

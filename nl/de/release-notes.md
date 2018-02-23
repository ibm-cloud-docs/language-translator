---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Releaseinformationen

Die folgenden neuen Features und Änderungen sind für den Service verfügbar.
{: shortdesc}

## 12. Januar 2018
{: #12-january-2018}

Eine Vorschau neuer NMT-Modelle (Neural Machine Translation) ist nun verfügbar. Sie können NMT-Modelle für die nachfolgend aufgeführten Sprachkombinationen testen. 

- Englisch als Quellen- und Zielsprache für Arabisch, Chinesisch, Niederländisch, Französisch, Deutsch, Italienisch, Japanisch, Koreanisch, Polnisch, Portugiesisch (Brasilien), Russisch, Spanisch und Türkisch.
- Französisch als Quellen- und Zielsprache für Deutsch und Spanisch.
- Deutsch als Quellen- und Zielsprache für Italienisch.

*Die NMT-Modelle und die Syntax für ihre Verwendung werden während des Vorschauzeitraums möglicherweise geändert. Zum gegenwärtigen Zeitpunkt unterstützen NMT-Modelle keine Korpusanpassung. Nur die Anpassung von Vorgabewörterbüchern wird unterstützt.*

Wenn Sie ein NMT-Vorschaumodell für die Übersetzung verwenden möchten, geben Sie den Header `X-Watson-Technology-Preview:2017-07-01` zusammen mit den Zeichencodes für die Quellen- und die Zielsprache des gewünschten Modells an. Das folgende Beispiel veranschaulicht die Übersetzung von Text aus der englischen in die spanische Sprache mit einem NMT-Vorschaumodell.

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}


## 15. Dezember 2016
{: #15-december-2016}

Es stehen zusätzliche Übersetzungsmodelle für die Domäne 'News' zur Verfügung: Englisch als Quellen- und Zielsprache für Japanisch.

## 15. November 2016
{: #15-november-2016}

Die Tools, die zuvor für den {{site.data.keyword.languagetranslatorshort}}-Service verfügbar waren, stehen nicht mehr zur Verfügung bzw. werden nicht mehr unterstützt. 

Wenden Sie sich an den Vertriebsbeauftragten oder an die Kundenunterstützung, um Informationen zur Verwendung der {{site.data.keyword.languagetranslatorshort}}-API für die Ausführung der vom {{site.data.keyword.languagetranslatorshort}}-Tool unterstützten Tasks zu erhalten.

## 01. September 2016
{: #1-september-2016}

Der IBM Watson&trade; Language Translation-Service wurde in {{site.data.keyword.languagetranslatorshort}}-Service umbenannt.

## 22. März 2016
{: #22-march-2016}

Es steht Unterstützung für zusätzliche Sprachen zur Verfügung: Englisch als Quellen- und Zielsprache für Italienisch; Spanisch als Quellen- und Zielsprache für Französisch.

## 03. Dezember 2015
{: #3-december-2015}

Ab 15. Januar 2016 werden alle Anpassungsfunktionen im Rahmen des Standardplans nicht weiter unterstützt. Für Anwendungen, die keine Anpassungsfunktionen nutzen, ist keine Änderung erforderlich, da der Standardplan für alle API-Aufrufe, die nicht in Zusammenhang mit Anpassungen oder angepassten Modellen stehen, aktiv bleibt. Wenn Sie die GA-Anpassungsfunktionen (Plan mit Trainingsfunktionen) des {{site.data.keyword.languagetranslatorshort}}-Service mit einer {{site.data.keyword.cloud}}-Anwendung nutzen möchten, die eine frühere Instanz des Service verwendet, führen Sie die folgenden Schritte aus:

1.  Erstellen Sie eine neue Watson {{site.data.keyword.languagetranslatorshort}}-Instanz und geben Sie den GA-Plan mit Trainingsfunktionen an.
1.  Erstellen Sie eine Bindung von der neuen Serviceinstanz mit Trainingsfunktionen zu Ihrer App in {{site.data.keyword.cloud_notm}}.
1.  Stellen Sie die Daten zusammen, die für die ursprüngliche Erstellung der angepassten Modelle verwendet wurden. Weitere Informationen finden Sie in [Struktur der Trainingsdaten](/docs/services/language-translator/customizing.html#structure).
1.  Laden Sie die Trainingsdaten hoch, um neue angepasste Modelle für die Instanz mit Trainingsfunktionen zu erstellen. Weitere Informationen finden Sie in [Training für ein angepasstes Übersetzungsmodell durchführen](/docs/services/language-translator/customizing.html#training).
1.  Erstellen Sie in Ihrer App für das Feld "ModelID" einen Verweis auf die neuen angepassten Modelle.
1.  Heben Sie die Bindung des früheren Service zu Ihrer App in {{site.data.keyword.cloud_notm}} auf und löschen Sie ihn anschließend.

## 06. November 2015
{: #6-november-2015}

Die Betaversion des {{site.data.keyword.languagetranslatorshort}}-Tools wird veröffentlicht. Bei dem Tool handelt es sich um eine Webanwendung, die eine grafische Benutzerschnittstelle zur Verwaltung und zum Training von Modellen für eine präzisere Maschinenübersetzung bereitstellt. Sie können Projekte erstellen, Trainingsdaten hochladen, Training für angepasste Modelle durchführen und Text übersetzen.

## 01. Dezember 2014
{: #1-december-2014}

Für die Betaversionen der Machine Translator- und Language Identification-APIs wurde ein Upgrade durchgeführt und die APIs wurden in der {{site.data.keyword.languagetranslatorshort}}-API zusammengefasst. Wenn Sie sofort mit der Verwendung des neuen Service beginnen möchten, müssen Sie den Code so aktualisieren, dass er diese Änderungen reflektiert:

- **Neuer Parameter 'model\_id'**: In der Beta-API wurde der Parameter `sid` definiert, um das Modell für die Übersetzung auszuwählen. In dieser Version wurde der Parameter `sid` in `model_id` umbenannt. Verwenden Sie zum Abrufen der zulässigen Werte für `model_id` die Operation `GET/language  translator/api/v2/models`. Eine Liste aller Modelle und der zugehörigen `model_id`-Werte wird zurückgegeben.
- **Unterstützung für Sprachkombinationen**: Anstatt eine `model_id` auszuwählen, können Sie nun eine Quellen- und eine Zielsprache angeben; es wird dann standardmäßig das Modell verwendet, für das in der allgemeinen Domäne 'News' Training durchgeführt wurde.
- **Unterstützung für JSON-Anforderungshauptteil**: Bei einer POST-Übersetzungsanforderung können Sie die Anforderung nun als JSON-Anforderung übergeben. Die JSON-Formatierung ermöglicht die Übergabe mehrerer Absätze zur Übersetzung anstelle eines einzelnen Textabschnitts im Formularübergabeformat.
- **Unterstützung für JSON-Antworthauptteil**: Die Antworten auf Übersetzungsanforderungen unterstützen zusätzlich zum einfachen Textformat auch die JSON-Formatierung. Mithilfe des JSON-Formats kann die Übersetzung in mehreren Absätzen zurückgegeben werden, nicht nur in einem einzelnen Textabschnitt.
- **Unterstützung für den Accept-Header**: Der Accept-Header kann nun zur Definition des Formats der Antwort in allen Operationen verwendet werden (text/plain oder application/json).
- **Unterstützung für Spracherkennung**: Spracherkennungsmethoden wurden zu dieser API hinzugefügt. Dies ermöglicht die Identifizierung der Sprache der Eingabetexte und das Auflisten aller unterstützten Sprachen, die von der API erkannt werden können.


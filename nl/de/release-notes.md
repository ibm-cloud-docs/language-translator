---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-14"

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

## Neuer API-Authentifizierungsprozess
{: #iam-auth-process }

Der {{site.data.keyword.languagetranslatorshort}}-Service verfügt über einen neuen API-Authentifizierungsprozess für Serviceinstanzen, die an den folgenden Standorten gehostet werden:

- Dallas (seit 15. Juni 2018)
- Frankfurt (seit 15. Juni 2018)
- London
- Sydney (seit 12. Juni 2018)
- Tokio
- Washington, DC (seit 12. Juni 2018)

{{site.data.keyword.cloud_notm}} wird auf eine Token-basierte IAM-Authentifizierung umgestellt (IAM = Identity and Access Management). Bei bestimmten Serviceinstanzen erfolgt die Authentifizierung bei der API unter Verwendung von IAM.

- Bei _neuen_ Serviceinstanzen, die an den zuvor angegebenen Standorten eingerichtet wurden, verwenden Sie IAM für die Authentifizierung. Sie können entweder ein Trägertoken oder einen API-Schlüssel übergeben. Tokens unterstützen authentifizierte Anforderungen, ohne dass Serviceberechtigungsnachweise in jedem Aufruf eingebettet werden. API-Schlüssel verwenden die Basisauthentifizierung.

    Wenn Sie eines der Watson-SDKs verwenden, können Sie den API-Schlüssel übergeben und das SDK den Lebenszyklus der Tokens verwalten lassen. Weitere Informationen und Beispiele finden Sie unter [Authentifizierung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/apidocs/language-translator#authentication){: new_window} in der API-Referenz.
- Bei _bestehenden_ Serviceinstanzen, die Sie vor dem angegebenen Datum erstellt haben, authentifizieren Sie sich weiterhin, indem Sie den Benutzernamen und das Kennwort für die Serviceinstanz angeben. Zu einem späteren Zeitpunkt müssen Sie diese Serviceinstanzen auf die IAM-Authentifizierung umstellen. Es werden Updates zum Umstellungsprozess und -zeitpunkt bereitgestellt. Weitere Informationen zur Umstellung finden Sie unter [Cloud Foundry-Serviceinstanzen in eine Ressourcengruppe migrieren](/docs/resources?topic=resources-migrate#migrate).

Um herauszufinden, welche Authentifizierung verwendet werden soll, können Sie die Serviceberechtigungsnachweise anzeigen, indem Sie auf die Serviceinstanz auf der [{{site.data.keyword.cloud_notm}}-Ressourcenseite ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/resources){: new_window} klicken.

## Service-API-Versionierung
{: shortdesc}

API-Anforderungen in {{site.data.keyword.languagetranslatorshort}} Version 3 erfordern einen Versionsparameter, der ein Datum im Format `version=YYYY-MM-DD` verwendet. Jedes Mal, wenn die API nicht abwärts kompatibel geändert wird, wird eine neue Nebenversion der API freigegeben.

Sie müssen den Versionsparameter mit jeder API-Anforderung senden. Der Service verwendet die API-Version für das von Ihnen angegebene Datum oder für die neueste Version vor diesem Datum. Verwenden Sie nicht standardmäßig das aktuelle Datum. Geben Sie stattdessen ein Datum an, das einer Version entspricht, die mit Ihrer App kompatibel ist, und ändern Sie es erst dann, wenn Ihre App für eine spätere Version bereit ist.

Die aktuelle Version ist `2018-05-01`.

## 14. Juni 2019
{: #14-june-2019}

Neue [Übersetzungsmodelle](/docs/services/language-translator?topic=language-translator-translation-models) sind jetzt für Englisch und Griechisch verfügbar.
- Englisch - Griechisch (en-el)
- Griechisch - Englisch (el-en)

## 13. Juni 2019
{: #13-june-2019}

Neue [Übersetzungsmodelle](/docs/services/language-translator?topic=language-translator-translation-models) sind jetzt für Englisch und Hebräisch verfügbar.
- Englisch - Hebräisch (en-he)
- Hebräisch - Englisch (he-en)

## 21. März 2019
{: #21-march-2019}

Seit 21. März 2019 werden nur noch Informationen zu Serviceberechtigungsnachweisen angezeigt, die zu der Rolle gehören, die Ihrem {{site.data.keyword.cloud_notm}}-Konto zugeordnet ist. Wenn Sie z. B. eine Rolle `Leseberechtigter` zugeordnet haben, sind alle `Schreibberechtigten` oder höhere Stufen von Serviceberechtigungsnachweisen nicht sichtbar.

Diese Änderung wirkt sich nicht auf den API-Zugriff für Benutzer oder Anwendungen mit bestehenden Serviceschlüssel-Berechtigungsnachweisen aus. Nur die Anzeige von Berechtigungsnachweisen innerhalb von {{site.data.keyword.cloud_notm}} ist betroffen.

Weitere Informationen zu Serviceschlüsseln und Benutzerrollen finden Sie unter [API-Schlüssel des IAM-Service](/docs/services/watson?topic=watson-api-key-bp#api-key-bp).

## 14. Dezember 2018
{: #14-december-2018}

- Sie können seither {{site.data.keyword.languagetranslatorshort}}-Serviceinstanzen am {{site.data.keyword.cloud_notm}}-Standort London erstellen.

## 16. November 2018
{: #16-november-2018}

- [Dokumente übersetzen (Beta)](/docs/services/language-translator?topic=language-translator-translating-documents) ist jetzt über neue API-Endpunkte verfügbar. Sie übergeben ein Microsoft Office-Dokument, ein PDF-Dokument oder ein anderes Dokument mit einem unterstützten Dateiformat zur Verarbeitung und {{site.data.keyword.languagetranslatorshort}} stellt eine übersetzte Kopie zur Verfügung, die die ursprüngliche Formatierung beibehält.

  - [Unterstützte Dateiformate](/docs/services/language-translator?topic=language-translator-translating-documents#supported-file-types) sind `.doc`, `.ppt`, `.pdf` usw.

- Neue [Übersetzungsmodelle](/docs/services/language-translator?topic=language-translator-translation-models) für Ungarisch sind jetzt verfügbar:
  - Ungarisch - Englisch (hu-en)
  - Englisch - Ungarisch (en-hu)

## 8. November 2018
{: #8-november-2018}

- Sie können seither {{site.data.keyword.languagetranslatorshort}}-Serviceinstanzen am {{site.data.keyword.cloud_notm}}-Standort Tokio erstellen.

## 9. August 2018
{: #9-august-2018}

Neue [Übersetzungsmodelle](/docs/services/language-translator?topic=language-translator-translation-models) für Norwegisch (Bokmål) sind jetzt verfügbar:
  - Norwegisch (Bokmål) - Englisch (nb-en)
  - Englisch - Norwegisch (Bokmål) (en-nb)

## 27. Juni 2018
{: #27-june-2018}

Neue [Übersetzungsmodelle](/docs/services/language-translator?topic=language-translator-translation-models), die sechs neue Sprachen unterstützen, sind jetzt zur Verfügung:
  - Katalanisch
    - Katalanisch - Spanisch (ca-es)
    - Spanisch - Katalanisch (es-ca)
  - Tschechisch
    - Tschechisch - Englisch (cs-en)
    - Englisch - Tschechisch (en-cs)
  - Dänisch
    - Dänisch - Englisch (da-en)
    - Englisch - Dänisch (en-da)
  - Finnisch
    - Finnisch - Englisch (fi-en)
    - Englisch - Finnisch (en-fi)
  - Hindi
    - Hindi - Englisch (hi-en)
    - Englisch - Hindi (en-hi)
  - Schwedisch
    - Schwedisch - Englisch (sv-en)
    - Englisch - Schwedisch (en-sv)
  

## 15. Juni 2018
{: #15-june-2018}

Seit dem 15. Juni 2018 setzen neue Serviceinstanzen, die in Deutschland und den Vereinigten Staaten (Süden) erstellt wurden, die [IAM-Authentifizierung (Identity and Access Management)](#iam-auth-process) ein.

Neue Serviceinstanzen, die Sie in Deutschland und in den Vereinigten Staaten (Süden) erstellen, sind nicht mehr mit Language Translator Version 2 kompatibel. Wenn Sie Language Translator Version 2 verwenden und beabsichtigen, neue Serviceinstanzen in Ihrer Anwendung zu verwenden, müssen Sie [auf Version 3 der API migrieren](/docs/services/language-translator?topic=language-translator-migrating).

## 12. Juni 2018
{: #12-june-2018}

{{site.data.keyword.languagetranslatorshort}} Version 3 ist jetzt verfügbar. Version 2 der Language Translator-API ist seit dem 31. Juli 2018 nicht mehr verfügbar. Die neuesten Serviceerweiterungen können nur nach Migration auf Version 3 der API genutzt werden. Weitere Informationen finden Sie auf der Seite [Auf Language Translator Version 3 migrieren](/docs/services/language-translator?topic=language-translator-migrating).

### Neuerungen in Version 3
{: #whats-new}

-  Version 3 der {{site.data.keyword.languagetranslatorshort}}-API beinhaltet NMT-Modelle (**Neural Machine Translation**), die signifikant bessere Übersetzungen ermöglichen. Alle NMT-Modelle stehen jetzt zur Anpassung zur Verfügung.
-  Angepasste Modelle können als Basismodelle für die Anpassung von Vorgabewörterbüchern verwendet werden.
-  Version 3 der API ist ein vereinfachtes, vollständig in JSON vorliegendes Subset der veralteten Version 2 der API.
-  Einführung von API-Versionsdaten, um Entwicklern die Möglichkeit zu geben, zukünftige API-Änderungen je nach Bedarf zu übernehmen.

### Wichtige Änderungen
{: #breaking-changes}

- Obligatorisches Versionsdatum für alle API-Endpunkte: API-Anforderungen in Version 3 erfordern einen Abfrageparameter im Format `version = YYYY-MM-DD`. Die neueste API-Version ist `version=2018-05-01`.
- Vereinfachte API:
  - Die Methoden zum **Übersetzen** (translate) und **Erkennen** (identify) bieten nicht die Möglichkeit, einfache Textantworten in Version 3 zurückzugeben. Die Methoden geben nur JSON-Antworten zurück.
  - Die Methoden `GET /translate` und `GET /identify` werden in Version 3 nicht unterstützt. Verwenden Sie stattdessen die Methoden `POST /translate` und `POST /identify`. 
- Die Anpassung monolingualer Korpora wird in Version 3 nicht unterstützt.
- Das Erstellen von angepassten Modellen mit parallelem Korpus und Vorgabewörterbuch muss nun in zwei API-Aufrufen erfolgen. Zuerst muss das Modell mit einem parallelem Korpus angepasst werden. Nachdem das Training für das angepasste Modell abgeschlossen wurde, passen Sie es erneut mit dem Vorgabewörterbuch an. Mit dieser Änderung können Sie ein angepasstes Modell verwenden, das mit einem parallelen Korpus als Basis für die Anpassung des Vorgabewörterbuchs trainiert wurde.
- In Version 3 der API stehen keine spezialisierten Modelle für die Domänen 'Dialog' und 'Patent' zur Verfügung. Die Übersetzungsqualität, die von den NMT-Modellen in den Domänen 'Dialog' und 'Patent' erzielt wird, wurde gegenüber den älteren spezialisierten Modellen verbessert.
- Fehlerobjektschlüssel wurden umbenannt, sodass sie mit anderen Watson-APIs konsistent sind. `error_code` wurde in `code` umbenannt und `error_message` wurde in `error` umbenannt.

### IAM-Authentifizierung

Seit dem 12. Juni 2018 setzen neue Serviceinstanzen, die in Sydney und den Vereinigten Staaten (Osten) erstellt wurden, die [IAM-Authentifizierung (Identity and Access Management)](#iam-auth-process) ein.

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

Sie finden ein [Video auf YouTube ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://youtu.be/L6ZC0QaUZ2k), das erläutert, wie {{site.data.keyword.languagetranslatorshort}} mit der neuen NMT-Vorschau eingerichtet wird.


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
2.  Erstellen Sie eine Bindung von der neuen Serviceinstanz mit Trainingsfunktionen zu Ihrer App in {{site.data.keyword.cloud_notm}}.
3.  Stellen Sie die Daten zusammen, die für die ursprüngliche Erstellung der angepassten Modelle verwendet wurden. Weitere Informationen finden Sie in [Struktur der Trainingsdaten](/docs/services/language-translator?topic=language-translator-customizing#structure).
4.  Laden Sie die Trainingsdaten hoch, um neue angepasste Modelle für die Instanz mit Trainingsfunktionen zu erstellen. Weitere Informationen finden Sie in [Training für ein angepasstes Übersetzungsmodell durchführen](/docs/services/language-translator?topic=language-translator-customizing#training).
5.  Erstellen Sie in Ihrer App für das Feld "ModelID" einen Verweis auf die neuen angepassten Modelle.
6.  Heben Sie die Bindung des früheren Service zu Ihrer App in {{site.data.keyword.cloud_notm}} auf und löschen Sie ihn anschließend.

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

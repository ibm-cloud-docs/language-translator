---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

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

# Dokumente übersetzen (Beta)
{: #document-translator-tutorial}


Sie können Dateien unter Beibehaltung des ursprünglichen Formats von einer Sprache in eine andere Sprache übersetzen. Mehr als zwölf verschiedene Dateiformate können übersetzt werden, einschließlich MS Office, Open Office und PDF.
{:shortdesc}

## Vorbereitungen
{: #prerequisites}

- [Beginnen Sie](/docs/services/language-translator?topic=language-translator-getting-started) mit {{site.data.keyword.languagetranslatorshort}}. Sie benötigen Ihre {{site.data.keyword.languagetranslatorshort}}-Serviceberechtigungsnachweise (`apikey` und `url`).
- Stellen Sie sicher, dass das zu übersetzende Dokument die folgenden Anforderungen erfüllt:
    - Maximale Dateigröße: **20 MB**
    - [Unterstützte Dateiformate](#supported-file-formats)
    - [Unterstützte Übersetzungsmodelle](/docs/services/language-translator?topic=language-translator-translation-models)

## Schritt 1: Dokument zur Übersetzung an Service übergeben
{: #submit-document-to-translate}

Die folgende Beispielanforderung übergibt eine Beispieldatei *curriculum.pdf* an den Service und übersetzt sie aus dem Englischen ins Französische. Ersetzen Sie `{apikey}` und `{url}` durch Ihre Serviceberechtigungsnachweise und ersetzen Sie `curriculum.pdf` durch einen relativen Pfad zu Ihrer Datei.

Beispielanforderung:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Um ein Dokument mit einem [angepassten Modell](/docs/services/language-translator?topic=language-translator-customizing) zu übersetzen, verwenden Sie den Parameter **model_id**. Die folgende Anforderung übersetzt das Dokument mit dem angepassten Modell mit der Modell-ID `96221b69-8e46-42e4-a3c1-808e17c787ca`.

Beispielanforderung:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
{url}/v3/documents?version=2018-05-01
```
{: pre}


Eine erfolgreiche Anforderung gibt in der Antwort eine `dokument-id` zurück.


Beispielantwort:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "processing",
  "created": "2018-10-11T03:31:25"
}
```
{: codeblock}

## Schritt 2: Übersetzungsstatus prüfen
{: #check-translation-status}

Nachdem Sie ein Dokument zur Übersetzung übergeben haben, können Sie den Übersetzungsstatus prüfen, um herauszufinden, wann das übersetzte Dokument zum Herunterladen verfügbar ist. Die folgende Beispielanforderung überprüft den Übersetzungsstatus des Dokuments mit der Dokument-ID `bae02796-0d28-435c-9115-888359fdde62`. 

Beispielanforderung:
```bash
curl -X GET \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Beispielantwort:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "available",
  "created": "2018-10-11T03:31:25",
  "completed": "2018-10-11T03:31:38"
}
```
{: codeblock}

Wenn der `Status` in der Antwort `available` (verfügbar) ist, kann das übersetzte Dokument heruntergeladen werden.

## Schritt 3: Übersetztes Dokument herunterladen
{: #download-translated-document}

Mit der folgenden Beispielanforderung wird das übersetzte Dokument mit der Dokument-ID `bae02796-0d28-435c-9115-888359fdde62` in der Datei *curriculum-fr.pdf* gespeichert. 

Beispielanforderung:
```bash
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01
```
{: pre}

## Schritt 4: Zuvor übergebenes Dokument übersetzen
{: #translate-document-by-reference}

Die folgende Beispielanforderung verweist auf die englische Originaldatei *curriculum.pdf* mit der `document_id` `bae02796-0d28-435c-9115 -888359fdde62` und übersetzt sie in die portugiesische Sprache.

Beispielanforderung:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Beispielantwort:
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

Die Antwort enthält eine neue `dokument-id`. Wiederholen Sie die Schritte zwei und drei mit Ihrer neuen `dokument-id`, um den Status der Übersetzung zu überprüfen und um die übersetzte Datei herunterzuladen, sobald sie verfügbar ist.

## Schritt 5: Dokumente löschen
{: #delete-documents}

Die Originaldokumente und alle zugehörigen übersetzten Dokumente werden automatisch gelöscht, wenn sie für eine bestimmte Zeit nicht verwendet wurden. Weitere Informationen finden Sie unter [Informationssicherheit](/docs/services/language-translator?topic=language-translator-information-security).
{: tip}

Wenn Sie Dokumente manuell löschen möchten, verwenden Sie die Methode zum **Löschen von Dokumenten**. In diesem Lernprogramm gibt es für die englische Datei *curriculum.pdf* zwei Übersetzungen, d. h. es sind zwei Anforderungen erforderlich, um alle Kopien des Originaldokuments zu löschen.

Löschen Sie die Originaldatei *curriculum.pdf*, die zuerst in die französische Sprache übersetzt wurde:
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Löschen Sie das Duplikat der Originaldatei *curriculum.pdf* und die portugiesische Übersetzung:
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01
```
{: pre}

## Unterstützte Dateiformate
{: #supported-file-formats}

-  Microsoft Office
    - Word: `.doc`, `.docx`
    - PowerPoint: `.ppt`, `.pptx`
    - Excel: `.xls`, `.xlsx`
    - Rich Text Format: `.rtf`
- Open Office
    - Writer: `.odt`
    - Impress: `.odp`
    - Calc: `.ods`
- Andere Formate
    - PDF: `.pdf`
    - HTML: `.htm`, `.html`
    - XML: `.xml`
    - JSON: `.json` (Werte mit dem Typ `string` oder `string array` werden übersetzt)
    - Text: `.txt`

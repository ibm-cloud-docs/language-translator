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

# Modell anpassen
{: #customizing}

Möchten Sie eine Übersetzungsfunktion erstellen, die von der Kundenunterstützung genutzt wird? Gibt es unternehmensspezifische Begriffe, die in Dialogen auf bestimmte Weise gehandhabt werden sollen? Möchten Sie es Ihren Entwicklern in einem bestimmten Land ermöglichen, Patentdaten in einer anderen Sprache zu suchen? Melden Sie häufig Patente zu einer bestimmten Technologie an? Verwenden Sie eigene Daten zur Erstellung eines angepassten Wörterverzeichnisses und eines angepassten Übersetzungsmodells in der {{site.data.keyword.languagetranslatorshort}}-API.
{: shortdesc}

Für die Anpassung des {{site.data.keyword.languagetranslatorshort}}-Modells stehen verschiedene Möglichkeiten zur Verfügung:

- Sie können Training für den Service durchführen, das Paare entsprechender Begriffe oder Ausdrücke in einer Quellen- und einer Zielsprache umfasst. Implementieren Sie ein *Vorgabewörterbuch* mit obligatorischen Paaren entsprechender Begriffe oder Ausdrücke und definitiven Begriffen, die vom Übersetzungsservice verbindlich zu verwenden sind. Oder geben Sie ein *paralleles Korpus* an, das Paare entsprechender Begriffe oder Ausdrücke enthält, die als alternative Übersetzungsvorschläge vom Übersetzungsservice verwendet werden sollen.
- Sie können einen umfangreichen Text in einer Zielsprache hochladen (als *monolinguales Korpus* bezeichnet), der als Sprachbeispiel dient, das der Service auswerten und zur Verbesserung der allgemeinen Übersetzungsqualität nutzen kann.

Verwenden Sie zum Anzeigen der Liste mit anpassbaren Modellen die Methode `GET /v2/models` und suchen Sie nach dem Antwortparameter `customizable=true` in der Antwort des jeweiligen Sprachmodells.

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

Für jedes anpassbare Modell können bis zu 10 Anpassungen pro Serviceinstanz gespeichert werden.

## Struktur der Trainingsdaten
{: #structure}

Zur Bereitstellung eines Wörterbuchs oder Korpus mit Begriffen für das Training des {{site.data.keyword.languagetranslatorshort}}-Service erstellen Sie ein gültiges Dokument im UTF-8-Format, das der Spezifikation von Translation Memory Exchange (TMX) [Version 1.4 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ttt.org/oscarstandards/tmx/tmx14.dtd){: new_window} entspricht. TMX ist eine XML-Spezifikation, die für Maschinenübersetzungstools konzipiert ist. Im folgenden Beispiel ist eine mit TMX formatierte Wörterbuchdatei dargestellt, die zwei jeweils aus Begriff und Übersetzung bestehende Paare enthält:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>International Business Machines</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>International Business Machines</seg>
      </tuv>
    </tu>
    <tu>
      <tuv xml:lang="en">
        <seg>patent</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>brevet</seg>
      </tuv>
    </tu>
  </body>
</tmx>
```
{: codeblock}

Jedes aus Begriff und Übersetzung bestehende Paar muss in die Tags `<tu>` eingeschlossen werden:

```xml
<tu>
  <tuv xml:lang="en">
    <seg>International Business Machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

Das Attribut `xml:lang` im Tag `<tuv>` identifiziert die Sprache eines Begriffs, der Tag `<seg>` enthält den Begriff oder die Übersetzung.

Der {{site.data.keyword.languagetranslatorshort}}-Service verwendet nur die Elemente `<tu>`, `<tuv>` und `<seg>`. Alle anderen Elemente im Beispiel sind für eine gültige TMX-Datei erforderlich oder dienen nur zu Informationszwecken, werden jedoch vom Service nicht verwendet.

Das vorherige Beispiel veranschaulicht, wie die Übersetzung eines technischen Begriffs wie 'patent' verbindlich standardisiert wird und wie die Übersetzung eines Firmennamens wie 'International Business Machines' angepasst wird. Mit dem Standardmodell wird 'International Business Machines' möglicherweise mit 'Machines Commerciales Internationales' übersetzt, tatsächlich darf der Begriff jedoch nicht übersetzt werden, da es sich um einen Firmennamen handelt.

## Beispiel als Vorlage verwenden

Führen Sie die folgenden Schritte aus, um das bereitgestellte Beispiel als Vorlage für ein eigenes Wörterbuch oder Korpus zu verwenden:

1.  Kopieren Sie das Beispiel und fügen Sie es in einen Texteditor ein.

1.  Ändern Sie das Attribut `srclang` des Tags `<header>` in den [Sprachencode ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} der Quellensprache, die das Wörterbuch bzw. das parallele Korpus verwenden soll.

1.  Ändern Sie das Attribut `xml:lang` des Tags `<tuv>` in den korrekten [Sprachencode ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} für die einzelnen Begriffe bzw. Übersetzungen.

    Der {{site.data.keyword.languagetranslatorshort}}-Service verwendet ISO 639-1-Sprachencodes für alle Sprachen; eine Ausnahme bildet ägyptisches Arabisch, für das der ISO 639-3-Code verwendet wird.

1.  Speichern Sie das Dokument mit der Erweiterung `.tmx` und UTF-8-Codierung.

### TMX-Datei in UTF-8-Codierung ändern

Für die Erstellung oder Generierung von TMX-Dateien können eine Reihe von Tools verwendet werden. Häufig sind generierte TMX-Dateien standardmäßig mit UTF-16 codiert. Der {{site.data.keyword.languagetranslatorshort}}-Service akzeptiert ausschließlich TMX-Dateien mit UTF-8-Codierung. Führen Sie die folgenden Schritte aus, um die Codierung einer TMX-Datei zu ändern:

1.  Öffnen Sie die TMX-Datei in einem Texteditor.

1.  Ändern Sie den XML-Header (falls vorhanden) von `<?xml ... encoding="utf-16"?>` in `<?xml ... encoding="utf-8"?>`.

1.  Speichern Sie die Datei mit einem neuen Namen und mit UTF-8-Codierung für die Ausgabe.

Mac-Benutzer können die Dateicodierung auch ändern, indem sie den XML-Header des Dokuments wie in Schritt 2 beschrieben aktualisieren und dann den folgenden Befehl auf dem Terminal ausführen:

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}

## Training für ein angepasstes Übersetzungsmodell durchführen
{: #training}

Verwenden Sie die Methode `POST /v2/models`, um die TMX-Datei hochzuladen und Training für das Übersetzungsmodell durchzuführen. Geben Sie mindestens eine der folgenden Dateioptionen an, um Training für das angepasste Modell durchzuführen:

- `forced_glossary`: Ein Vorgabewörterbuch ist eine mit UTF-8 codierte TMX-Datei. Sie enthält Paare entsprechender Begriffe in der Quellen- und Zielsprache, die vom System als absolut gültige Vorgabe verwendet werden. Diese Datei überschreibt die ursprünglichen Domänendaten vollständig.

    Für Vorgabewörterbücher gilt eine maximale Dateigröße von 10 MB. Zum gegenwärtigen Zeitpunkt kann nur eine einzelne Vorgabewörterbuchdatei pro Übersetzungsmodell hochgeladen werden.
    
- `parallel_corpus`: Ein paralleles Korpus ist eine mit UTF-8 codierte TMX-Datei. Sie enthält entsprechende Ausdrücke in der Quellen- und Zielsprache, die als Beispiele für Watson dienen. Ein paralleles Korpus unterscheidet sich von einem Vorgabewörterbuch dahingehend, dass es die ursprünglichen Domänendaten nicht überschreibt.

    Damit ein erfolgreiches Training für ein angepasstes Modell durchgeführt werden kann, muss ein Dokument für ein paralleles Korpus mindestens 5000 Paare aus Begriff und Übersetzung enthalten.
    
- `monolingual_corpus`: Ein monolinguales Korpus ist eine mit UTF-8 codierte einfache Textdatei. Sie enthält einen Text in der Zielsprache, der thematisch zur Übersetzung passt. Durch die Bereitstellung eines monolingualen Korpus können wörtliche Übersetzungen verbessert werden, indem sie flüssiger und natürlicher gemacht werden.

    Damit ein erfolgreiches Training für ein angepasstes Modell durchgeführt werden kann, muss ein Dokument für ein monolinguales Korpus mindestens 1000 Sätze enthalten.

Die kumulative Dateigröße aller hochgeladenen Wörterbuch- und Korpusdateien ist auf 250 MB begrenzt. Abhängig von der Größe der hochgeladenen Dateien kann das Training einige Minuten, z. B. bei einem Wörterbuch, oder mehrere Stunden, z. B. bei einem großen Korpus, in Anspruch nehmen.

Im folgenden curl-Beispiel wird die Dateioption `forced_glossary` verwendet.
1. Laden Sie das TMX-Dateibeispiel im Abschnitt [Struktur der Trainingsdaten](#structure) herunter.
1. Verwenden Sie die Domäne 'News' für die französische Sprache (en-fr) als Basismodell. Alle Angaben in der TMX-Datei überschreiben die ursprünglichen Domänendaten vollständig.

    Verwenden Sie die Methode `GET v2/models`, um alle Modelldomänen, die der {{site.data.keyword.languagetranslatorshort}}-Service unterstützt, zu suchen:

```curl
curl -u "{username}":"{password}" -X POST -F base_model_id=en-fr -F name="test_glossary" -F forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

Die Antwort der Methode `POST /v2/models` besteht aus dem Code `200` und einer neuen `model_id`. Verwenden Sie die `model_id` bei der Übersetzung von Text mithilfe dieses neu angepassten Modells.

## Training überwachen

Die Größe der TMX-Trainingsdatei wirkt sich auf die Trainingszeit einer `POST /v2/models`-Anforderung aus. Verwenden Sie die Methode `GET /v2/models/<model_id>` und überprüfen Sie den Wert des Parameters `status` in der Antwort, um den Fortschritt des Trainings zu überwachen und zu prüfen, ob das Training erfolgreich abgeschlossen wurde.

Dieser Beispielbefehl liefert Informationen zum Modell und überprüft den Status des Trainings, das im Abschnitt [Training für ein angepasstes Übersetzungsmodell durchführen](#training) gestartet wurde. In diesem Befehl wird ein leerer Anforderungshauptteil verwendet.

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}

Der Antwortparameter `STATUS` beschreibt den Status des Modells im Trainingsprozess:

- `uploading`
- `uploaded`
- `dispatching`
- `queued@<#>`
- `training`
- `trained`
- `publishing`
- `available`

Wenn der Modellstatus `available` lautet, ist das Modell zur Verwendung mit Ihrer Serviceinstanz bereit. Wenn das Modell gelöscht wurde oder beim Trainingsprozess ein Fehler aufgetreten ist, wird möglicherweise einer der folgenden Fehler angezeigt:

- `deleted`
- `error`

## Angepasstes Übersetzungsmodell verwenden

Geben Sie nach dem Training eines angepassten Übersetzungsmodells die Modell-ID (model\_id) dieses Übersetzungsmodells zur Verwendung in der Methode `POST /v2/translate` oder `GET /v2/translate` an.

Mit dem folgenden Beispiel wird das Modell für die Übersetzung aus der englischen in die französische Sprache, das im Abschnitt [Training für ein angepasstes Übersetzungsmodell durchführen](#training) angepasst wurde, aufgerufen.

```curl
curl -u "{username}":"{password}" --header "Content-Type: application/json" -X POST --data "{\"model_id\": \"3e7dfdbe-f757-4150-afee-458e71eb93fb\",\"text\": \"Hello, my name is Watson, and I work for International Business Machines. How can I help you today?\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate 
```
{: codeblock}

Der {{site.data.keyword.languagetranslatorshort}}-Service wertet die Qualität der Übersetzung aus, indem er die BLEU-Standards (Bilingual Evaluation Understudy) und die von IBM entwickelten Standards verwendet. Die Ergebnisse können abhängig von der Sprachkombination, der verwendeten regions- oder landestypischen Sprache oder der Domäne der Daten variieren.

## Angepasstes Übersetzungsmodell löschen

Wenn ein Übersetzungsmodell veraltet ist, können Sie es löschen. Verwenden Sie zum Löschen eines angepassten Übersetzungsmodells die Methode `DELETE /v2/models/<model_id>`. Verwenden Sie zum Abrufen der Modell-IDs aller Übersetzungsmodelle - sowohl angepasster als auch Standardmodelle - die Methode `GET /v2/models`.

Mit dem folgenden Befehl wird das Übersetzungsmodell gelöscht, das in den hier beschriebenen Beispielen erstellt wurde.

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}


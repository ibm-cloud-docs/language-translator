---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-13"

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

Die meisten der in {{site.data.keyword.languagetranslatorshort}} bereitgestellten Übersetzungsmodelle können erweitert werden, sodass sie sich angepasste Begriffe und Ausdrücke oder einen allgemeinen Stil aneignen, der aus Ihren Übersetzungsdaten abgeleitet wird. Befolgen Sie die folgenden Anweisungen, um ein eigenes angepasstes Übersetzungsmodell zu erstellen.
{: shortdesc}

## Vorbereitungen
{: #before-you-begin}

1. Stellen Sie sicher, dass Ihre {{site.data.keyword.languagetranslatorshort}}-Serviceinstanz auf dem Advanced- oder Premium-Preisstrukturplan basiert. Die Pläne 'Lite' und 'Standard' unterstützen die Anpassung nicht.
1. Suchen Sie nach einem anpassbaren Basismodell für Ihr Sprachpaar. Sie benötigen die Modell-ID des Basismodells, um Ihr angepasstes Modell zu trainieren.
    - Durchsuchen Sie die Modelle, die auf der Seite [Übersetzungsmodelle](/docs/services/language-translator?topic=language-translator-translation-models) aufgeführt sind. Suchen Sie in der Spalte **Anpassungsfähigkeit** nach dem Wert "**true**" und stellen Sie sicher, dass die Sprachen **Quelle** und **Ziel** des Modells mit Ihrem Sprachpaar übereinstimmen.
    - Alternativ dazu können Sie die API-Methode zum [Auflisten von Modellen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/apidocs/language-translator#list-models) verwenden, um Modelle programmgestützt zu durchsuchen. Sie können die Ergebnisse mit den Parametern `source` und `target` nach der Sprache filtern.

## Schritt 1: Eigene Trainingsdaten erstellen
{: #create-your-training-data}

Für den Service sind Trainingsdaten erforderlich, die im [TMX-Dateiformat (Translation Memory Exchange)](#creating-tmx-files) bereitgestellt werden müssen. Sie können bis zu zehn Anpassungen für jedes Sprachpaar in einer Serviceinstanz speichern. Der Service unterstützt zwei Arten von Anpassungsanforderungen. Sie können ein Modell entweder mit einem Vorgabewörterbuch (Forced Glossary) oder mit einem Textkorpus, der sich aus zweisprachigen Satzpaaren zusammensetzt, anpassen.

- Verwenden Sie ein [Vorgabewörterbuch](#forced-glossary-customization), um Begriffe und Ausdrücke auf bestimmte Art und Weise zu übersetzen.
- Verwenden Sie ein [paralleles Korpus](#parallel-corpus-customization), wenn Sie möchten, dass sich Ihr angepasstes Modell an allgemeinen Übersetzungsmustern in Ihren Beispielen orientiert und dadurch dazulernt. Was Ihr Modell aus einem parallelen Korpus lernt, kann die Übersetzungsergebnisse für eingegebenen Text verbessern, für den das Modell noch nicht trainiert wurde.

Wenn Sie Ihre [TMX-Dateien (Translation Memory Exchange)](#creating-tmx-files) erstellt haben, sind Sie bereit, Ihr Modell zu trainieren.

## Schritt 2: Modell trainieren
{: #train-your-model}

Verwenden Sie die Methode zum [Erstellen von Modellen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/apidocs/language-translator#create-model), um Ihr Modell zu trainieren. Geben Sie in Ihrer Anforderung die Modell-ID eines anpassbaren Basismodells sowie Trainingsdaten im Parameter `forced_glossary` oder `parallel_corpus` an.

### Beispielanforderung
{: #train-model-example-request}

Die folgende Beispielanforderung verwendet eine Vorgabewörterbuchdatei _glossary.tmx_, um das Basismodell `en-es` anzupassen. Ein Beispiel für eine TMX-Datei mit Vorgabewörterbuch finden Sie unter [Anpassung eines Vorgabewörterbuchs](#forced-glossary).

```bash
curl --user apikey:{apikey} -X POST --form forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

Die API-Antwort enthält Details zu Ihrem angepassten Modell, einschließlich der zugehörigen Modell-ID. Verwenden Sie die Modell-ID, um den Status Ihres Modells zu überprüfen und um Sätze zu übersetzen, sobald der Status des Modells "available" wird.

```json
{
  "model_id": "96221b69-8e46-42e4-a3c1-808e17c787ca",
  "source": "en",
  "target": "es",
  "base_model_id": "en-es",
  "domain": "general",
  "customizable": false,
  "default_model": false,
  "owner": "4937aab7-0f3a-4a75-bee1-0b7a12b6b8",
  "status": "uploaded",
  "name": "custom-english-to-spanish",
  "train_log": null
}
```
{: codeblock}

## Schritt 3: Modellstatus überprüfen
{: #check-model-status}

Das Trainieren des Modells kann von einigen Minuten (bei Verwendung von Vorgabewörterbüchern) bis zu mehreren Stunden (bei Verwendung großer paralleler Korpora) dauern, je nachdem, wie viel Trainingsdaten vorhanden sind. Um zu ermitteln, ob Ihr Modell verfügbar ist, verwenden Sie die Methode zum [Abrufen von Modellen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/apidocs/language-translator#get-model-details) und geben Sie die Modell-ID an, die Sie in der Serviceantwort in Schritt 2 erhalten haben. Außerdem können Sie den Status aller Ihrer Modelle mit der Methode zum [Auflisten von Modellen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/apidocs/language-translator#list-models) verwenden.

Das Antwortattribut `status` beschreibt den Status des Modells im Trainingsprozess:

- `uploading`
- `uploaded`
- `dispatching`
- `queued`
- `training`
- `trained`
- `publishing`
- `available`

Wenn der Modellstatus `available` lautet, ist das Modell zur Verwendung mit Ihrer Serviceinstanz bereit. Wenn das Modell gelöscht wurde oder wenn beim Trainingsprozess ein Fehler aufgetreten ist, wird möglicherweise einer der folgenden Statuszustände angezeigt:

- `deleted`
- `error`

### Beispielanforderung
{: #check-model-example-request}

Im folgenden Beispiel werden Informationen für das Modell mit der Modell-ID `96221b69-8e46-42e4-a3c1-808e17c787ca` abgerufen.

```bash
curl --user apikey:{apikey_value} "https://gateway.watsonplatform.net/language-translator/api/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## Schritt 4: Text mit angepasstem Modell übersetzen
{: #translate-text}

Um Ihr angepasstes Modell zu verwenden, geben Sie den zu übersetzenden Text und die Modell-ID des angepassten Modells in der Methode zum [Übersetzen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/apidocs/language-translator#translate) an.

### Beispielanforderung
{: #translate-text-example-request}

Im folgenden Beispiel wird Text mit dem angepassten Modell mit der Modell-ID `96221b69-8e46-42e4-a3c1-808e17c787ca` übersetzt.

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data '{"text":"Hello","model_id":"96221b69-8e46-42e4-a3c1-808e17c787ca"}' https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}


## Anpassung eines Vorgabewörterbuchs
{: #forced-glossary-customization}

Sie können ein **Vorgabewörterbuch** (Forced Glossary) verwenden, um obligatorische Übersetzungen für bestimmte Begriffe und Ausdrücke festzulegen. Wenn Sie das Übersetzungsverhalten gezielt steuern wollen, verwenden Sie ein Vorgabewörterbuch. 

- Format der Trainingsdaten: [TMX](#creating-tmx-files) (UTF-8-codiert)
- Maximale Dateigröße: 10 MB
- Sie können ein Vorgabewörterbuch auf ein Basismodell anwenden oder auf ein Modell, das mit einem parallelen Korpus angepasst wurde.
- Begrenzung auf ein Vorgabewörterbuch pro Modell.

Bei Beispielen mit Vorgabewörterbüchern ist die Groß-/Kleinschreibung zu beachten. Stellen Sie daher sicher, dass Ihre Trainingsdaten die Groß-/Kleinschreibung der Inhalte berücksichtigen, die Ihre Anwendung verarbeiten wird.
{: tip}

### Beispiel für die Verwendung eines Vorgabewörterbuchs
{: #forced-glossary-example}

Das folgende Beispiel zeigt eine TMX-Datei mit zwei Übersetzungspaaren. Das erste Paar sorgt dafür, dass "international business machines" bei der Übersetzung als Anglizismus erhalten bleibt. Diese Vorgabe einer Übersetzung kann nützlich sein, wenn z. B. Firmennamen nicht übersetzt werden sollen (auch wenn Sie im englischen Ausgangstext unrichtigerweise kleingeschrieben wurden). Das zweite Paar zwingt das Modell, immer die französische Übersetzung "brevet" zu verwenden, wenn im Englischen der Begriff "patent" vorkommt.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="phrase" o-tmf="" adminlang="en"
    srclang="en" datatype="PlainText" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
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



## Anpassung eines parallelen Korpus
{: #parallel-corpus-customization}

Sie können ein **paralleles Korpus** verwenden, um zusätzliche Übersetzungen bereitzustellen, anhand derer das Basismodell dazulernen kann. Dies ermöglicht es, das Basismodell an ein bestimmtes Fachgebiet (Domäne) anzupassen. Wie das resultierende angepasste Modell Text übersetzt, hängt davon ab, wie das Modell die Kombination aus parallelem Korpus und Basismodell interpretiert.

- Format der Trainingsdaten: [TMX](#creating-tmx-files) (UTF-8-codiert)
- Maximale Länge der Übersetzungspaare: 80 Wörter im Quellentext
- Minimale Anzahl von Übersetzungspaaren: 5.000
- Maximale Dateigröße: 250 MB
- Sie können mehrere Dateien mit parallelem Korpus zur Verarbeitung übergeben, indem Sie den mehrteiligen Formularparameter `parallel_corpus` wiederholen, solange die kumulative Größe der Dateien das Limit von 250 MB nicht überschreitet.

### Beispiel für ein paralleles Korpus
{: #parallel-corpus-example}

Im Folgenden finden Sie einen kleinen Teil eines parallelen Korpus für die Sprachrichtung Englisch/Französisch, das von der [MultiUN-Dokumentsammlung![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://opus.nlpl.eu/MultiUN.php) heruntergeladen wurde, die auf der OPUS-Website mit einem offenen parallelen Korpus verfügbar ist. Sie können eine komprimierte Version der gesamten TMX-Datei [hier ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz) herunterladen.


```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
<header creationdate="Tue Jan 29 12:49:40 2013"
          srclang="en"
          adminlang="en"
          o-tmf="unknown"
          segtype="sentence"
          creationtool="Uplug"
          creationtoolversion="unknown"
          datatype="PlainText" />
  <body>
    <tu>
      <tuv xml:lang="en"><seg>RESOLUTION 55/100</seg></tuv>
      <tuv xml:lang="fr"><seg>RÉSOLUTION 55/100</seg></tuv>
    </tu>
    <tu>
      <tuv xml:lang="en"><seg>Adopted at the 81st plenary meeting, on 4 December 2000, on the recommendation of the Committee (A/55/602/Add.2 and Corr.1, para. 94),The draft resolution recommended in the report was sponsored in the Committee by: Bolivia, Cuba, El Salvador, Ghana and Honduras. by a recorded vote of 106 to 1, with 67 abstentions, as follows:</seg></tuv>
      <tuv xml:lang="fr"><seg>Adoptée à la 81e séance plénière, le 4 décembre 2000, sur la recommandation de la Commission (A/55/602/Add.2, par. 94)Le projet de résolution recommandé dans le rapport de la Commission avait pour auteurs les pays suivants: Bolivie, Cuba, El Salvador, Ghana et Honduras., par 106 voix contre une, avec 67 abstentions, à la suite d'un vote enregistré, les voix s'étant réparties comme suit:</seg></tuv>
    </tu>
    ...
```
{: codeblock}

Die Verbesserungen durch die Anpassung des parallelen Korpus sind im Allgemeinen weniger vorhersehbar als die Ergebnisse, die sich durch die Anpassung eines Vorgabewörterbuchs erzielen lassen. Betrachten Sie zum Beispiel die folgende Übersetzungseinheit (Translation Unit) aus dem parallelen Korpus (Zeilen 172-175).

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

Wenn Sie den englischen Text "55/102. Globalization and its impact on the full enjoyment of all human rights" mit dem Basismodell `en-fr` übersetzen, erhalten Sie die folgende französische Übersetzung.

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

Wenn derselbe Eingabesatz von einem angepassten Modell, das mit dem Beispielkorpus trainiert wurde, übersetzt wird, erhalten Sie eine andere Übersetzung, die nicht mit der Beispielübersetzung identisch ist, die in den Trainingsdaten bereitgestellt wird.

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- Das angepasste Modell übersetzt "the full enjoyment" mit "le plein exercice" anstelle von "la pleine jouissance". Der Grund für diesen Unterschied gegenüber dem Basismodellverhalten ist wahrscheinlich, dass es viele Beispiele im Korpus gibt, in denen "enjoyment" mit "exercice" übersetzt wird.
- Das angepasste Modell übersetzt "of all human rights" mit "de tous les droits de l'homme", anstatt das Ergebnis aus der Übersetzungseinheit ("des droits de l'homme") zu reproduzieren. Dieses Verhalten zeigt das Verständnis des Basismodells durch das trainierte Modell sowie aller Übersetzungsbeispiele, die sich auf "of all human rights" im parallelen Korpus beziehen.

In einigen Fällen kann es so aussehen, als würde ein angepasstes Modell, das mit einem parallelen Korpus trainiert wurde, ein bestimmtes Beispiel ignorieren, das Sie bereitgestellt haben. In diesen Fällen sollten Sie versuchen, Ihre Trainingsdaten nach anderen Sätzen zu durchsuchen, die das Übersetzungsverhalten beeinflussen könnten, oder Sie können ein Vorgabewörterbuch verwenden, wenn Sie eine ganz bestimmte Übersetzung erhalten möchten.


## TMX-Dateien erstellen
{: #creating-tmx-files}

Zur Bereitstellung eines Wörterbuchs oder Korpus mit Begriffen für das Training des {{site.data.keyword.languagetranslatorshort}}-Service erstellen Sie ein gültiges Dokument im UTF-8-Format, das der Spezifikation von Translation Memory Exchange (TMX) [Version 1.4 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ttt.org/oscarStandards/tmx/){: new_window} entspricht. TMX ist eine XML-Spezifikation, die für Maschinenübersetzungstools konzipiert ist. Im folgenden Beispiel ist eine mit TMX formatierte Wörterbuchdatei mit zwei Übersetzungseinheiten (Translation Units, `<tu>`-Elemente) dargestellt:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
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
    <seg>international business machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

Das Attribut `xml:lang` im Tag `<tuv>` identifiziert die Sprache eines Begriffs, der Tag `<seg>` enthält den Begriff oder die Übersetzung.

Der {{site.data.keyword.languagetranslatorshort}}-Service verwendet nur die Elemente `<tu>`, `<tuv>` und `<seg>`. Alle anderen Elemente im Beispiel sind für eine gültige TMX-Datei erforderlich oder dienen nur zu Informationszwecken, werden jedoch vom Service nicht verwendet.



### Beispiel als Vorlage verwenden
{: #using-the-example-template}

Führen Sie die folgenden Schritte aus, um das bereitgestellte Beispiel als Vorlage für ein eigenes Wörterbuch oder Korpus zu verwenden:

1. Kopieren Sie das Beispiel und fügen Sie es in einen Texteditor ein.

2. Ändern Sie das Attribut `srclang` des Tags `<header>` in den [Sprachencode ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} der Quellensprache, die das Wörterbuch bzw. das parallele Korpus verwenden soll.

3. Ändern Sie das Attribut `xml:lang` des Tags `<tuv>` in den korrekten [Sprachencode ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} für die einzelnen Begriffe bzw. Übersetzungen.

4. Speichern Sie das Dokument mit der Erweiterung `.tmx` und UTF-8-Codierung.

### TMX-Datei in UTF-8-Codierung ändern
{: #changing-tmx-file-to-utf-8}

Für die Erstellung oder Generierung von TMX-Dateien können eine Reihe von Tools verwendet werden. Häufig sind generierte TMX-Dateien standardmäßig mit UTF-16 codiert. Der {{site.data.keyword.languagetranslatorshort}}-Service akzeptiert ausschließlich TMX-Dateien mit UTF-8-Codierung. Führen Sie die folgenden Schritte aus, um die Codierung einer TMX-Datei zu ändern:

1. Öffnen Sie die TMX-Datei in einem Texteditor.

1. Ändern Sie den XML-Header (falls vorhanden) von `<?xml ... encoding="utf-16"?>` in `<?xml ... encoding="utf-8"?>`.

1. Speichern Sie die Datei mit einem neuen Namen und mit UTF-8-Codierung für die Ausgabe.

Mac-Benutzer können die Dateicodierung auch ändern, indem sie den XML-Header des Dokuments wie in Schritt 2 beschrieben aktualisieren und dann den folgenden Befehl auf dem Terminal ausführen:

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}


## Angepasstes Übersetzungsmodell löschen
{: #deleting-a-custom-model}

Verwenden Sie zum Löschen eines angepassten Übersetzungsmodells die Methode zum [Löschen von Modellen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/apidocs/language-translator#delete-model).

Mit dem folgenden Befehl wird das Übersetzungsmodell mit der Modell-ID `3e7dfdbe-f757-4150-afee-458e71eb93fb` gelöscht.

```curl
curl --user apikey:{apikey_value} --request DELETE "https://gateway.watsonplatform.net/language-translator/api/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: codeblock}

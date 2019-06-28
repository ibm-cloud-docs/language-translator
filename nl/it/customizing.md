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

# Personalizzazione del tuo modello
{: #customizing}

La maggior parte dei modelli di traduzione forniti in {{site.data.keyword.languagetranslatorshort}} può essere estesa per apprendere termini e frasi personalizzati oppure uno stile generale derivato dai tuoi dati di traduzione. Attieniti alle seguenti istruzioni per creare un tuo modello di traduzione personalizzato.
{: shortdesc}

## Prima di iniziare
{: #before-you-begin}

1. Assicurati che la tua istanza del servizio {{site.data.keyword.languagetranslatorshort}} sia in un piano di prezzi Advanced o Premium. I piani Lite e Standard non supportano la personalizzazione.
1. Trova un modello di base personalizzabile per la tua coppia di lingue. Ti servirà l'ID del modello di base per addestrare il tuo modello personalizzato.
    - Cerca nei modelli elencati nella pagina [Modelli di traduzione](/docs/services/language-translator?topic=language-translator-translation-models). Cerca il valore **true**" nella colonna **Personalizzabile** e assicurati che le lingue di **Origine** e **Destinazione** del modello corrispondano alla tua coppia di lingue.
    - In alternativa, puoi utilizzare il metodo API [List models ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/apidocs/language-translator#list-models) per cercare nei modelli in modo programmatico. Puoi filtrare i risultati in base alla lingua con i parametri `source` e `target`. 

## Passo 1: Crea i tuoi dati di addestramento
{: #create-your-training-data}

Il servizio richiede che i dati di addestramento vengano forniti nel [formato file TMX (Translation Memory Exchange)](#creating-tmx-files). Puoi archiviare fino a 10 personalizzazioni per ogni coppia di lingue in un'istanza del servizio. Il servizio supporta due tipi di richieste di personalizzazione. Puoi personalizzare un modello con un glossario forzato oppure con un corpus che contiene frasi parallele.

- Utilizza un [glossario forzato](#forced-glossary-customization) per forzare la traduzione in uno specifico modello di alcuni termini e frasi.
- Utilizza un [corpus parallelo](#parallel-corpus-customization) quando vuoi che il tuo modello personalizzato impari dai modelli di traduzione generali nei tuoi esempi. Quello che il tuo modello apprende da un corpus parallelo può migliorare i risultati della traduzione per il testo immesso su cui il modello non è stato addestrato. 

Dopo che hai creato i tuoi [file TMX (Translation Memory Exchange)](#creating-tmx-files), sei pronto ad addestrare il tuo modello.

## Passo 2: Addestra il tuo modello
{: #train-your-model}

Utilizza il metodo [Create model ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/apidocs/language-translator#create-model) per addestrare il tuo modello. Nella tua richiesta, specifica l'ID di un modello di base personalizzabile e i dati di addestramento nei parametri `forced_glossary` o `parallel_corpus`.

### Richiesta di esempio
{: #train-model-example-request}

La seguente richiesta di esempio utilizza un file di glossario forzato, _glossary.tmx_, per personalizzare il modello di base `en-es`. Vedi la sezione [Personalizzazione del glossario forzato](#forced-glossary) per un file TMX di glossario forzato di esempio.

```bash
curl --user apikey:{apikey} -X POST --form forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

La risposta API conterrà i dettagli sul tuo modello personalizzato, incluso il suo ID modello. Utilizza l'ID modello per controllare lo stato del tuo modello e per tradurre le frasi quando lo stato del modello diventa "available".

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

## Passo 3: Controlla lo stato del tuo modello
{: #check-model-status}

L'addestramento del modello potrebbe richiedere tanto un paio di minuti (per i glossari forzati) e tanto diverse ore (per corpus paralleli di grandi dimensioni), a seconda della quantità di dati di traduzione coinvolti. Per vedere se il tuo modello è disponibile, utilizza il metodo [Get model ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/apidocs/language-translator#get-model-details) e specifica l'ID modello che hai ricevuto nella risposta del servizio nel Passo 2. Puoi inoltre controllare lo stato di tutti i tuoi modelli con il metodo [List models ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/apidocs/language-translator#list-models).

L'attributo della risposta `status` descrive lo stato del modello nel processo di addestramento:

- `uploading`
- `uploaded`
- `dispatching`
- `queued`
- `training`
- `trained`
- `publishing`
- `available`

Quando lo stato del modello è `disponibile`, il tuo modello è pronto per essere utilizzato con la tua istanza del servizio. Se il tuo modello viene eliminato o se viene riscontrato un errore nel processo di addestramento, potresti visualizzare uno dei seguenti stati:

- `deleted`
- `error`

### Richiesta di esempio
{: #check-model-example-request}

Il seguente esempio ottiene informazioni dal modello identificato dall'ID modello `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```bash
curl --user apikey:{apikey_value} "https://gateway.watsonplatform.net/language-translator/api/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## Passo 4: Traduci il testo con il tuo modello personalizzato
{: #translate-text}

Per utilizzare il tuo modello personalizzato, specifica il testo che vuoi tradurre e l'ID del modello personalizzato nel metodo [Translate ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/apidocs/language-translator#translate).

### Richiesta di esempio
{: #translate-text-example-request}

Il seguente esempio traduce il testo con il modello personalizzato identificato dall'ID modello `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data '{"text":"Hello","model_id":"96221b69-8e46-42e4-a3c1-808e17c787ca"}' https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}


## Personalizzazione del glossario forzato
{: #forced-glossary-customization}

Utilizza un **glossario forzato** per impostare le traduzioni obbligatorie per termini e frasi specifici. Se desideri un controllo specifico sulla modalità di funzionamento della traduzione, utilizza un glossario forzato.

- Formato dei dati di addestramento: [TMX](#creating-tmx-files) (con codifica UTF-8)
- Dimensione massima del file: 10 MB
- Puoi applicare un glossario forzato a un modello di base oppure a un modello che è stato personalizzato con un corpus parallelo
- Limita un singolo glossario forzato per ogni modello

Gli esempi di glossario forzato sono sensibili a maiuscole/minuscole; assicurati quindi che i tuoi dati di addestramento riflettano le maiuscole/minuscole del contenuto che verrà riscontrato dalla tua applicazione.
{: tip}

### Esempio di glossario forzato
{: #forced-glossary-example}

Il seguente esempio mostra un file TMX con due coppie di traduzione. La prima coppia forza la conservazione di "international business machines" in inglese durante la traduzione. Questo tipo di traduzione forzata può essere utile se vuoi conservare dei nomi di azienda di cui sono state indicate in modo non corretto le maiuscole/minuscole in comunicazioni non formali. La seconda coppia forza il modello è utilizzare sempre "brevet" quando si traduce "patent".

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



## Personalizzazione del corpus parallelo
{: #parallel-corpus-customization}

Utilizza un **corpus parallelo** per fornire ulteriori traduzioni da cui il modello di base può apprendere. Ciò aiuta ad adottare il modello di base per uno specifico dominio. Il modo in cui il modello personalizzato risultante traduce il testo dipende dalla comprensione combinata, da parte del modello, del corpus parallelo e del modello di base.

- Formato dei dati di addestramento: [TMX](#creating-tmx-files) (con codifica UTF-8)
- Lunghezza massima delle coppie di traduzione: 80 parole di origine
- Numero minimo di coppie di traduzione: 5.000
- Dimensione massima del file: 250 MB
- Puoi inoltrare più file di corpus parallelo ripetendo il parametro di modulo in più parti `parallel_corpus` a condizione che la dimensione cumulativa non superi i 250 MB.

### Esempio di corpus parallelo
{: #parallel-corpus-example}

Il seguente è un piccolo frammento di un corpus parallelo dall'inglese al francese che era stato scaricato dalla [raccolta MultiUN ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://opus.nlpl.eu/MultiUN.php), disponibile nel sito web di corpus parallelo aperto OPUS. Puoi scaricare una versione compressa dell'intero file TMX [qui ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz).


```xml
<?xml version="1.0" encoding="UTF-8" ?>
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

I miglioramenti generali dalla personalizzazione del corpus parallelo sono meno prevedibili rispetto ai risultati obbligatori che si possono ottenere dalla personalizzazione del glossario forzato. Considera ad esempio la seguente unità di traduzione dal corpus parallelo di esempio (righe 172-175).

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

Se traduci "55/102. Globalization and its impact on the full enjoyment of all human rights" con il modello `en-fr` di base, il servizio risponde con la seguente traduzione:

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

Quando la stessa frase immessa viene tradotta da un modello personalizzato addestrato con il corpus di esempio, il servizio risponde con una traduzione differente che non è identica alla traduzione di esempio fornita nei dati di traduzione.

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- Il modello personalizzato traduce "the full enjoyment" come "le plein exercice" invece di "la pleine jouissance". La probabile spiegazione per questa deviazione dalla modalità di funzionamento del modello di base è che ci sono molti esempi nel corpus in cui "enjoyment" è tradotto come "exercice".
- Il modello personalizzato traduce "of all human rights" come "de tous les droits de l'homme" invece di riprodurre il risultato dall'unità di traduzione "des droits de l'homme". Questa modalità di funzionamento riflette la comprensione combinata, da parte del modello addestrato, del modello di base e di tutti gli esempi di traduzione correlati a "of all human rights" dal corpus parallelo.

In alcuni casi, potrebbe sembrare che un modello personalizzato addestrato con un corpus parallelo stia ignorando uno specifico esempio da te fornito. In tali casi, prova a cercare nei tuoi dati di addestramento delle altre frasi che è possibile stiano influenzando la modalità di funzionamento della traduzione oppure valuta l'utilizzo di un glossario forzato se vuoi controllare una specifica traduzione.


## Creazione di file TMX
{: #creating-tmx-files}

Per fornire un glossario o un corpus di termini per la formazione del servizio {{site.data.keyword.languagetranslatorshort}}, crea un documento codificato UTF-8 valido che sia conforme alla specifica TMX (Translation Memory Exchange) [versione 1.4 ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ttt.org/oscarStandards/tmx/){: new_window}. TMX è una specifica XML progettata per gli strumenti machine translation. Il seguente esempio è un file di glossario in formato TMX con due unità di traduzione (elementi `<tu>`):

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

Ogni coppia di termine e traduzione deve essere racchiusa tra tag `<tu>`:

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

L'attributo `xml:lang` nella tag `<tuv>` identifica la lingua in cui viene espresso un termine, mentre la tag `<seg>` contiene il termine o la traduzione.

Il servizio {{site.data.keyword.languagetranslatorshort}} utilizza solo gli elementi `<tu>`, `<tuv>` e `<seg>`. Tutti gli altri elementi nell'esempio sono obbligatori per creare un file TMX valido o sono informativi, ma non utilizzati nel servizio.



### Utilizzo dell'esempio come un template
{: #using-the-example-template}

Per utilizzare l'esempio fornito come un template per il tuo proprio glossario o corpus, completa la seguente procedura:

1. Copia e incolla l'esempio in un editor di testo.

2. Modifica l'attributo `srclang` della tag `<header>` nel [codice lingua ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} della lingua di origine che utilizza il tuo corpus parallelo o glossario.

3. Modifica l'attributo `xml:lang` delle tag `<tuv>` per correggere il [codice lingua ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} di ogni termine o traduzione.

4. Salva il documento con l'estensione `.tmx` e codifica UTF-8.

### Modifica di un file TMX per la codifica UTF-8
{: #changing-tmx-file-to-utf-8}

Puoi utilizzare vari strumenti per creare o generare i file TMX. Spesso, i file TMX generati sono per impostazione predefinita codificati UTF-16. Il servizio {{site.data.keyword.languagetranslatorshort}} accetta solo file TMX codificati UTF-8. Per modificare la codifica di un file TMX, completa la seguente procedura:

1. Apri il file TMX in un editor di testo.

1. Modifica l'intestazione XML (se presente) da `<?xml ... encoding="utf-16"?>` a `<?xml ... encoding="utf-8"?>`.

1. Salva il file con un nuovo nome e con l'output di codifica UTF-8.

Gli utenti Mac possono anche modificare la codifica del file aggiornando l'intestazione XML del documento come descritto nel passo 2 e quindi eseguire il seguente comando nel terminale:

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}


## Eliminazione di un modello di traduzione personalizzato
{: #deleting-a-custom-model}

Per eliminare un modello di traduzione personalizzato, utilizza il metodo [Delete model ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/apidocs/language-translator#delete-model).

Il seguente comando elimina il modello di traduzione con l'ID modello `3e7dfdbe-f757-4150-afee-458e71eb93fb`.

```curl
curl --user apikey:{apikey_value} --request DELETE "https://gateway.watsonplatform.net/language-translator/api/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: codeblock}

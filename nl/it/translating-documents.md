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

# Traduzione di documenti (Beta)
{: #document-translator-tutorial}


Traduci i file da una lingua a un'altra conservando il formato originale. Possono essere tradotti più di 12 formati file differenti, compresi MS Office, Open Office e PDF.
{:shortdesc}

## Prima di iniziare
{: #prerequisites}

- [Introduzione](/docs/services/language-translator?topic=language-translator-getting-started) a {{site.data.keyword.languagetranslatorshort}}. Ti serviranno le tue credenziali del servizio {{site.data.keyword.languagetranslatorshort}} (`apikey` e `url`).
- Assicurati che il documento che vuoi tradurre soddisfi i seguenti requisiti:
    - Dimensione massima del file: **20 MB**
    - [Formati file supportati](#supported-file-formats)
    - [Modelli di traduzione supportati](/docs/services/language-translator?topic=language-translator-translation-models)

## Passo 1: Inoltra un documento da tradurre
{: #submit-document-to-translate}

La seguente richiesta di esempio inoltra un file di esempio *curriculum.pdf* al servizio e lo traduce dall'inglese al francese. Sostituisci `{apikey}` e `{url}` con le tue credenziali del servizio e sostituisci `curriculum.pdf` con un percorso relativo al tuo file.

Richiesta di esempio:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Per tradurre un documento con un [modello personalizzato](/docs/services/language-translator?topic=language-translator-customizing), utilizza il parametro **model_id**. La seguente richiesta traduce il documento con il modello personalizzato identificato dall'ID modello `96221b69-8e46-42e4-a3c1-808e17c787ca`.

Richiesta di esempio:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
{url}/v3/documents?version=2018-05-01
```
{: pre}


Una richiesta eseguita correttamente restituirà un `document_id` nella risposta.


Risposta di esempio:
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

## Passo 2: Controlla lo stato della traduzione
{: #check-translation-status}

Dopo che hai inoltrato un documento per la traduzione, puoi controllare lo stato della traduzione per appurare quando è disponibile per il download il documento tradotto. La seguente richiesta di esempio controlla lo stato della traduzione del documento con l'ID `bae02796-0d28-435c-9115-888359fdde62`. 

Richiesta di esempio:
```bash
curl -X GET \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Risposta di esempio:
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

Quando lo stato (`status`) nella risposta indica una condizione di disponibilità (`available`), il documento tradotto è pronto per il download.

## Passo 3: Scarica il documento tradotto
{: #download-translated-document}

La seguente richiesta di esempio salva il documento tradotto con l'ID documento `bae02796-0d28-435c-9115-888359fdde62` nel file *curriculum-fr.pdf*. 

Richiesta di esempio:
```bash
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01
```
{: pre}

## Passo 4: Traduci un documento precedentemente inoltrato
{: #translate-document-by-reference}

La seguente richiesta di esempio fa riferimento al file *curriculum.pdf* in inglese originale con l'ID documento (`document_id`) `bae02796-0d28-435c-9115-888359fdde62` e lo traduce in portoghese.

Richiesta di esempio:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Risposta di esempio:
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

La risposta contiene un nuovo ID documento (`document_id`). Ripeti i passi due e tre con il tuo nuovo ID documento (`document_id`) per controllare lo stato della traduzione e per scaricare il file tradotto una volta che è disponibile.

## Passo 5: Elimina i documenti
{: #delete-documents}

I documenti originali e gli eventuali documenti tradotti associati vengono eliminati automaticamente dopo che non sono stati utilizzati per un certo periodo di tempo. Vedi [Sicurezza delle informazioni](/docs/services/language-translator?topic=language-translator-information-security) per ulteriori dettagli.
{: tip}

Per eliminare i documenti in modo manuale, utilizza il metodo **Delete document**. In questa esercitazione, il file *curriculum.pdf* in inglese è stato coinvolto in due traduzioni e quindi sono necessarie due richieste per eliminare tutte le copie del documento originale.

Elimina l'inoltro originale di *curriculum.pdf* e la traduzione in francese:
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Elimina il duplicato del file *curriculum.pdf* e la traduzione in portoghese.
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01
```
{: pre}

## Formati file supportati
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
- Altri formati
    - PDF: `.pdf`
    - HTML: `.htm`, `.html`
    - XML: `.xml`
    - JSON: `.json` (vengono tradotti i valori con tipo `string` o `string array`)
    - Testo: `.txt`

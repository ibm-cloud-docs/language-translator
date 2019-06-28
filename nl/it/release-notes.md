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

# Note sulla release

Sono disponibili le seguenti nuove funzioni e modifiche per il servizio.
{: shortdesc}

## Nuovo processo di autenticazione API
{: #iam-auth-process }

Il servizio {{site.data.keyword.languagetranslatorshort}} dispone di un nuovo processo di autenticazione API per le istanze del servizio che sono ospitate nelle seguenti ubicazioni:

- Dallas a partire dal 15 giugno 2018
- Francoforte a partire dal 15 giugno 2018
- Londra
- Sydney a partire dal 12 giugno 2018
- Tokyo
- Washington, DC a partire dal 12 giugno 2018

{{site.data.keyword.cloud_notm}} sta eseguendo la migrazione all'autenticazione IAM (Identity and Access Management) basata sui token. Con alcune istanze del servizio, esegui l'autenticazione presso l'API utilizzando IAM.

- Per le _nuove_ istanze del servizio create nelle ubicazioni indicate in precedenza, utilizzi IAM per l'autenticazione. Puoi passare un token di connessione o una chiave API. I token supportano le richieste autenticate senza incorporare le credenziali del servizio in ogni chiamata. Le chiavi API utilizzano l'autenticazione di base.

    Quando utilizzi uno degli SDK Watson, puoi passare la chiave API e lasciare che l'SDK gestisca il ciclo di vita dei token. Per ulteriori informazioni ed esempi, vedi [Autenticazione ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/apidocs/language-translator#authentication){: new_window} nella guida di riferimento API.
- Per le istanze del servizio _esistenti_ che hai creato prima della data indicata, continui a eseguire l'autenticazione fornendo il nome utente e la password per l'istanza del servizio. Alla fine dovrai eseguire la migrazione di queste istanze del servizio all'autenticazione IAM. Verranno forniti degli aggiornamenti sul processo e le date di migrazione. Per ulteriori informazioni sulla migrazione, vedi [Migrazione di istanze del servizio Cloud Foundry a un gruppo di risorse](/docs/resources?topic=resources-migrate#migrate).

Per appurare quale sia l'autenticazione da utilizzare, visualizza le credenziali del servizio facendo clic sull'istanza del servizio nella [pagina delle risorse di {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com/resources){: new_window}.

## Controllo delle versioni dell'API del servizio
{: shortdesc}

Le richieste API in {{site.data.keyword.languagetranslatorshort}} v3 richiedono un parametro di versione che utilizza una data nel formato `version=YYYY-MM-DD`. Ogni volta che modifichiamo l'API in modo incompatibile con le versioni precedenti, rilasciamo una nuova versione secondaria dell'API. 

Invia il parametro di versione con ogni richiesta API. Il servizio utilizza la versione API per la data che specifichi oppure la versione più recente prima di tale data. Non impostare come predefinita la data corrente. Specifica invece una data che corrisponda a una versione compatibile con la tua applicazione e non modificarla finché l'applicazione non è pronta per una versione successiva.

La versione corrente è `2018-05-01`.

## 14 giugno 2019
{: #14-june-2019}

Dei nuovi [modelli di traduzione](/docs/services/language-translator?topic=language-translator-translation-models) sono ora disponibili per l'inglese e il greco.
- Dall'inglese al greco (en-el)
- Dal greco all'inglese (el-en)

## 13 giugno 2019
{: #13-june-2019}

Dei nuovi [modelli di traduzione](/docs/services/language-translator?topic=language-translator-translation-models) sono ora disponibili per l'inglese e l'ebraico.
- Dall'inglese all'ebraico (en-he)
- Dall'ebraico all'inglese (he-en)

## 21 marzo 2019
{: #21-march-2019}

A partire dal 21 marzo 2019, vedrai solo le informazioni sulle credenziali del servizio associate al ruolo che è stato assegnato al tuo account {{site.data.keyword.cloud_notm}}. Ad esempio, se ti è stato assegnato un ruolo di lettore (`reader`), i livelli di scrittore (`writer`) o superiore di credenziali del servizio non saranno visibili.

Questa modifica non ha alcun effetto sull'accesso API per gli utenti o le applicazioni con le credenziali di chiave di servizio esistenti. È interessata solo la visualizzazione delle credenziali in {{site.data.keyword.cloud_notm}}.

Per ulteriori informazioni sulle chiavi di servizio e i ruoli utente, vedi [Chiavi API del servizio IAM](/docs/services/watson?topic=watson-api-key-bp#api-key-bp).

## 14 dicembre 2018
{: #14-december-2018}

- Puoi ora creare delle istanze del servizio {{site.data.keyword.languagetranslatorshort}} nell'ubicazione di Londra di {{site.data.keyword.cloud_notm}}. 

## 16 novembre 2018
{: #16-november-2018}

- [La traduzione di documenti (Beta)](/docs/services/language-translator?topic=language-translator-translating-documents) è ora disponibile tramite i nuovi endpoint API. Inoltra un documento Microsoft Office, PDF o un altro documento con un formato file supportato; {{site.data.keyword.languagetranslatorshort}} fornirà una copia tradotta che conserva la formattazione originale.
  - [I formati file supportati](/docs/services/language-translator?topic=language-translator-translating-documents#supported-file-types) includono `.doc`, `.ppt`, `.pdf` e altri ancora.

- Sono ora disponibili dei nuovi [modelli di traduzione](/docs/services/language-translator?topic=language-translator-translation-models) per l'ungherese.
  - Dall'ungherese all'inglese (hu-en)
  - Dall'inglese all'ungherese (en-hu)

## 8 novembre 2018
{: #8-november-2018}

- Puoi ora creare delle istanze del servizio {{site.data.keyword.languagetranslatorshort}} nell'ubicazione di Tokyo di {{site.data.keyword.cloud_notm}}.

## 9 agosto 2018
{: #9-august-2018}

Sono ora disponibili dei nuovi [modelli di traduzione](/docs/services/language-translator?topic=language-translator-translation-models) per il norvegese (Bokmål).
  - Dal norvegese (Bokmål) all'inglese (nb-en)
  - Dall'inglese al norvegese (Bokmål) (en-nb)

## 27 giugno 2018
{: #27-june-2018}

Sono ora disponibili dei nuovi [modelli di traduzione](/docs/services/language-translator?topic=language-translator-translation-models) che presentano sei nuove lingue:
  - Catalano
    - Dal catalano allo spagnolo (ca-es)
    - Dallo spagnolo al catalano (es-ca)
  - Ceco
    - Dal ceco all'inglese (cs-en)
    - Dall'inglese al ceco (en-cs)
  - Danese
    - Dal danese all'inglese (da-en)
    - Dall'inglese al danese (en-da)
  - Finlandese
    - Dal finlandese all'inglese (fi-en)
    - Dall'inglese al finlandese (en-fi)
  - Hindi
    - Dall'hindi all'inglese (hi-en)
    - Dall'inglese all'hindi (en-hi)
  - Svedese
    - Dallo svedese all'inglese (sv-en)
    - Dall'inglese allo svedese (en-sv)
  

## 15 giugno 2018
{: #15-june-2018}

A partire dal 15 giugno 2018, le nuove istanze del servizio create nelle regioni Germania e Stati Uniti Sud utilizzano l'[autenticazione IAM (Identity and Access Management)](#iam-auth-process).

Le nuove istanze del servizio che crei in Germania e Stati Uniti Sud non saranno compatibili con Language Translator v2. Se utilizzi Language Translator v2 e intendi utilizzare delle nuove istanze del servizio nella tua applicazione, dovrai [eseguire la migrazione all'API v3](/docs/services/language-translator?topic=language-translator-migrating).

## 12 giugno 2018
{: #12-june-2018}

{{site.data.keyword.languagetranslatorshort}} v3 è ora disponibile. L'API Language Translator v2 non sarà più disponibile a partire dal 31 luglio 2018. Per avvalerti dei più recenti miglioramenti del servizio, esegui la migrazione all'API v3. Per ulteriori informazioni, visualizza la pagina [Migrazione a Language Translator v3](/docs/services/language-translator?topic=language-translator-migrating).

### Novità nella v3
{: #whats-new}

-  L'API v3 di {{site.data.keyword.languagetranslatorshort}} viene fornita con modelli NMT (**Neural Machine Translation**) che offrono risultati della traduzione notevolmente migliorati. Tutti i modelli NMT sono ora disponibili per la personalizzazione.
-  Utilizza i modelli personalizzati come modelli di base per la personalizzazione del glossario forzato.
-  API v3 è un sottoinsieme tutto JSON semplificato dell'API v2 che è stata ritirata.
-  Introduce le date della versione API per dare agli sviluppatori la libertà di adottare le future modifiche dell'API secondo il loro ritmo.

### Modifiche sostanziali
{: #breaking-changes}

- Data della versione obbligatoria per tutti gli endpoint API: le richieste API v3 richiedono un parametro di query della data della versione nel formato `version=YYYY-MM-DD`. La versione API più recente è `version=2018-05-01`.
- API semplificata:
  - I metodi **Translate** e **Identify** non offrono l'opzione di restituire risposte in testo semplice in v3. I metodi restituiscono solo risposte JSON.
  - I metodi `GET /translate` e `GET /identify` non sono supportati nella v3. Utilizza invece i metodi `POST /translate` e `POST /identify`. 
- La personalizzazione del corpus monolingue non è supportata nella v3.
- La creazione di modelli personalizzati sia con un corpus parallelo che un glossario forzato dove ora essere eseguita in due chiamate API. Per prima cosa, personalizza il modello con un corpus parallelo. Dopo che il modello personalizzato ha completato l'addestramento, personalizzalo di nuovo con il glossario forzato. Questa modifica ti consente di utilizzare un modello personalizzato addestrato con un corpus parallelo come una base per la personalizzazione del glossario forzato.
- I modelli di dominio di brevetti e conversazioni specializzati non sono disponibili nell'API v3. La qualità della traduzione fornita dai modelli NMT nei domini relativi a brevetti e conversazioni è generalmente migliorata rispetto ai modelli specializzati meno recenti.
- Le chiavi dell'oggetto di errore sono state rinominate in modo che siano congruenti con altre API Watson. `error_code` è stato rinominato come `code` e `error_message` è stato rinominato come `error`.

### Autenticazione IAM

A partire dal 12 giugno 2018, le nuove istanze del servizio create nelle regioni Sydney e Stati Uniti Est utilizzano l'[autenticazione IAM (Identity and Access Management)](#iam-auth-process).

## 12 gennaio 2018
{: #12-january-2018}

Sono disponibili nuovi nodelli NMT (Neural Machine Translation) in anteprima. Puoi provare i modelli NMT per le seguenti coppie di lingue. 

- Da o verso l'inglese: arabo, cinese, olandese, francese, tedesco, italiano, giapponese, coreano, polacco, portoghese (brasiliano), russo, spagnolo e turco.
- Da e verso il francese: tedesco, spagnolo
- Da e verso il tedesco: italiano

*I modelli NMT e la sintassi per utilizzarli sono soggetti a modifiche durante il periodo di anteprima. Al momento, i modelli NMT non supportano la personalizzazione corpus. Sono supportati solo i glossari forzati.*

Per utilizzare un modello di anteprima NMT per la traduzione, specifica l'intestazione `X-Watson-Technology-Preview:2017-07-01` insieme ai codici carattere delle lingue di origine e di destinazione del modello che desideri utilizzare. Il seguente esempio mostra come tradurre dall'inglese allo spagnolo con un modello di anteprima NMT.

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}

Puoi guardare un [video dimostrativo su YouTube ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://youtu.be/L6ZC0QaUZ2k) che spiega come configurare {{site.data.keyword.languagetranslatorshort}} con l'anteprima NMT.


## 15 dicembre 2016
{: #15-december-2016}

Sono stati aggiunti ulteriori nuovi modelli di traduzione: verso l'inglese e dal giapponese

## 15 novembre 2016
{: #15-november-2016}

Lo strumento che era precedentemente disponibile per il servizio {{site.data.keyword.languagetranslatorshort}} non è più disponibile o supportato. 

Contatta il tuo rappresentante delle vendite o il supporto clienti per le informazioni su come utilizzare l'API {{site.data.keyword.languagetranslatorshort}} per eseguire le attività supportate dallo strumento {{site.data.keyword.languagetranslatorshort}}.

## 1 settembre 2016
{: #1-september-2016}

Il servizio IBM Watson&trade; Language Translation è stato ridenominato come il servizio {{site.data.keyword.languagetranslatorshort}}.

## 22 marzo 2016
{: #22-march-2016}

È stato aggiunto il supporto per ulteriori lingue: verso l'inglese e dall'italiano e verso lo spagnolo e dal francese.

## 3 dicembre 2015
{: #3-december-2015}

A partire dal 15 gennaio 2016, tutte le funzionalità di personalizzazione nel piano Standard sono state sospese. Le applicazioni che non utilizzano le funzioni di personalizzazione non hanno bisogno di essere modificate, poiché il piano Standard rimane attivo per tutte le chiamate API non correlate alla personalizzazione o ai modelli personalizzati. Per utilizzare le funzioni di personalizzazione GA (il piano Addestrabile) del servizio {{site.data.keyword.languagetranslatorshort}} con un'applicazione {{site.data.keyword.cloud}} che utilizza un'istanza precedente del servizio, completa la seguente procedura:

1.  Crea una nuova istanza Watson {{site.data.keyword.languagetranslatorshort}} e specifica il piano "Addestrabile" GA.
2.  Associa la nuova istanza "Addestrabile" del servizio alla tua applicazione in {{site.data.keyword.cloud_notm}}.
3.  Raccogli i dati che sono stati inizialmente utilizzati per creare i modelli personalizzati. Per ulteriori informazioni, consulta [Struttura dei dati di formazione](/docs/services/language-translator?topic=language-translator-customizing#structure).
4.  Carica i dati di formazione per creare i nuovi modelli personalizzati nell'istanza "Addestrabile". Per ulteriori informazioni, consulta [Formazione di un modello di traduzione personalizzato](/docs/services/language-translator?topic=language-translator-customizing#training).
5.  Nella tua applicazione, fai puntare il campo "IDModello" ai nuovi modelli personalizzati.
6.  Annulla l'associazione del servizio precedente alla tua applicazione in {{site.data.keyword.cloud_notm}} e quindi quindi eliminalo.

## 6 novembre 2015
{: #6-november-2015}

È stato rilasciato lo strumento beta {{site.data.keyword.languagetranslatorshort}}. Lo strumento è un'applicazione web che fornisce un'interfaccia utente grafica per gestire e formare i modelli per una più accurata traduzione automatica. Puoi creare i progetti, caricare i dati di formazione, formare i modelli personalizzati e tradurre il testo.

## 1 dicembre 2014
{: #1-december-2014}

Le API Machine Translator beta e Language Identification beta sono state aggiornate e combinate nell'API {{site.data.keyword.languagetranslatorshort}}. Per iniziare immediatamente ad utilizzare il nuovo servizio, comprendi e aggiorna il tuo codice in modo che rispecchi queste modifiche:

- **Nuovo parametro model\_id**: nell'API beta, hai definito il parametro `sid` per selezionare il modello da utilizzare per la traduzione. In questa versione, il parametro `sid` è stato ridenominato con `id_modello`. Per richiamare i valori consentiti `id_modello`, utilizza l'operazione `GET/language  translator/api/v2/models`. Ti viene restituito un elenco di tutti i modelli e i rispettivi valori corrispondenti `id_modello`.
- **Supporto coppia di lingue**: invece di selezionare un `id_modello`, puoi ora specificare una lingua di destinazione e di origine e il modello sarà impostato in modo predefinito sulla lingua formata nel dominio di novità generale.
- **Supporto corpo di richiesta JSON**: quando effettui una richiesta di traduzione POST, puoi ora eseguire la richiesta come un invio JSON. La formattazione JSON ti consente di inviare più paragrafi per la traduzione, invece di soltanto un'unica parte di testo nel formato di invio del modulo.
- **Supporto corpo di risposta JSON**: la richiesta di traduzione restituisce la formattazione JSON di supporto così come la formattazione di testo semplice. Il formato JSON permette il supporto per parole tradotte da restituire in più paragrafi invece di una sola parte di testo.
- **Supporto intestazione Accept**: l'intestazione Accept può ora essere utilizzata per definire il formato della risposta in tutte le operazioni (testo/semplice o applicazione/json).
- **Supporto identificazione lingua**: i metodi di identificazione della lingua sono stati aggiunti a questa API. Questo ti consente di identificare la lingua dei testi di immissione ed elencare tutte le lingue supportate che possono essere rilevate dall'API.

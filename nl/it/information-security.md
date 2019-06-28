---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-04"

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

# Sicurezza delle informazioni
{: #information-security}

IBM si impegna a offrire ai suoi clienti e partner soluzioni innovative per la privacy, la sicurezza e la governance dei dati.
{: shortdesc}

**Avviso:**
i clienti sono responsabili per la garanzia della propria conformità alle varie leggi e normative, incluso il Regolamento generale sulla protezione dei dati (GDPR) dell'Unione Europea. È responsabilità esclusiva dei clienti richiedere una consulenza legale qualificata per identificare e interpretare normative e regolamenti che potrebbero influenzare le attività di business dei clienti ed eventuali azioni che i clienti dovranno intraprendere per rispettare la conformità a tali normative e regolamenti. 

I prodotti, i servizi e le altre funzionalità qui descritti non sono adatti per tutte le situazioni dei clienti e potrebbero avere una disponibilità limitata. IBM non fornisce consulenza legale, contabile o di controllo né dichiara o garantisce che i propri servizi o prodotti assicureranno che i clienti siano conformi ad eventuali norme di legge o regolamentari. 

Se hai bisogno di richiedere il supporto GDPR per le risorse {{site.data.keyword.cloud}} {{site.data.keyword.watson}} che vengono create 

-   Nell'Unione Europea (EU), consulta [Richiesta di supporto per le risorse IBM Cloud Watson create nell'Unione Europea](/docs/services/watson/getting-started-gdpr-sar.html#request-EU).
-   Al di fuori dell'Unione Europea (EU), consulta [Richiesta di supporto per le risorse fuori dall'Unione Europea](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU).

## Regolamento generale sulla protezione dei dati (GDPR) dell'Unione Europea
{: #gdpr}

IBM si impegna a offrire ai nostri clienti e partner soluzioni innovative per la privacy, la sicurezza e la governance dei dati per assisterli nel loro percorso verso la conformità al GDPR. 

È possibile trovare ulteriori informazioni sul percorso di preparazione al GDPR e sulle nostre funzionalità e offerte GDPR che supportano il tuo percorso di conformità [qui ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](../../icons/launch-glyph.svg "Icona link esterno")](http://www.ibm.com/gdpr){: new_window}.

## Etichettatura ed eliminazione dei dati in Language Translator
{: #gdpr-in-service}

Il servizio {{site.data.keyword.languagetranslatorshort}} memorizza in cache in modo temporaneo i dati di traduzione dalle richieste di traduzione e conserva i dati di addestramento utilizzati per creare i modelli personalizzati.

### Dati e documenti di traduzione
{: #translation-data-and-documents}

Quando invii del testo a {{site.data.keyword.languagetranslatorshort}} nel metodo **Translate**, il servizio memorizza in cache il testo di origine e il risultato della traduzione per migliorare le prestazioni quando riceve lo stesso testo in richieste **Translate** successive. Il testo della traduzione memorizzato in cache viene eliminato solo dopo che non è stato utilizzato per un periodo di 15 giorni.

I documenti inoltrati al servizio per la traduzione tramite il metodo **Translate document** sono archiviati internamente per fornire il file tradotto e per supportare ulteriori richieste **Translate document** mediante riferimento al documento caricato originale. Il documento originale e gli eventuali documenti tradotti associati vengono eliminati solo dopo non essere stati utilizzati in successive richieste **Translate document** per un periodo di 15 giorni. Il metodo **Delete document** può essere utilizzato per eliminare i documenti prima del termine ultimo dell'eliminazione. 

I dati e i documenti di traduzione sono crittografati quando sono in transito e quando sono inattivi.

### Dati di addestramento del modello personalizzato
{: #custom-model-training-data}

Quando addestri un modello personalizzato, i dati di addestramento che utilizzi per creare il modello sono archiviati per fornirti il modello personalizzato. I dati di addestramento e i modelli personalizzati sono crittografati quando sono in transito e quando sono inattivi. I dati di addestramento crittografati persistono nell'archiviazione finché il modello non viene eliminato con il metodo **Delete model**.

I modelli personalizzati possono essere eliminati solo a livello del modello. I dati di componente utilizzati per creare un modello personalizzato non possono essere eliminati. Se utilizzi dati personali quando crei un modello personalizzato, è necessario creare un modello personalizzato separato per ciascun cliente e il nome (`name`) di modello etichettato per identificare il cliente in modo che possa essere eliminato, se richiesto. 

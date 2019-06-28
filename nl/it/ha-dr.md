---

copyright:
  years: 2019
lastupdated: "2019-03-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Alta disponibilità e ripristino di emergenza
{: #ha-dr}

{{site.data.keyword.languagetranslatorfull}} è altamente disponibile in più ubicazioni di {{site.data.keyword.cloud_notm}} (ad esempio Dallas e Washington, DC). Tuttavia, il ripristino da potenziali emergenze che influenza un'intera ubicazione richiede pianificazione e preparazione.
{: shortdesc}

Sei responsabile della comprensione della configurazione, della personalizzazione e dell'utilizzo del servizio. Sei anche responsabile di essere in grado di ricreare un'istanza del servizio in una nuova ubicazione e di ripristinare i dati in qualsiasi ubicazione. Vedi [Come garantisco nessun tempo di inattività? ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} per ulteriori informazioni.

## Alta disponibilità (HA)
{: #high-availability}

{{site.data.keyword.languagetranslatorshort}} supporta l'alta disponibilità senza un singolo punto di errore. Il servizio raggiunge l'alta disponibilità in modo automatico e trasparente utilizzando la funzione MZR (multi-zone region) fornita da {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} abilita più zone che non condividono un singolo punto di errore all'interno di una singola ubicazione. Fornisce anche il bilanciamento del carico automatico tra le zone all'interno di una regione.


## Ripristino di emergenza
{: #disaster-recovery}

In caso di errore irrecuperabile in una regione, completa la seguente procedura.

- Crea una nuova istanza del servizio {{site.data.keyword.languagetranslatorshort}}.
- Regola il tuo software applicativo per utilizzare il nuovo URL e le nuove credenziali dell'istanza del servizio.
- Crea dei nuovi modelli personalizzati per sostituire quelli che hai perso. Usa gli stessi glossari forzati e corpus paralleli che hai usato per creare i tuoi modelli personalizzati precedenti. Vedi [Personalizzazione del tuo modello](/docs/services/language-translator?topic=language-translator-customizing#customizing) per ulteriori informazioni sui modelli personalizzati.
  - Per prepararti per un ripristino rapido, archivia delle copie dei backup dei tuoi file di addestramento ogni volta che crei un modello. Puoi utilizzare i campi `name` e `model_id` dei tuoi modelli personalizzati insieme ai nomi dei tuoi file di addestramento per tenere traccia dei file che utilizzi per ciascun modello. 
- Regola il tuo software applicativo per utilizzare i nuovi modelli personalizzati.


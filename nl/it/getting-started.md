---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-04"

---
<!-- Attribute definitions -->
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Esercitazione introduttiva
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} ti consente di tradurre del testo in modo programmatico da una lingua a un'altra.
{:shortdesc}
{: hide-dashboard}

Questa esercitazione ti descrive i comandi per tradurre del testo dall'inglese allo spagnolo e per identificare la lingua di un esempio di testo.

## Prima di iniziare
{: #prerequisites}

- {: hide-dashboard} Crea un'istanza del servizio:
    1.  {: hide-dashboard}Vai alla pagina [{{site.data.keyword.languagetranslatorshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/catalog/services/language-translator){: new_window} nel catalogo {{site.data.keyword.Bluemix_notm}}.
    2.  Registrati per un account {{site.data.keyword.Bluemix_notm}} gratuito o accedi.
    3.  Fai clic su **Crea**.
- Copia le credenziali per autenticarti con la tua istanza del servizio:
    1.  Nella pagina **Gestisci**, fai clic su **Mostra** per visualizzare le tue credenziali.
    2.  Copia i valori `Chiave API` e `URL`.
- Assicurati di avere il comando `curl` :
    - Gli esempi utilizzano il comando `curl` per richiamare i metodi dell'interfaccia HTTP. Installa la versione per il tuo sistema operativo da [curl.haxx.se ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://curl.haxx.se/){: new_window}. Installa la versione che supporta il protocollo SSL (Secure Sockets Layer). Assicurati di includere il file binario installato nella tua variabile di ambiente `PATH`.

Questa esercitazione utilizza una chiave API per l'autenticazione. Per gli utilizzi di produzione, assicurati di riesaminare le [procedure ottimali](/docs/services/watson/apikey-bp.html#api-bp) della chiave API.
{: tip}

## Passo 1: traduci il testo
{: #translate-text}

Usa il seguente esempio per tradurre due frasi: "Hello, world!" e "How are you?" dall'inglese allo spagnolo. <span class="hide-dashboard">Sostituisci `{apikey}` e `{url}` con le tue credenziali del servizio.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## Passo 2: Identifica la lingua
{: #identify-language}

Utilizza il seguente esempio per identificare la lingua del testo. <span class="hide-dashboard">Sostituisci `{apikey}` e `{url}` con le tue credenziali del servizio.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## Passi successivi
{: #next-steps}

- Impara come [personalizzare](/docs/services/language-translator?topic=language-translator-customizing) {{site.data.keyword.languagetranslatorshort}} per lavorare per il tuo caso d'uso
- Prova la [traduzione di documenti (Beta)](/docs/services/language-translator?topic=language-translator-document-translator-tutorial)
- Visualizza la [guida di riferimento API](https://{DomainName}/apidocs/language-translator)
- Esplora le [applicazioni di esempio](/docs/services/language-translator?topic=language-translator-sample-applications)
- Visualizza le informazioni sul supporto linguistico:
    - [Modelli di traduzione](/docs/services/language-translator?topic=language-translator-translation-models)
    - [Lingue identificabili](/docs/services/language-translator?topic=language-translator-identifiable-languages)

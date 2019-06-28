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

# Tutoriel d'initiation
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} vous permet de traduire un texte, à l'aide d'un programme, d'une langue vers une autre.
{:shortdesc}
{: hide-dashboard}

Ce tutoriel vous guide lors de l'utilisation des commandes permettant de traduire de l'anglais vers l'espagnol et d'identifier la langue d'un échantillon de texte. 

## Avant de commencer
{: #prerequisites}

- {: hide-dashboard} Créez une instance du service :
    1.  {: hide-dashboard} Accédez à la page [{{site.data.keyword.languagetranslatorshort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/services/language-translator){: new_window} du catalogue {{site.data.keyword.Bluemix_notm}}.
    2.  Inscrivez-vous pour un compte {{site.data.keyword.Bluemix_notm}} gratuit ou connectez-vous.
    3.  Cliquez sur **Créer**.
- Copiez les données d'identification afin de vous authentifier auprès de votre instance de service :
    1.  Dans la page **Gérer**, cliquez sur **Afficher** pour afficher vos données d'identification.
    2.  Copiez les valeurs des zones `Clé d'API` et `URL`. 
- Assurez-vous que la commande `curl` est disponible :
    - Les exemples utilisent la commande `curl` pour appeler les méthodes de l'interface HTTP. Installez la version de votre système d'exploitation à partir du site [curl.haxx.se ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://curl.haxx.se/){: new_window}. Installez la version compatible avec le protocole SSL (Secure Sockets Layer). Veillez à inclure le fichier binaire installé indiqué dans votre variable d'environnement `PATH`.

Ce tutoriel utilise une clé d'interface de programmation (API) pour l'authentification. Pour une utilisation en production, veillez à étudier les [pratiques recommandées](/docs/services/watson/apikey-bp.html#api-bp) en matière de clé d'API.
{: tip}

## Etape 1 : Traduisez le texte
{: #translate-text}

Utilisez l'exemple suivant pour traduire deux phrases, "Hello, world!" et "How are you?" de l'anglais vers l'espagnol. <span class="hide-dashboard">Remplacez `{apikey}` et `{url}` par vos données d'identification de service.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## Etape 2 : Identifiez la langue
{: #identify-language}

Utilisez l'exemple suivant pour identifier la langue du texte. <span class="hide-dashboard">Remplacez `{apikey}` et `{url}` par vos données d'identification de service.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## Etapes suivantes
{: #next-steps}

- Apprenez à [personnaliser](/docs/services/language-translator?topic=language-translator-customizing) {{site.data.keyword.languagetranslatorshort}} afin de l'adapter à votre cas d'utilisation
- Essayez [Traduction de documents (Bêta)](/docs/services/language-translator?topic=language-translator-document-translator-tutorial)
- Affichez la [référence d'API](https://{DomainName}/apidocs/language-translator)
- Explorez les [exemples d'application](/docs/services/language-translator?topic=language-translator-sample-applications)
- Consultez les informations de support de langue :
    - [Modèles de traduction](/docs/services/language-translator?topic=language-translator-translation-models)
    - [Langues identifiables](/docs/services/language-translator?topic=language-translator-identifiable-languages)

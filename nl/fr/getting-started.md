---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

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

# Tutoriel d'initiation
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} vous permet de traduire à l'aide d'un programme un texte dans un contexte lié à l'actualité, des conversations ou des brevets. Ce tutoriel vous guide lors de l'utilisation des commandes permettant de traduire un exemple de contenu de l'anglais vers l'espagnol et lors du choix du domaine.
{:shortdesc}

## Avant de commencer 
{: #prerequisites}

- Créez une instance du service :
    - {: download} Si vous lisez ceci, vous avez créé votre instance de service. Il vous faut maintenant obtenir vos données d'identification.
    - Créez un projet à partir d'un service :
        1.  Accédez à la page {{site.data.keyword.watson}} Developer Console [Services ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Sélectionnez {{site.data.keyword.languagetranslatorshort}}, cliquez sur **Add Services**, puis inscrivez-vous afin de recevoir un compte {{site.data.keyword.Bluemix_notm}} gratuit ou connectez-vous. 
        1.  Entrez `language-tutorial` comme nom de projet et cliquez sur **Créer un projet**.
- Copiez les données d'identification afin de vous authentifier auprès de votre instance de service : 
    - {: download} Depuis le tableau de bord du service (affiché) :
        1.  Cliquez sur l'onglet **Données d'identification pour le service**. 
        1.  Cliquez sur **Afficher les données d'identification** sous **Actions**.
        1.  Copiez les valeurs `username`, `password` et `url`.
        {: download}
    - Depuis votre projet **language-tutorial** dans Developer Console, copiez les valeurs `username`, `password` et `url` de `"language_translator"` à partir de la section **Credentials**.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Si vous utilisez {{site.data.keyword.Bluemix_dedicated_notm}}, créez votre instance de service à partir de la page [{{site.data.keyword.languagetranslatorshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/catalog/services/language-translator/){: new_window} du catalogue. Pour savoir comment trouver vos données d'identification du service, voir
[Données d'identification de service pour les services Watson![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Etape 1 : Traduisez le texte
{: #translate-text}

Utilisez l'exemple suivant pour traduire "Hello, world!" de l'anglais vers l'espagnol. Remplacez `{username}` et `{password}` par les données d'identification du service que vous avez copiées à l'étape précédente.

```bash
curl -X POST --user {username}:{password} --header "Accept: application/json" --data "{\"text\":\"Hello, world\",\"source\":\"en\",\"target\":\"es\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{:codeblock}

Une prévisualisation des nouveaux modèles NMT (Neural Machine Translation) qui améliorent la qualité des traductions est désormais disponible. Pour plus de détails, consultez les [notes sur l'édition](release-notes.html#12-january-2018).
{: tip}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  version: 'v2',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
});
language_translator.translate({
    text: 'Hello, world!',
    source: 'en',
    target: 'es'
  },
  function(err, translation) {
    if (err)
      console.log(err)
    else
      console.log(translation);
});
```
{:node}
{:codeblock} -->

<!-- ```java
LanguageTranslator service = new LanguageTranslator();
service.setUsernameAndPassword("username","password");

TranslationResult result = service.translate("Hello, world!", "en", "es");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
    username="username",
    password="password")

translation = language_translator.translate(
    text="Hello, world!",
    source="en",
    target="es"
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->


## Etape 2 : Essayez un modèle spécifique du domaine
{: #specify-model}

{{site.data.keyword.languagetranslatorshort}} est doté de modèles spécialisés dans les domaines des actualités, des conversations et des brevets. Lorsque vous indiquez les langues `source` et `target` à l'étape 2, le service utilise par défaut le modèle du domaine des actualités pour ce chemin de traduction. Si vous souhaitez utiliser un modèle propre à un domaine, indiquez le `model_id` des langues `source` et `target`. Vous pouvez également faire appel à un [modèle personnalisé](customizing.html) si vous en avez créé un. 

_Les modèles spécifiques d'un domaine ne sont pas pris en charge dans les demandes contenant l'[en-tête de prévisualisation NMT](release-notes.html#12-january-2018)._

Dans l'exemple suivant, "Hey world, whats up?" est traduit à l'aide du modèle conversationnel de l'anglais vers l'espagnol. Remplacez `{username}` et `{password}` par vos informations :

```bash
curl -X POST --user {username}:{password} --header "Content-Type: application/json" --header "Accept: application/json" --data "{\"text\":\"Hey world, whats up?\",\"model_id\":\"en-es-conversational\"}" "https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{:codeblock}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
  version: 'v2',
});
language_translator.translate({
    text: 'Hey, world! What's up?',
    model_id: 'en-es-conversational'
  },
  function(err, translation) {
    if (err)
      console.log(err)
    else
      console.log(translation);
});
```
{:node}
{:codeblock} -->

<!-- ```java
LanguageTranslator service = new LanguageTranslator();
service.setUsernameAndPassword("username","password");

TranslationResult result = service.translate("Hey, world! What's up?", "en-es-conversational");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```python
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
  username="username",
  password="password"
)

translation = language_translator.translate(
  text="Hey, world! What's up?",
  model_id="en-es-conversational"
)
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->

Vous pouvez utiliser la méthode [List models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models){: new_window} afin d'afficher les modèles disponibles pour votre instance de service.
{:tip}

## Etapes suivantes
{: #next-steps}

- Apprenez à [personnaliser](/docs/services/language-translator/customizing.html) {{site.data.keyword.languagetranslatorshort}} afin de l'adapter à votre cas d'utilisation. 
- Affichez la
[référence d'API ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){:new_window}.
- Interagissez avec l'API dans [API Explorer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){:new_window}.
- Essayez le [modèle d'application Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/language-translator-nodejs){:new_window}.

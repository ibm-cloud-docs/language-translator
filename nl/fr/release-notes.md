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

# Notes sur l'édition

Les nouvelles fonctions et modifications apportées au service
ci-après sont disponibles.
{: shortdesc}

## 12 janvier 2018
{: #12-january-2018}

De nouveaux modèles NMT (Neural Machine Translation) sont disponibles à la prévisualisation. Vous pouvez essayer les modèles NMT pour les paires de langues suivantes:  

- Anglais vers et depuis : arabe, chinois, néerlandais, français, allemand, italien, japonais, coréen, polonais, portugais (Brésil), russe, espagnol et turc 
- Français vers et depuis : allemand, espagnol
- Allemand vers et depuis : italien

*Les modèles NMT et leur syntaxe d'utilisation sont sujets à modification pendant la période de prévisualisation. A l'heure actuelle, les modèles NMT ne prennent pas en charge la personnalisation de corpus. Seule la personnalisation du glossaire forcé est prise en charge.*

Si vous voulez utiliser un modèle NMT en prévisualisation pour effectuer une traduction, indiquez l'en-tête `X-Watson-Technology-Preview:2017-07-01` avec les codes caractères des langues source et cible du modèle souhaité. L'exemple suivant indique comment traduire de l'anglais vers l'espagnol avec un modèle NMT en prévisualisation.

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}


## 15 décembre 2016
{: #15-december-2016}

Des modèles de traduction supplémentaires liés aux actualités ont été ajoutés : l'anglais vers et depuis le japonais. 

## 15 novembre 2016
{: #15-november-2016}

Les outils précédemment disponibles pour le service {{site.data.keyword.languagetranslatorshort}} ne sont plus disponibles ou ne sont plus pris en charge.  

Contactez votre ingénieur commercial ou le support technique pour avoir davantage d'informations sur l'utilisation de l'API {{site.data.keyword.languagetranslatorshort}} afin d'effectuer les tâches prises en charge par l'outil {{site.data.keyword.languagetranslatorshort}}.

## 1er septembre 2016
{: #1-september-2016}

Le service IBM Watson&trade; Language Translation a été renommé en service {{site.data.keyword.languagetranslatorshort}}.

## 22 mars 2016
{: #22-march-2016}

La prise en charge des langues supplémentaires suivantes a été ajoutée : l'anglais vers depuis l'italien et l'espagnol vers et depuis le français. 

## 3 décembre 2015
{: #3-december-2015}

Depuis le 15 janvier 2016, toutes les fonctions de personnalisation du plan Standard ne sont plus suivies. Il n'est pas nécessaire de modifier les applications qui n'utilisent pas de fonctions de personnalisation car le plan Standard reste actif pour tous les appels d'API qui ne sont pas liés à la personnalisation ou à des modèles personnalisés. Si vous souhaitez employer les fonctions de personnalisation de la GA (plan Trainable) du service {{site.data.keyword.languagetranslatorshort}} avec une application {{site.data.keyword.cloud}} qui utilise une instance antérieure du service, procédez comme suit :

1.  Créez une nouvelle instance Watson {{site.data.keyword.languagetranslatorshort}} et indiquez le plan de GA "Trainable".
1.  Liez la nouvelle instance "Trainable" du service à votre application dans {{site.data.keyword.cloud_notm}}.
1.  Regroupez les données utilisées lors de la création initiale des modèles personnalisés. Pour plus d'informations, voir [Structure des données d'entraînement](/docs/services/language-translator/customizing.html#structure).
1.  Téléchargez les données d'entraînement pour créer de nouveaux modèles personnalisés sur l'instance "Trainable". Pour plus d'informations, voir [Entraînement d'un modèle de traduction personnalisé](/docs/services/language-translator/customizing.html#training).
1.  Dans votre application, faites pointer la zone "ModelID" vers les nouveaux modèles personnalisés. 
1.  Déconnectez le service précédent de votre application dans {{site.data.keyword.cloud_notm}}, puis supprimez-le.

## 6 novembre 2015
{: #6-november-2015}

La version bêta de l'outil {{site.data.keyword.languagetranslatorshort}} est publiée. Cet outil est une application Web qui fournit une interface graphique permettant de gérer et d'entraîner des modèles dans le but d'améliorer l'exactitude de la traduction automatique. Vous pouvez créer des projets, télécharger des données d'entraînement et traduire du texte. 

## 1er décembre 2014
{: #1-december-2014}

Les API bêta Machine Translator et Language Identification ont été mises à niveau et combinées dans l'API {{site.data.keyword.languagetranslatorshort}}. Pour commencer à utiliser immédiatement le nouveau service, vous devez mettre à jour votre code afin qu'il reflète les changements suivants :

- **Nouveau paramètre model\_id** : dans l'API bêta, vous définissiez le paramètre `sid` afin de sélectionner le modèle à employer pour la traduction. Dans cette version, le paramètre `sid` est renommé en `model_id`. Pour extraire les valeurs admises par le paramètre `model_id`, utilisez l'opération `GET/language  translator/api/v2/models`. La liste de tous les modèles et des valeurs `model_id` correspondantes est renvoyée.
- **Prise en charge des paires de langues** : au lieu de sélectionner un `model_id`, vous pouvez désormais indiquer une langue source et une langue cible ; le modèle utilisé par défaut sera alors celui qui a été entraîné sur le domaine général des actualités. 
- **Prise en charge du corps de demande JSON** : lorsque vous effectuez une demande de traduction POST, vous pouvez maintenant faire de la demande une soumission JSON. Le formatage JSON vous permet de soumettre plusieurs paragraphes à traduire au lieu d'indiquer un seul texte au format de soumission de formulaire. 
- **Prise en charge du corps de réponse JSON** : la demande de traduction renvoie une prise en charge de formatage JSON et de formatage de texte en clair. Le format JSON permet de renvoyer les termes traduits sous la forme de plusieurs paragraphes au lieu d'un seul texte.
- **Prise en charge de l'en-tête Accept** : l'en-tête Accept peut désormais être utilisé pour définir le format de la réponse dans toutes les opérations (text/plain ou application/json).
- **Prise en charge de Language Identification** : des méthodes d'identification de langue ont été ajoutées à cette API. Cela vous permet d'identifier la langue des textes d'entrée et de répertorier toutes les
langues prises en charge pouvant être détectées par l'API.


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

# Notes sur l'édition

Les nouvelles fonctions et modifications apportées au service
ci-après sont disponibles.
{: shortdesc}

## Nouveau processus d'authentification d'API
{: #iam-auth-process }

Le service {{site.data.keyword.languagetranslatorshort}} inclut un nouveau processus d'authentification d'API pour les instances de service hébergées aux emplacements suivants :

- Dallas depuis le 15 juin 2018
- Francfort depuis le 15 juin 2018
- Londres
- Sydney depuis le 12 juin 2018
- Tokyo
- Washington, DC depuis le 12 juin 2018

{{site.data.keyword.cloud_notm}} migre vers l'authentification IAM (Identity and Access Management) par jeton. Avec certaines instances de service, vous vous authentifiez auprès de l'API en utilisant IAM.

- Pour les _nouvelles_ instances de service créées dans les emplacements indiqués précédemment, vous utilisez IAM pour l'authentification. Vous pouvez transmettre un jeton bearer ou une clé d'API. Les jetons prennent en charge les demandes authentifiées sans intégrer de données d'identification de service dans chaque appel. Les clés d'API utilisent l'authentification de base.

    Lorsque vous utilisez un kit SDK Watson, vous pouvez transmettre la clé d'API et laisser le kit SDK gérer le cycle de vie des jetons. Pour plus d'informations et des exemples, voir [Authentification ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/apidocs/language-translator#authentication){: new_window} dans la référence de l'API.
- Pour les instances de service _existantes_ créées avant la date indiquée, vous continuez de vous authentifier en indiquant le nom d'utilisateur et le mot de passe pour l'instance de service. Il peut également être nécessaire de migrer ces instances de service vers l'authentification IAM. Des mises à jour concernant les dates et le processus de migration seront mises à disposition. Pour plus d'informations sur la migration, voir [Migration des instances de service Cloud Foundry vers un groupe de ressources](/docs/resources?topic=resources-migrate#migrate).

Pour déterminer l'authentification à utiliser, affichez les données d'identification du service en cliquant sur l'instance de service dans la [page des ressources {{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/resources){: new_window}.

## Gestion des versions d'API du service
{: shortdesc}

Les demandes d'API dans {{site.data.keyword.languagetranslatorshort}}, version 3 requièrent un paramètre de version qui accepte une date au format `version=YYYY-MM-DD`. Chaque fois que nous modifions l'API de manière irréversible, nous publions une nouvelle version mineure de l'API. 

Envoyez le paramètre de version avec chaque demande d'API. Le service utilise la version d'API correspondant à la date que vous spécifiez ou la toute dernière version avant cette date. Ne laissez pas la date du jour par défaut. Indiquez à la place une date correspondant à une version compatible avec votre application et ne la changez pas tant que votre application n'est pas prête pour une version ultérieure.

La version actuelle est `2018-05-01`.

## 14 juin 2019
{: #14-june-2019}

De nouveaux [modèles de traduction](/docs/services/language-translator?topic=language-translator-translation-models) sont désormais disponibles pour l'anglais et le grec. 
- Anglais en grec (en-el)
- Grec en anglais (el-en)

## 13 juin 2019
{: #13-june-2019}

De nouveaux [modèles de traduction](/docs/services/language-translator?topic=language-translator-translation-models) sont désormais disponibles pour l'anglais et l'hébreu. 
- Anglais en hébreu (en-he)
- Hébreu en anglais (he-en)

## 21 mars 2019
{: #21-march-2019}

Depuis le 21 mars 2019, vous ne pouvez voir que les données d'identification du service associées au rôle affecté à votre compte {{site.data.keyword.cloud_notm}}. Par exemple, si vous disposez du rôle `reader`, les niveaux de données d'identification du service supérieurs ou égaux à `writer` ne sont pas visibles. 

Ce changement n'affecte pas l'accès aux API pour les utilisateurs ou applications qui possèdent déjà des données d'identification de clé de service. Seul l'affichage des données d'identification dans {{site.data.keyword.cloud_notm}} est affecté.

Pour plus d'informations sur les clés de service et les rôles utilisateur, voir [Clés d'API de service IAM](/docs/services/watson?topic=watson-api-key-bp#api-key-bp). 

## 14 décembre 2018
{: #14-december-2018}

- Vous pouvez maintenant créer des instances de service {{site.data.keyword.languagetranslatorshort}} dans l'emplacement {{site.data.keyword.cloud_notm}} de Londres. 

## 16 novembre 2018
{: #16-november-2018}

- [Traduction de documents (Bêta)](/docs/services/language-translator?topic=language-translator-translating-documents) est désormais disponible par l'intermédiaire de nouveaux noeuds finaux d'API. Soumettez un document Microsoft Office, un PDF ou un autre document dont le format de fichier est pris en charge ; {{site.data.keyword.languagetranslatorshort}} vous proposera une traduction qui respecte le formatage d'origine. 
  - Les [formats de fichier pris en charge](/docs/services/language-translator?topic=language-translator-translating-documents#supported-file-types) sont `.doc`, `.ppt`, `.pdf`, etc.

- De nouveaux [modèles de traduction](/docs/services/language-translator?topic=language-translator-translation-models) sont désormais disponibles pour le hongrois : 
  - Hongrois en anglais (hu-en)
  - Anglais en hongrois (en-hu)

## 8 novembre 2018
{: #8-november-2018}

- Vous pouvez maintenant créer des instances de service {{site.data.keyword.languagetranslatorshort}} dans l'emplacement {{site.data.keyword.cloud_notm}} de Tokyo. 

## 9 août 2018
{: #9-august-2018}

De nouveaux [modèles de traduction](/docs/services/language-translator?topic=language-translator-translation-models) sont désormais disponibles pour le norvégien bokmål : 
  - Norvégien bokmål en anglais (nb-en)
  - Anglais en norvégien bokmål (en-nb)

## 27 juin 2018
{: #27-june-2018}

De nouveaux [modèles de traduction](/docs/services/language-translator?topic=language-translator-translation-models) prenant en charge six nouvelles langues sont désormais disponibles : 
  - Catalan
    - Catalan en espagnol (ca-es)
    - Espagnol en catalan (es-ca)
  - Tchèque
    - Tchèque en anglais (cs-en)
    - Anglais en tchèque (en-cs)
  - Danois
    - Danois en anglais (da-en)
    - Anglais en danois (en-da)
  - Finnois
    - Finnois en anglais (fi-en)
    - Anglais en finnois (en-fi)
  - Hindi
    - Hindi en anglais (hi-en)
    - Anglais en hindi (en-hi)
  - Suédois
    - Suédois en anglais (sv-en)
    - Anglais en suédois (en-sv)
  

## 15 juin 2018
{: #15-june-2018}

Depuis le 15 juin 2018, les nouvelles instances de service créées dans les régions Allemagne et Sud des Etats-Unis utilisent l'[authentification IAM (Identity and Access Management)](#iam-auth-process). 

Les nouvelles instances de service que vous créez en Allemagne et dans le Sud des Etats-Unis ne sont pas compatibles avec Language Translator, version 2. Si vous utilisez Language Translator, version 2 et prévoyez d'utiliser de nouvelles instances de service dans votre application, vous devrez [migrer vers l'API version 3](/docs/services/language-translator?topic=language-translator-migrating). 

## 12 juin 2018
{: #12-june-2018}

{{site.data.keyword.languagetranslatorshort}}, version 3 est désormais disponible. L'API version 2 de Language Translator n'est plus disponible depuis le 31 juillet 2018. Pour profiter des toutes dernières améliorations du service, migrez vers l'API version 3. Pour plus d'informations, consultez la page relative à la [migration vers Language Translator, version 3](/docs/services/language-translator?topic=language-translator-migrating). 

### Nouveautés de la version 3
{: #whats-new}

-  L'API version 3 de {{site.data.keyword.languagetranslatorshort}} est fournie avec des modèles NMT qui offrent des résultats de traduction considérablement améliorés. Tous les modèles NMT peuvent être maintenant personnalisés. 
-  Utilisation de modèles personnalisés comme modèles de base pour la personnalisation des glossaires forcés. 
-  L'API version 3 est un sous-ensemble JSON simplifié de l'API version 2 retirée. 
-  Introduction des dates de version d'API pour offrir aux développeurs la liberté d'adopter les futures modifications d'API à leur propre rythme. 

### Modifications majeures
{: #breaking-changes}

- Date de version obligatoire pour tous les noeuds finaux d'API : les demandes d'API version 3 requièrent un paramètre de requête de date de version au format `version=YYYY-MM-DD`. La dernière version d'API est `version=2018-05-01`. 
- API simplifiée :
  - Les méthodes **Translate** et **Identify** ne permettent pas de renvoyer des réponses en texte en clair dans la version 3. Elles ne renvoient que des réponses JSON. 
  - Les méthodes `GET /translate` et `GET /identify` ne sont pas prises en charge dans la version 3. Utilisez les méthodes `POST /translate` et `POST /identify` à la place.  
- La personnalisation de corpus monolingues n'est pas prise en charge dans la version 3.
- La création de modèles personnalisés avec un corpus parallèle et un glossaire forcé doit être maintenant effectuée dans deux appels d'API. Commencez par personnaliser le modèle avec un corpus parallèle. Une fois que l'entraînement du modèle personnalisé est terminé, personnalisez-le de nouveau avec le glossaire forcé. Ce changement vous permet d'utiliser un modèle personnalisé entraîné avec un corpus parallèle comme base de la personnalisation des glossaires forcés. 
- Les modèles spécialisés dans les domaines des brevets et des conversations ne sont pas disponibles dans l'API version 3. La qualité de la traduction offerte par les modèles NMT dans les domaines des brevets et des conversations est généralement supérieure à celle des modèles spécialisés antérieurs. 
- Les clés d'objet des erreur ont été renommées afin d'être cohérentes avec les autres API Watson. `error_code` a été renommé en `code` et `error_message`, en `error`.

### Authentification IAM

Depuis le 12 juin 2018, les nouvelles instances de service créées dans les régions Sydney et Est des Etats-Unis utilisent l'[authentification IAM (Identity and Access Management)](#iam-auth-process). 

## 12 janvier 2018
{: #12-january-2018}

De nouveaux modèles NMT sont disponibles à la prévisualisation. Vous pouvez essayer les modèles NMT pour les paires de langues suivantes: 

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

Vous pouvez regarder une [vidéo de présentation sur YouTube ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://youtu.be/L6ZC0QaUZ2k) qui explique la manière de configurer {{site.data.keyword.languagetranslatorshort}} avec la prévisualisation NMT. 


## 15 décembre 2016
{: #15-december-2016}

Des modèles de traduction supplémentaires liés aux actualités ont été ajoutés : l'anglais vers et depuis le japonais.

## 15 novembre 2016
{: #15-november-2016}

Les outils précédemment disponibles pour le service {{site.data.keyword.languagetranslatorshort}} ne sont plus disponibles ou ne sont plus pris en charge. 

Contactez votre ingénieur commercial ou le support technique pour avoir davantage d'informations sur l'utilisation de l'API {{site.data.keyword.languagetranslatorshort}} afin d'effectuer les tâches prises en charge par l'outil {{site.data.keyword.languagetranslatorshort}}.

## 1er septembre 2016
{: #1-september-2016}

Le service de traduction IBM Watson&trade; se nomme maintenant {{site.data.keyword.languagetranslatorshort}}.

## 22 mars 2016
{: #22-march-2016}

La prise en charge des langues supplémentaires suivantes a été ajoutée : l'anglais vers depuis l'italien et l'espagnol vers et depuis le français.

## 3 décembre 2015
{: #3-december-2015}

Depuis le 15 janvier 2016, toutes les fonctions de personnalisation du plan Standard ne sont plus suivies. Il n'est pas nécessaire de modifier les applications qui n'utilisent pas de fonctions de personnalisation car le plan Standard reste actif pour tous les appels d'API qui ne sont pas liés à la personnalisation ou à des modèles personnalisés. Si vous souhaitez employer les fonctions de personnalisation de la GA (plan Trainable) du service {{site.data.keyword.languagetranslatorshort}} avec une application {{site.data.keyword.cloud}} qui utilise une instance antérieure du service, procédez comme suit :

1.  Créez une nouvelle instance Watson {{site.data.keyword.languagetranslatorshort}} et indiquez le plan de GA "Trainable".
2.  Liez la nouvelle instance "Trainable" du service à votre application dans {{site.data.keyword.cloud_notm}}.
3.  Regroupez les données utilisées lors de la création initiale des modèles personnalisés. Pour plus d'informations, voir [Structure des données d'entraînement](/docs/services/language-translator?topic=language-translator-customizing#structure).
4.  Téléchargez les données d'entraînement pour créer de nouveaux modèles personnalisés sur l'instance "Trainable". Pour plus d'informations, voir [Entraînement d'un modèle de traduction personnalisé](/docs/services/language-translator?topic=language-translator-customizing#training).
5.  Dans votre application, faites pointer la zone "ModelID" vers les nouveaux modèles personnalisés.
6.  Déconnectez le service précédent de votre application dans {{site.data.keyword.cloud_notm}}, puis supprimez-le.

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

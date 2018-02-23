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

# Personnalisation de votre modèle
{: #customizing}

Souhaitez-vous créer un traducteur destiné à être utilisé par un support client ? Disposez-vous de termes propres à votre entreprise que vous désirez employer d'une certaine manière dans des conversations ? Voulez-vous permettre à vos ingénieurs dans un pays de rechercher des données liées à des brevets dans une autre langue ? Déposez-vous des brevets liés à une technologie spécifique ? Utilisez vos propres données pour créer un dictionnaire personnalisé ainsi qu'un modèle de traduction personnalisé dans l'API {{site.data.keyword.languagetranslatorshort}}.
{: shortdesc}

Vous pouvez personnaliser le modèle {{site.data.keyword.languagetranslatorshort}} comme indiqué ci-après :  

- Enseignez au service les paires de termes ou d'expressions correspondants dans une langue source et une langue cible. Fournissez un *glossaire forcé*, qui contient des paires de termes ou d'expressions absolus, à savoir les termes définitifs que le service de traduction doit considérer comme obligatoires. Vous pouvez également fournir un *corpus parallèle*, contenant des paires de termes ou d'expressions servant de suggestions de traduction secondaires dont le service de traduction doit tenir compte.
- Téléchargez un corps de texte volumineux dans une langue cible (appelée *corpus monolingue*) destiné à servir d'échantillon de langue et que le service peut évaluer et utiliser pour améliorer la qualité globale de la traduction. 

Pour afficher la liste des modèles que vous pouvez personnaliser, utilisez la méthode `GET /v2/models` et recherchez le paramètre de réponse `customizable=true` dans la réponse pour chaque modèle de langue. 

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

Chaque modèle personnalisable peut stocker jusqu'à 10 personnalisations par instance de service. 

## Structure des données d'entraînement
{: #structure}

Pour fournir un glossaire ou un corpus des termes destiné à être employé par le service {{site.data.keyword.languagetranslatorshort}} lors de son entraînement, créez un document valide codé en UTF-8 conforme à la spécification Translation Memory Exchange (TMX) [version 1.4 ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ttt.org/oscarstandards/tmx/tmx14.dtd){: new_window}. TMX est une spécification XML conçue pour les outils de traduction automatique. Voici un exemple de fichier de glossaire au format TMX comportant deux paires terme-traduction : 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>International Business Machines</seg>
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

Chaque paire terme-traduction doit figurer entre des balises `<tu>` : 

```xml
<tu>
  <tuv xml:lang="en">
    <seg>International Business Machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

L'attribut `xml:lang` dans la balise `<tuv>` identifie la langue dans laquelle un terme est exprimé, alors que la balise `<seg>` contient le terme ou la traduction.

Le service {{site.data.keyword.languagetranslatorshort}} utilise uniquement les éléments `<tu>`, `<tuv>` et `<seg>`. Tous les autres éléments de l'exemple sont requis pour la validité du fichier TMX ou sont présents à titre d'information, mais ils ne sont pas utilisés par le service.

L'exemple précédent montre comme standardiser de manière permanente la traduction d'un terme technique, comme 'patent' et comment personnaliser la traduction du nom d'une société, comme 'International Business Machines'. Avec le modèle standard, l'expression 'International Business Machines' pourrait être traduite par 'Machines Commerciales Internationales', mais elle ne doit en fait pas être traduite car il s'agit du nom d'une société.

## Utilisation de l'exemple comme modèle

Pour utiliser l'exemple fourni comme modèle pour votre propre glossaire ou corpus, procédez comme indiqué ci-après : 

1.  Copiez et collez l'exemple dans un éditeur de texte. 

1.  Modifiez l'attribut `srclang` de la balise `<header>` en indiquant le [code de langue ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} de la langue source employée par votre glossaire ou votre corpus parallèle. 

1.  Modifiez l'attribut `xml:lang` des balises `<tuv>` en indiquant le [code de langue ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} correct pour chaque terme ou chaque traduction. 

    Le service {{site.data.keyword.languagetranslatorshort}} utilise les codes de langue ISO 639-1 pour toutes les langues sauf pour l'arabe égyptien, qui utilise le code ISO 639-3.

1.  Sauvegardez le document avec l'extension `.tmx` et le codage UTF-8. 

### Modification d'un fichier TMX en codage UTF-8

Vous pouvez faire appel à plusieurs outils pour créer ou générer des fichiers TMX. Les fichiers TMX obtenus sont souvent codés en UTF-16 par défaut. Le service {{site.data.keyword.languagetranslatorshort}} accepte uniquement les fichiers TMX codés en UTF-8. Pour modifier le codage d'un fichier TMX, procédez comme suit : 

1.  Ouvrez le fichier TMX dans un éditeur de texte.

1.  Modifiez l'en-tête XML (le cas échéant) `<?xml ... encoding="utf-16"?>` en `<?xml ... encoding="utf-8"?>`.

1.  Sauvegardez le fichier sous un nouveau nom et avec une sortie codée en UTF-8. 

Les utilisateurs de Mac peuvent également modifier le codage du fichier en mettant à jour l'en-tête XML du document comme décrit à l'étape 2, puis en exécutant la commande suivante dans le Terminal :

```bash
iconv -f utf-16 -t utf-8 <nom_fichier_utf-16.tmx> <nouveau_nom_ficheir_utf-8.tmx>
```
{: pre}

## Entraînement d'un modèle de traduction personnalisé
{: #training}

Utilisez la méthode `POST /v2/models` pour télécharger votre fichier TMX et entraîner votre modèle de traduction. Indiquez au moins une des options de fichier suivantes pour entraîner votre modèle personnalisé :

- `forced_glossary` : fichier TMX codé en UTF-8 contenant des paires de termes correspondants dans les langue source et cible, et considérées comme absolues par le système. Ce fichier remplace complètement les données de domaine d'origine. 

    Les glossaires forcés sont soumis à une limite de taille de 10 Mo. A l'heure actuelle, vous ne pouvez charger qu'un fichier de glossaire forcé par modèle de traduction.
    
- `parallel_corpus` : fichier TMX codé en UTF-8 contenant des expressions correspondantes dans les langues source et cible qui servent d'exemples pour Watson. Les corpus parallèles diffèrent des glossaires forcés car ils ne remplacement pas les données de domaine d'origine.

    Pour que l'entraînement d'un modèle personnalisé aboutisse, le document de corpus parallèle doit comporter au moins 5 000 paires de termes et de traductions. 
    
- `monolingual_corpus` : fichier en texte clair codé en UTF-8 contenant un corps de texte dans la langue cible, lié au domaine dans lequel vous souhaitez effectuer la traduction. Le fait de fournir un corpus monolingue contribue à l'amélioration des traductions littérales en rendant la traduction plus fluide et plus naturelle.

    Pour que l'entraînement d'un modèle personnalisé aboutisse, le document de corpus monolingue doit contenir au moins 1 000 phrases. 

La taille de fichier cumulée de tous les fichiers de glossaire et de corpus téléchargés est limitée à 250 Mo. Selon la taille des fichiers téléchargés, l'entraînement peut prendre quelques minutes pour un glossaire ou durer plusieurs heures dans le cas d'un corpus volumineux. 

L'exemple curl suivant utilise l'option de fichier `forced_glossary`. 
1. Téléchargez le fichier TMX exemple depuis la section [Structure des données d'entraînement](#structure). 
1. Utilisez le domaine d'actualités en français (en-fr) comme modèle de base. Tout ce qui est indiqué dans le fichier TMX remplace complètement les données de domaine d'origine. 

    Pour rechercher tous les domaines de modèle pris en charge par le service {{site.data.keyword.languagetranslatorshort}}, utilisez la méthode `GET v2/models` :

```curl
curl -u "{username}":"{password}" -X POST -F base_model_id=en-fr -F name="test_glossary" -F forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

La méthode `POST /v2/models` répond avec un code `200` et un nouveau `model_id`. Utilisez ce `model_id` lorsque vous traduisez un texte avec ce nouveau modèle personnalisé. 

## Surveillance de l'entraînement

La taille du fichier d'entraînement TMX affecte la durée de l'entraînement d'une demande `POST /v2/models`. Pour surveiller la progression de l'entraînement et savoir s'il aboutit, faites appel à la méthode `GET /v2/models/<model_id>` et consultez la valeur du paramètre `status` dans la réponse.

Cet exemple de commande donne des informations sur le modèle et vérifie le statut de l'entraînement qui a commencé dans la section [Entraînement du modèle de traduction](#training). Cette commande utilise un corps de demande vide. 

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}

Le paramètre de réponse `STATUS` décrit l'état du modèle dans le processus d'entraînement : 

- `uploading`
- `uploaded`
- `dispatching`
- `queued@<#>`
- `training`
- `trained`
- `publishing`
- `available`

Lorsque le statut du modèle prend la valeur `available`, il est prêt à être utilisé avec votre instance de service. Si votre modèle est supprimé, ou s'il rencontre une erreur lors du processus d'entraînement, l'une des erreurs suivantes risque de s'afficher :

- `deleted`
- `error`

## Utilisation d'un modèle de traduction personnalisé

Après avoir entraîné votre modèle de traduction personnalisé, indiquez le model\_id de ce modèle de traduction pour l'utiliser avec la méthode `POST /v2/translate` ou `GET /v2/translate`.

L'exemple suivant appelle le modèle de l'anglais vers le français qui a été personnalisé dans la section [Entraînement d'un modèle de traduction personnalisé](#training). 

```curl
curl -u "{username}":"{password}" --header "Content-Type: application/json" -X POST --data "{\"model_id\": \"3e7dfdbe-f757-4150-afee-458e71eb93fb\",\"text\": \"Hello, my name is Watson, and I work for International Business Machines. How can I help you today?\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{: codeblock}

Le service {{site.data.keyword.languagetranslatorshort}} évalue la qualité de la traduction à l'aide des normes BLEU (Bilingual Evaluation Understudy) et de normes développées par IBM. Les résultats varient selon la paire de langues, l'utilisation de termes vernaculaires ou du domaine des données. 

## Suppression d'un modèle de traduction personnalisé

Lorsqu'un modèle de traduction devient obsolète, vous pouvez le supprimer. Pour supprimer un modèle de traduction personnalisé, utilisez la méthode `DELETE /v2/models/<model_id>`. Pour extraire les ID de modèle de tous les modèles de traduction, qu'il s'agisse de modèles personnalisés ou par défaut, utilisez la méthode `GET /v2/models`.

La commande suivante supprime le modèle de traduction créé dans ces exemples. 

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}


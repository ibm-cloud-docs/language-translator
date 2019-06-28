---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-13"

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

La plupart des modèles de traduction fournis dans {{site.data.keyword.languagetranslatorshort}} peuvent être étendus pour apprendre des termes et phrases personnalisés ou un style général dérivé de vos données de traduction. Pour créer votre propre modèle de traduction personnalisé, procédez comme suit :
{: shortdesc}

## Avant de commencer
{: #before-you-begin}

1. Assurez-vous que votre instance de service {{site.data.keyword.languagetranslatorshort}} se trouve dans un plan de tarification Avancé ou Premium. Les plans Simplifié et Standard ne prennent pas en charge la personnalisation. 
1. Recherchez un modèle de base personnalisable pour votre paire de langues. Vous avez besoin de l'ID modèle du modèle de base pour entraîner votre modèle personnalisé. 
    - Recherchez les modèles répertoriés dans la page [Modèles de traduction](/docs/services/language-translator?topic=language-translator-translation-models). Recherchez la valeur "**true**" dans la colonne **Personnalisable** et assurez-vous que les langues **Source** et **Cible** du modèle correspondent à votre paire de langues. 
    - Vous pouvez également utiliser la méthode d'API [List models ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/apidocs/language-translator#list-models) pour rechercher des modèles à l'aide d'un programme. Vous pouvez filtrer les résultats par langue à l'aide des paramètres `source` et `target`. 

## Etape 1 : Créez vos données d'entraînement
{: #create-your-training-data}

Les données d'entraînement doivent être fournies au service au [format de fichier TMX](#creating-tmx-files). Vous pouvez stocker jusqu'à 10 personnalisations par paire de langues dans une instance de service. Le service prend en charge deux types de demande de personnalisation. Vous pouvez personnaliser un modèle avec un glossaire forcé ou un corpus contenant des phrases parallèles. 

- Utilisez un [glossaire forcé](#forced-glossary-customization) pour forcer la traduction de certains termes et phrases d'une manière spécifique. 
- Utilisez un [corpus parallèle](#parallel-corpus-customization) si vous souhaitez que votre modèle personnalisé apprenne des modèles de traduction généraux de vos exemples. Ce que votre modèle apprend d'un corpus parallèle peut améliorer les résultats de traduction d'un texte en entrée sur lequel le modèle ne s'est pas encore entraîné. 

Une fois que vous avez créé vos [fichiers TMX](#creating-tmx-files), vous êtes prêt à entraîner votre modèle. 

## Etape 2 : Entraînez votre modèle
{: #train-your-model}

Utilisez la méthode [Create model ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/apidocs/language-translator#create-model) pour entraîner votre modèle. Dans votre demande, spécifiez l'ID modèle d'un modèle de base personnalisable et les données d'entraînement dans les paramètres `forced_glossary` ou `parallel_corpus`. 

### Exemple de demande
{: #train-model-example-request}

L'exemple de demande ci-après utilise un fichier de glossaire forcé, _glossary.tmx_, pour personnaliser le modèle de base `en-es`. Pour un exemple de fichier TMX de glossaire forcé, reportez-vous à la section [Personnalisation de glossaire forcé](#forced-glossary). 

```bash
curl --user apikey:{apikey} -X POST --form forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

La réponse de l'API contient des détails sur votre modèle personnalisé et notamment l'ID modèle. Utilisez ce dernier pour vérifier le statut de votre modèle et traduire des phrases une fois que ce statut devient "disponible". 

```json
{
  "model_id": "96221b69-8e46-42e4-a3c1-808e17c787ca",
  "source": "en",
  "target": "es",
  "base_model_id": "en-es",
  "domain": "general",
  "customizable": false,
  "default_model": false,
  "owner": "4937aab7-0f3a-4a75-bee1-0b7a12b6b8",
  "status": "uploaded",
  "name": "custom-english-to-spanish",
  "train_log": null
}
```
{: codeblock}

## Etape 3 : Vérifiez le statut de votre modèle
{: #check-model-status}

L'entraînement du modèle peut prendre de quelques minutes (pour les glossaires forcés) à plusieurs heures (pour les corpus parallèles volumineux) selon la quantité de données d'entraînement impliquée. Pour vérifier si votre modèle est disponible, utilisez la méthode [Get model ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/apidocs/language-translator#get-model-details) et spécifiez l'ID modèle que vous avez reçu dans la réponse du service à l'étape 2. Vous pouvez également vérifier le statut de tous vos modèles à l'aide de la méthode [List models ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/apidocs/language-translator#list-models). 

L'attribut de réponse `status` décrit l'état du modèle dans le processus d'entraînement : 

- `uploading`
- `uploaded`
- `dispatching`
- `queued`
- `training`
- `trained`
- `publishing`
- `available`

Lorsque le statut du modèle prend la valeur `available`, il est prêt à être utilisé avec votre instance de service. Si votre modèle est supprimé, ou s'il rencontre une erreur lors du processus d'entraînement, l'un des statuts suivants risque de s'afficher :

- `deleted`
- `error`

### Exemple de demande
{: #check-model-example-request}

L'exemple ci-après obtient les informations du modèle identifié par l'ID modèle `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```bash
curl --user apikey:{apikey_value} "https://gateway.watsonplatform.net/language-translator/api/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## Etape 4 : Traduisez du texte à l'aide de votre modèle personnalisé
{: #translate-text}

Pour utiliser votre modèle personnalisé, spécifiez le texte à traduire et l'ID modèle du modèle personnalisé dans la méthode [Translate ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/apidocs/language-translator#translate). 

### Exemple de demande
{: #translate-text-example-request}

L'exemple ci-après traduit le texte à l'aide du modèle personnalisé identifié par l'ID modèle `96221b69-8e46-42e4-a3c1-808e17c787ca`. 

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data '{"text":"Hello","model_id":"96221b69-8e46-42e4-a3c1-808e17c787ca"}' https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}


## Personnalisation de glossaire forcé
{: #forced-glossary-customization}

Utilisez un ** glossaire forcé** afin de définir des traductions obligatoires pour des termes et phrases spécifiques. Si vous souhaitez un contrôle spécifique sur le comportement de traduction, utilisez un glossaire forcé. 

- Format des données d'entraînement : [TMX](#creating-tmx-files) (codage UTF-8)
- Taille maximale du fichier : 10 Mo
- Vous pouvez appliquer un glossaire forcé à un modèle de base ou à un modèle personnalisé à l'aide d'un corpus parallèle. 
- Limitez-vous à un glossaire forcé par modèle. 

Les exemples de glossaire forcé étant sensibles à la mise en majuscules, assurez-vous que vos données d'entraînement reflètent la mise en majuscules du contenu que votre application rencontrera.
{: tip}

### Exemple de glossaire forcé
{: #forced-glossary-example}

L'exemple ci-après illustre un fichier TMX avec deux paires de traduction. La première paire force la conservation de la chaîne "international business machines" en anglais lors de la traduction. Ce type de traduction forcée peut s'avérer utile si vous souhaitez conserver des noms de société mis à tord en majuscules dans des communications informelles. La deuxième paire force le modèle à toujours utiliser "brevet" lors de la traduction de "patent". 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="phrase" o-tmf="" adminlang="en"
    srclang="en" datatype="PlainText" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
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



## Personnalisation de corpus parallèle
{: #parallel-corpus-customization}

Utilisez un **corpus parallèle** pour fournir des traductions supplémentaires à partir desquelles le modèle de base s'entraînera. Il permet d'adapter le modèle de base à un domaine spécifique. La manière dont le modèle personnalisé résultant traduit le texte dépend de la compréhension combinée du corpus parallèle et du modèle de base par le modèle. 

- Format des données d'entraînement : [TMX](#creating-tmx-files) (codage UTF-8)
- Longueur maximale des paires de traduction : 80 mots source
- Nombre minimal de paires de traduction : 5 000
- Taille maximale du fichier : 250 Mo
- Vous pouvez soumettre plusieurs fichiers de corpus parallèle en répétant le paramètre `parallel_corpus` à partir du moment où la taille cumulée de ces fichiers ne dépasse pas 250 Mo. 

### Exemple de corpus parallèle
{: #parallel-corpus-example}

Vous trouverez ci-après un extrait de corpus parallèle de l'anglais vers le français, téléchargé à partir de la [collection MultiUN ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://opus.nlpl.eu/MultiUN.php) disponible sur le site Web de corpus parallèle ouvert OPUS. Vous pouvez télécharger une version compressée de l'intégralité du fichier TMX [ici ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz).


```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
<header creationdate="Tue Jan 29 12:49:40 2013"
          srclang="en"
          adminlang="en"
          o-tmf="unknown"
          segtype="sentence"
          creationtool="Uplug"
          creationtoolversion="unknown"
          datatype="PlainText" />
  <body>
    <tu>
      <tuv xml:lang="en"><seg>RESOLUTION 55/100</seg></tuv>
      <tuv xml:lang="fr"><seg>RÉSOLUTION 55/100</seg></tuv>
    </tu>
    <tu>
      <tuv xml:lang="en"><seg>Adopted at the 81st plenary meeting, on 4 December 2000, on the recommendation of the Committee (A/55/602/Add.2 and Corr.1, para. 94),The draft resolution recommended in the report was sponsored in the Committee by: Bolivia, Cuba, El Salvador, Ghana and Honduras. by a recorded vote of 106 to 1, with 67 abstentions, as follows:</seg></tuv>
      <tuv xml:lang="fr"><seg>Adoptée à la 81e séance plénière, le 4 décembre 2000, sur la recommandation de la Commission (A/55/602/Add.2, par. 94)Le projet de résolution recommandé dans le rapport de la Commission avait pour auteurs les pays suivants: Bolivie, Cuba, El Salvador, Ghana et Honduras., par 106 voix contre une, avec 67 abstentions, à la suite d'un vote enregistré, les voix s'étant réparties comme suit:</seg></tuv>
    </tu>
    ...
```
{: codeblock}

Les améliorations générales liées à la personnalisation du corpus parallèle sont moins prévisibles que les résultats obligatoires que vous obtenez de la personnalisation du glossaire forcé. Par exemple, étudiez l'unité de traduction ci-après de l'exemple de corpus parallèle (lignes 172 à 175).

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

Si vous traduisez "55/102. Globalization and its impact on the full enjoyment of all human rights" à l'aide du modèle de base `en-fr`, le service répond avec la traduction ci-après. 

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

Si la même phrase en entrée est traduire par un modèle personnalisé entraîné avec l'exemple de corpus, le service répond avec une autre traduction, différente de celle de l'exemple de traduction fourni dans les données d'entraînement. 

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- Le modèle personnalisé traduit "the full enjoyment" par "le plein exercice" au lieu de "la pleine jouissance". Cet écart par rapport au comportement du modèle de base s'explique sans doute par les nombreux exemples du corpus dans lesquels "enjoyment" est traduit par "exercice". 
- Le modèle personnalisé traduit "of all human rights" par "de tous les droits de l'homme" au lieu de reproduire le résultat de l'unité de traduction "des droits de l'homme". Ce comportement reflète la compréhension cohésive du modèle de base par le modèle entraîné et tous les exemples de traduction liés à "of all human rights" du corpus parallèle. 

Dans certains cas, un modèle personnalisé entraîné avec un corpus parallèle peut sembler ignorer un exemple spécifique que vous avez fourni. Essayez alors de rechercher dans vos données d'entraînement d'autres phrases qui pourraient influencer le comportement de traduction ou envisagez d'utiliser un glossaire forcé si vous souhaitez contrôler une traduction spécifique. 


## Création de fichiers TMX
{: #creating-tmx-files}

Pour fournir un glossaire ou un corpus des termes destiné à être employé par le service {{site.data.keyword.languagetranslatorshort}} lors de son entraînement, créez un document valide codé en UTF-8 conforme à la spécification TMX [version 1.4 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ttt.org/oscarStandards/tmx/){: new_window}. TMX est une spécification XML conçue pour les outils de traduction automatique. Voici un exemple de fichier de glossaire au format TMX comportant deux unités de traduction (éléments `<tu>`) : 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
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
    <seg>international business machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

L'attribut `xml:lang` dans la balise `<tuv>` identifie la langue dans laquelle un terme est exprimé, alors que la balise `<seg>` contient le terme ou la traduction.

Le service {{site.data.keyword.languagetranslatorshort}} utilise uniquement les éléments `<tu>`, `<tuv>` et `<seg>`. Tous les autres éléments de l'exemple sont requis pour la validité du fichier TMX ou sont présents à titre d'information, mais ils ne sont pas utilisés par le service.



### Utilisation de l'exemple comme modèle
{: #using-the-example-template}

Pour utiliser l'exemple fourni comme modèle pour votre propre glossaire ou corpus, procédez comme indiqué ci-après :

1. Copiez et collez l'exemple dans un éditeur de texte.

2. Modifiez l'attribut `srclang` de la balise `<header>` en indiquant le [code de langue ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} de la langue source employée par votre glossaire ou votre corpus parallèle.

3. Modifiez l'attribut `xml:lang` des balises `<tuv>` en indiquant le [code de langue ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} correct pour chaque terme ou chaque traduction.

4. Sauvegardez le document avec l'extension `.tmx` et le codage UTF-8.

### Modification d'un fichier TMX en codage UTF-8
{: #changing-tmx-file-to-utf-8}

Vous pouvez faire appel à plusieurs outils pour créer ou générer des fichiers TMX. Les fichiers TMX obtenus sont souvent codés en UTF-16 par défaut. Le service {{site.data.keyword.languagetranslatorshort}} accepte uniquement les fichiers TMX codés en UTF-8. Pour modifier le codage d'un fichier TMX, procédez comme suit :

1. Ouvrez le fichier TMX dans un éditeur de texte.

1. Modifiez l'en-tête XML (le cas échéant) `<?xml ... encoding="utf-16"?>` en `<?xml ... encoding="utf-8"?>`.

1. Sauvegardez le fichier sous un nouveau nom et avec une sortie codée en UTF-8.

Les utilisateurs de Mac peuvent également modifier le codage du fichier en mettant à jour l'en-tête XML du document comme décrit à l'étape 2, puis en exécutant la commande suivante dans le Terminal :

```bash
iconv -f utf-16 -t utf-8 <nom_fichier_utf-16.tmx> <nouveau_nom_fichier_utf-8.tmx>
```
{: pre}


## Suppression d'un modèle de traduction personnalisé
{: #deleting-a-custom-model}

Pour supprimer un modèle de traduction personnalisé, utilisez la méthode [Delete model ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/apidocs/language-translator#delete-model). 

La commande suivante supprime le modèle de traduction dont l'ID modèle est `3e7dfdbe-f757-4150-afee-458e71eb93fb`.

```curl
curl --user apikey:{apikey_value} --request DELETE "https://gateway.watsonplatform.net/language-translator/api/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: codeblock}

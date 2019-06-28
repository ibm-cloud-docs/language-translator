---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

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

# Traduction de documents (Bêta)
{: #document-translator-tutorial}


Traduisez des fichiers d'une langue vers une autre tout en conservant le format d'origine. Il est possible de traduire dans plus de 12 formats de fichier différents, dont MS Office, Open Office et PDF.
{:shortdesc}

## Avant de commencer
{: #prerequisites}

- [Initiation](/docs/services/language-translator?topic=language-translator-getting-started) à {{site.data.keyword.languagetranslatorshort}}. Vous avez besoin de vos {{site.data.keyword.languagetranslatorshort}} données d'identification du service (`apikey` et `url`). 
- Assurez-vous que le document à traduire satisfait les exigences suivantes : 
    - Taille maximale du fichier : **20 Mo**
    - [Formats de fichier pris en charge](#supported-file-formats)
    - [Modèles de traduction pris en charge](/docs/services/language-translator?topic=language-translator-translation-models)

## Etape 1 : Soumettez un document à traduire
{: #submit-document-to-translate}

L'exemple de demande suivant soumet un exemple de fichier *curriculum.pdf* au service et le traduit de l'anglais vers le français. Remplacez `{apikey}` et `{url}` par vos données d'identification du service et remplacez `curriculum.pdf` par un chemin d'accès relatif vers votre fichier. 

Exemple de demande :
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Pour traduire un document à l'aide d'un [modèle personnalisé](/docs/services/language-translator?topic=language-translator-customizing), utilisez le paramètre **model_id**. La demande ci-après traduit le document à l'aide du modèle personnalisé identifié par l'ID modèle `96221b69-8e46-42e4-a3c1-808e17c787ca`. 

Exemple de demande :
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
{url}/v3/documents?version=2018-05-01
```
{: pre}


Une demande réussie renvoie un ID `document_id` dans la réponse.


Exemple de réponse :
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "processing",
  "created": "2018-10-11T03:31:25"
}
```
{: codeblock}

## Etape 2 : Vérifiez le statut de la traduction
{: #check-translation-status}

Une fois que vous avez soumis un document à traduire, vous pouvez vérifier le statut de la traduction pour déterminer si le document traduit peut être téléchargé. L'exemple de demande suivant vérifie le statut de la traduction du document dont l'ID est `bae02796-0d28-435c-9115-888359fdde62`.  

Exemple de demande :
```bash
curl -X GET \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Exemple de réponse :
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "available",
  "created": "2018-10-11T03:31:25",
  "completed": "2018-10-11T03:31:38"
}
```
{: codeblock}

Si, dans la réponse, `status` a pour valeur `available`, le document traduit est prêt à être téléchargé. 

## Etape 3 : Téléchargez le document traduit
{: #download-translated-document}

L'exemple de demande suivant sauvegarde le document traduit dont l'ID est `bae02796-0d28-435c-9115-888359fdde62` dans le fichier *curriculum-fr.pdf*.  

Exemple de demande :
```bash
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01
```
{: pre}

## Etape 4 : Traduisez un document déjà soumis
{: #translate-document-by-reference}

L'exemple de demande suivant fait référence au fichier *curriculum.pdf* d'origine en anglais, dont l'ID est `document_id` `bae02796-0d28-435c-9115-888359fdde62`, et le traduit en portugais. 

Exemple de demande :
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Exemple de réponse :
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

La réponse contient un nouvel ID `id_document/MD:CODE>. Répétez les étapes deux et trois avec votre nouveau document `document_id` pour vérifier le statut de la traduction et télécharger le fichier traduit une fois qu'il est disponible. 

## Etape 5 : Supprimez des documents
{: #delete-documents}

Les documents d'origine et les documents traduits associés sont supprimés automatiquement une fois qu'ils ont été utilisés pendant un certain temps. Pour plus d'informations, reportez-vous à la rubrique [Sécurité des informations](/docs/services/language-translator?topic=language-translator-information-security).
{: tip}

Pour supprimer des documents manuellement, utilisez la méthode **Delete document**. Dans ce tutoriel, le fichier *curriculum.pdf* en anglais ayant été impliqué avec deux traductions, deux demandes sont requises pour supprimer toutes les copies du document d'origine. 

Supprimez la soumission d'origine du fichier *curriculum.pdf* et la traduction en français : 
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Supprimez le doublon du fichier *curriculum.pdf* d'origine et la traduction en portugais. 
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01
```
{: pre}

## Formats de fichier pris en charge
{: #supported-file-formats}

-  Microsoft Office
    - Word : `.doc`, `.docx`
    - PowerPoint : `.ppt`, `.pptx`
    - Excel : `.xls`, `.xlsx`
    - RTF : `.rtf`
- Open Office
    - Writer : `.odt`
    - Impress : `.odp`
    - Calc : `.ods`
- Autres formats
    - PDF : `.pdf`
    - HTML : `.htm`, `.html`
    - XML : `.xml`
    - JSON : `.json` (les valeurs de type `chaîne` ou `tableau de chaînes` sont traduites)
    - Texte : `.txt`

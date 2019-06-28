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

# Modèles de traduction
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}} peut traduire les langues suivantes.
Cliquez sur une langue dans la liste ci-dessous pour afficher une liste des modèles de traduction compatibles.

Vous pouvez également utiliser la méthode d'API **List models** pour afficher les modèles de traduction disponibles et notamment vos modèles personnalisés. Vous pouvez filtrer les résultats par langue à l'aide des paramètres `source` et `target`. L'exemple ci-après répertorie les modèles qui peuvent traduire de l'anglais vers l'espagnol. 

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [Arabe](#arabic)
  - [Catalan](#catalan)
  - [Chinois (simplifié)](#chinese-simplified)
  - [Chinois (traditionnel)](#chinese-traditional)
  - [     Tchèque
    ](#czech)
  - [     Danois
    ](#danish)
  - [     Néerlandais
    ](#dutch)
  - [Anglais](#english)
  - [     Finnois
    ](#finnish)
  - [Français](#french)
  - [Allemand](#german)
  - [     Grec
    ](#greek)
  - [     Hébreu
    ](#hebrew)
  - [     Hindi
    ](#hindi)
  - [     Hongrois
    ](#hungarian)
  - [Italien](#italian)
  - [Japonais](#japanese)
  - [Coréen](#korean)
  - [Norvégien bokmål](#norwegian-bokmal)
  - [     Polonais
    ](#polish)
  - [Portugais](#portuguese)
  - [     Russe
    ](#russian)
  - [Espagnol](#spanish)
  - [     Suédois
    ](#swedish)
  - [     Turc
    ](#turkish)

## Arabe
{: #arabic}

Les modèles suivants peuvent traduire un texte à partir de l'arabe.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ar-en</code>
    </td>
    <td>
     Arabe (<code>ar</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Catalan
{: #catalan}

Les modèles suivants peuvent traduire un texte en catalan.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ca-es</code>
    </td>
    <td>
     Catalan (<code>ca</code>)
    </td>
    <td>
     Espagnol (<code>es</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Chinois (simplifié)
{: #chinese-simplified}

Les modèles suivants peuvent traduire un texte en chinois (simplifié).

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     Chinois simplifié (<code>zh</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Chinois (traditionnel)
{: #chinese-traditional}

Les modèles suivants peuvent traduire un texte en chinois (traditionnel).

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     Chinois traditionnel (<code>zh-TW</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Tchèque
{: #czech}

Les modèles suivants peuvent traduire un texte en tchèque.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     Tchèque (<code>cs</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Danois
{: #danish}

Les modèles suivants peuvent traduire un texte en danois.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     Danois (<code>da</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Néerlandais
{: #dutch}

Les modèles suivants peuvent traduire un texte en néerlandais.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     Néerlandais (<code>nl</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Anglais
{: #english}

Les modèles suivants peuvent traduire un texte à partir de l'anglais.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Arabe (<code>ar</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-cs</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Tchèque (<code>cs</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-da</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Danois (<code>da</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-de</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Allemand (<code>de</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-el</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Grec (<code>el</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-es</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Espagnol (<code>es</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-fi</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Finnois (<code>fi</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-fr</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Français (<code>fr</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-he</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Hébreu (<code>he</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-hi</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Hindi (<code>hi</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-it</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Italien (<code>it</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-ja</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Japonais (<code>ja</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-ko</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Coréen (<code>ko</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-nb</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Norvégien bokmal (<code>nb</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-nl</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Néerlandais (<code>nl</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-pl</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Polonais (<code>pl</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-pt</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Portugais (<code>pt</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-ru</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Russe (<code>ru</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-sv</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Suédois (<code>sv</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-tr</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Turc (<code>tr</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-zh</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Chinois simplifié (<code>zh</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-zh-TW</code>
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     Chinois traditionnel (<code>zh-TW</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Finnois
{: #finnish}

Les modèles suivants peuvent traduire un texte en finnois.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     Finnois (<code>fi</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Français
{: #french}

Les modèles suivants peuvent traduire un texte à partir du français.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     Français (<code>fr</code>)
    </td>
    <td>
     Allemand (<code>de</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>fr-en</code>
    </td>
    <td>
     Français (<code>fr</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>fr-es</code>
    </td>
    <td>
     Français (<code>fr</code>)
    </td>
    <td>
     Espagnol (<code>es</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Allemand
{: #german}

Les modèles suivants peuvent traduire un texte à partir de l'allemand.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     Allemand (<code>de</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>de-fr</code>
    </td>
    <td>
     Allemand (<code>de</code>)
    </td>
    <td>
     Français (<code>fr</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>de-it</code>
    </td>
    <td>
     Allemand (<code>de</code>)
    </td>
    <td>
     Italien (<code>it</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Grec
{: #greek}

Les modèles suivants peuvent traduire un texte en grec.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>el-en</code>
    </td>
    <td>
     Grec (<code>el</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Hébreu
{: #hebrew}

Les modèles suivants peuvent traduire un texte en hébreu.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>he-en</code>
    </td>
    <td>
     Hébreu (<code>he</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>


## Hindi
{: #hindi}

Les modèles suivants peuvent traduire un texte en hindi.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>hi-en</code>
    </td>
    <td>
     Hindi (<code>hi</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Hongrois
{: #hungarian}

Les modèles suivants peuvent traduire un texte en hongrois.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>hu-en</code>
    </td>
    <td>
     Hongrois (<code>hu</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Italien
{: #italian}

Les modèles suivants peuvent traduire un texte à partir de l'italien.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>it-de</code>
    </td>
    <td>
     Italien (<code>it</code>)
    </td>
    <td>
     Allemand (<code>de</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>it-en</code>
    </td>
    <td>
     Italien (<code>it</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Japonais
{: #japanese}

Les modèles suivants peuvent traduire un texte à partir du japonais.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     Japonais (<code>ja</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Coréen
{: #korean}

Les modèles suivants peuvent traduire un texte à partir du coréen.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ko-en</code>
    </td>
    <td>
     Coréen (<code>ko</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Norvégien bokmål
{: #norwegian-bokmal}

Les modèles suivants peuvent traduire un texte en norvégien bokmål.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     Norvégien bokmal (<code>nb</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Polonais
{: #polish}

Les modèles suivants peuvent traduire un texte en polonais. 

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     Polonais (<code>pl</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Portugais
{: #portuguese}

Les modèles suivants peuvent traduire un texte à partir du portugais.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     Portugais (<code>pt</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Russe
{: #russian}

Les modèles suivants peuvent traduire un texte en russe. 

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ru-en</code>
    </td>
    <td>
     Russe (<code>ru</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Espagnol
{: #spanish}

Les modèles suivants peuvent traduire un texte à partir de l'espagnol.

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     Espagnol (<code>es</code>)
    </td>
    <td>
     Catalan (<code>ca</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>es-en</code>
    </td>
    <td>
     Espagnol (<code>es</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>es-fr</code>
    </td>
    <td>
     Espagnol (<code>es</code>)
    </td>
    <td>
     Français (<code>fr</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Suédois
{: #swedish}

Les modèles suivants peuvent traduire un texte en suédois. 

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>sv-en</code>
    </td>
    <td>
     Suédois (<code>sv</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Turc
{: #turkish}

Les modèles suivants peuvent traduire un texte en turc. 

<table>
 <thead>
  <th>
   ID du modèle
  </th>
  <th>
   Source
  </th>
  <th>
   Cible
  </th>
  <th>
   Domaine
  </th>
  <th>
   Personnalisable
  </th>
  <tbody>
   <tr>
    <td>
     <code>tr-en</code>
    </td>
    <td>
     Turc (<code>tr</code>)
    </td>
    <td>
     Anglais (<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

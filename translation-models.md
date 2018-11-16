---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

# Translation models
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}} can translate the following languages.
Click a language in the list below to view a list of compatible translation models.

You can also use the **List models** API method to view the translation models that are available, including your custom models. You can filter results by language with the `source` and `target` parameters. The following example lists models that can translate English to Spanish.

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [Arabic](#arabic)
  - [Catalan](#catalan)
  - [Chinese (Simplified)](#chinese-simplified)
  - [Chinese (Traditional)](#chinese-traditional)
  - [Czech](#czech)
  - [Danish](#danish)
  - [Dutch](#dutch)
  - [English](#english)
  - [Finnish](#finnish)
  - [French](#french)
  - [German](#german)
  - [Hindi](#hindi)
  - [Hungarian](#hungarian)
  - [Italian](#italian)
  - [Japanese](#japanese)
  - [Korean](#korean)
  - [Norwegian Bokmål](#norwegian-bokmal)
  - [Polish](#polish)
  - [Portuguese](#portuguese)
  - [Russian](#russian)
  - [Spanish](#spanish)
  - [Swedish](#swedish)
  - [Turkish](#turkish)

## Arabic
{: #arabic}

The following models can translate Arabic text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ar-en</code>
    </td>
    <td>
     Arabic (<code>ar</code>)
    </td>
    <td>
     English (<code>en</code>)
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

The following models can translate Catalan text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
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
     Spanish (<code>es</code>)
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

## Chinese (Simplified)
{: #chinese-simplified}

The following models can translate Chinese (Simplified) text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     Simplified Chinese (<code>zh</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Chinese (Traditional)
{: #chinese-traditional}

The following models can translate Chinese (Traditional) text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     Traditional Chinese (<code>zh-TW</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Czech
{: #czech}

The following models can translate Czech text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     Czech (<code>cs</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Danish
{: #danish}

The following models can translate Danish text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     Danish (<code>da</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Dutch
{: #dutch}

The following models can translate Dutch text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     Dutch (<code>nl</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## English
{: #english}

The following models can translate English text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Arabic (<code>ar</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Czech (<code>cs</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Danish (<code>da</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     German (<code>de</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Spanish (<code>es</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Finnish (<code>fi</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     French (<code>fr</code>)
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
     English (<code>en</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Italian (<code>it</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Japanese (<code>ja</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Korean (<code>ko</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Norwegian Bokmal (<code>nb</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Dutch (<code>nl</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Polish (<code>pl</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Portuguese (<code>pt</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Russian (<code>ru</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Swedish (<code>sv</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Turkish (<code>tr</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Simplified Chinese (<code>zh</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Traditional Chinese (<code>zh-TW</code>)
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

## Finnish
{: #finnish}

The following models can translate Finnish text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     Finnish (<code>fi</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## French
{: #french}

The following models can translate French text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     French (<code>fr</code>)
    </td>
    <td>
     German (<code>de</code>)
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
     French (<code>fr</code>)
    </td>
    <td>
     English (<code>en</code>)
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
     French (<code>fr</code>)
    </td>
    <td>
     Spanish (<code>es</code>)
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

## German
{: #german}

The following models can translate German text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     German (<code>de</code>)
    </td>
    <td>
     English (<code>en</code>)
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
     German (<code>de</code>)
    </td>
    <td>
     French (<code>fr</code>)
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
     German (<code>de</code>)
    </td>
    <td>
     Italian (<code>it</code>)
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

The following models can translate Hindi text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
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
     English (<code>en</code>)
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

## Hungarian
{: #hungarian}

The following models can translate Hungarian text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>hu-en</code>
    </td>
    <td>
     Hungarian (<code>hu</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Italian
{: #italian}

The following models can translate Italian text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>it-de</code>
    </td>
    <td>
     Italian (<code>it</code>)
    </td>
    <td>
     German (<code>de</code>)
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
     Italian (<code>it</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Japanese
{: #japanese}

The following models can translate Japanese text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     Japanese (<code>ja</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Korean
{: #korean}

The following models can translate Korean text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ko-en</code>
    </td>
    <td>
     Korean (<code>ko</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Norwegian Bokmål
{: #norwegian-bokmal}

The following models can translate Norwegian Bokmål text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     Norwegian Bokmal (<code>nb</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Polish
{: #polish}

The following models can translate Polish text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     Polish (<code>pl</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Portuguese
{: #portuguese}

The following models can translate Portuguese text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     Portuguese (<code>pt</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Russian
{: #russian}

The following models can translate Russian text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ru-en</code>
    </td>
    <td>
     Russian (<code>ru</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Spanish
{: #spanish}

The following models can translate Spanish text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     Spanish (<code>es</code>)
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
     Spanish (<code>es</code>)
    </td>
    <td>
     English (<code>en</code>)
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
     Spanish (<code>es</code>)
    </td>
    <td>
     French (<code>fr</code>)
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

## Swedish
{: #swedish}

The following models can translate Swedish text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>sv-en</code>
    </td>
    <td>
     Swedish (<code>sv</code>)
    </td>
    <td>
     English (<code>en</code>)
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

## Turkish
{: #turkish}

The following models can translate Turkish text.

<table>
 <thead>
  <th>
   Model ID
  </th>
  <th>
   Source
  </th>
  <th>
   Target
  </th>
  <th>
   Domain
  </th>
  <th>
   Customizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>tr-en</code>
    </td>
    <td>
     Turkish (<code>tr</code>)
    </td>
    <td>
     English (<code>en</code>)
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

---

copyright:
  years: 2015, 2020
lastupdated: "2020-04-22"

keywords: translation models,list translation models,customizable models

subcollection: language-translator

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

# Supported languages for translation
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}} can translate from the following languages to any other language in the list, with the exception of Catalan. Click a language to see the customizable translation models for that language.

|Language|Language code|
|---|---|
|[Arabic](#arabic)|`ar`|
|[Bengali](#bengali)|`bn`|
|[Bulgarian](#bulgarian)|`bg`|
|[Catalan](#catalan)\*|`ca`|
|[Chinese (Simplified)](#chinese-simplified)|`zh`|
|[Chinese (Traditional)](#chinese-traditional)|`zh-TW`|
|[Croatian](#croatian)|`hr`|
|[Czech](#czech)|`cs`|
|[Danish](#danish)|`da`|
|[Dutch](#dutch)|`nl`|
|[English](#english)|`en`|
|[Estonian](#estonian)|`et`|
|[Finnish](#finnish)|`fi`|
|[French](#french)|`fr`|
|[German](#german)|`de`|
|[Greek](#greek)|`el`|
|[Gujarati](#gujarati)|`gu`|
|[Hebrew](#hebrew)|`he`|
|[Hindi](#hindi)|`hi`|
|[Hungarian](#hungarian)|`hu`|
|[Irish](#irish)|`ga`|
|[Indonesian](#indonesian)|`id`|
|[Italian](#italian)|`it`|
|[Japanese](#japanese)|`ja`|
|[Korean](#korean)|`ko`|
|[Latvian](#latvian)|`lv`|
|[Lithuanian](#lithuanian)|`li`|
|[Malay](#malay)|`ms`|
|[Malayalam](#malayalam)|`ml`|
|[Maltese](#maltese)|`mt`|
|[Norwegian Bokmål](#norwegian-bokmal)|`nb`|
|[Polish](#polish)|`pl`|
|[Portuguese](#portuguese)|`pt`|
|[Romanian](#romanian)|`ro`|
|[Russian](#russian)|`ru`|
|[Slovak](#slovak)|`sk`|
|[Slovenian](#slovenian)|`sl`|
|[Spanish](#spanish)|`es`|
|[Swedish](#swedish)|`sv`|
|[Tamil](#tamil)|`ta`|
|[Telugu](#telugu)|`te`|
|[Thai](#thai)|`th`|
|[Turkish](#turkish)|`tr`|
|[Urdu](#urdu)|`ur`|
|[Vietnamese](#Vietnamese)|`vi`|

\* Catalan is supported only for translation to and from Spanish.


## Customization support
{: #customization-support}

The following sections list the customizable translation models for each language.

You can also use the **List models** API method to view the translation models that support customization and any custom models that you have created. You can filter results by language with the `source` and `target` parameters. The following example lists models that can translate English to Spanish.

```sh
curl --user "apikey:{apikey}" "https://{url}/v3/models?source=en&target=es&version=2018-05-01"
```
{: pre}

### Arabic
{: #arabic}

The following Arabic translation models can be customized.

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

### Bengali
{: #bengali}

The following Bengali translation models can be customized.

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
     <code>bn-en</code>
    </td>
    <td>
     Bengali (<code>bn</code>)
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


### Bulgarian
{: #bulgarian}

The following Bulgarian translation models can be customized.

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
     <code>bg-en</code>
    </td>
    <td>
     Bulgarian (<code>bg</code>)
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

### Catalan
{: #catalan}

The following Catalan translation models can be customized.

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

### Chinese (Simplified)
{: #chinese-simplified}

The following Chinese (Simplified) translation models can be customized.

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

### Chinese (Traditional)
{: #chinese-traditional}

The following Chinese (Traditional) translation models can be customized.

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

### Croatian
{: #croatian}

The following Croatian translation models can be customized.

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
     <code>hr-en</code>
    </td>
    <td>
     Croatian (<code>hr</code>)
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

### Czech
{: #czech}

The following Czech translation models can be customized.

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

### Danish
{: #danish}

The following Danish translation models can be customized.

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

### Dutch
{: #dutch}

The following Dutch translation models can be customized.

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

### English
{: #english}

The following English translation models can be customized.

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
     <code>en-bg</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Bulgarian (<code>bg</code>)
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
     <code>en-el</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Greek (<code>el</code>)
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
     <code>en-et</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Estonian (<code>et</code>)
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
     <code>en-ga</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Irish (<code>ga</code>)
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
     English (<code>en</code>)
    </td>
    <td>
     Hebrew (<code>he</code>)
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
     <code>en-hr</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Croatian (<code>hr</code>)
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
     <code>en-id</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Indonesian (<code>id</code>)
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
     <code>en-lv</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Latvian (<code>lv</code>)
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
     <code>en-lt</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Lithuanian (<code>lt</code>)
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
     <code>en-ms</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Malay (<code>ms</code>)
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
     <code>en-ro</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Romanian (<code>ro</code>)
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
     <code>en-sk</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Slovak (<code>sk</code>)
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
     <code>en-sl</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Slovenian (<code>sl</code>)
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
     <code>en-th</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Thai (<code>th</code>)
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
   <tr>
    <td>
     <code>en-ur</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Urdu (<code>ur</code>)
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
     <code>en-vi</code>
    </td>
    <td>
     English (<code>en</code>)
    </td>
    <td>
     Vietnamese (<code>vi</code>)
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

### Estonian
{: #estonian}

The following Estonian translation models can be customized.

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
     <code>et-en</code>
    </td>
    <td>
     Estonian (<code>et</code>)
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

### Finnish
{: #finnish}

The following Finnish translation models can be customized.

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

### French
{: #french}

The following French translation models can be customized.

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

### German
{: #german}

The following German translation models can be customized.

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

### Greek
{: #greek}

The following Greek translation models can be customized.

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
     <code>el-en</code>
    </td>
    <td>
     Greek (<code>el</code>)
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

### Gujarati
{: #gujarati}

The following Gujarati translation models can be customized.

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
     <code>gu-en</code>
    </td>
    <td>
     Gujarati (<code>gu</code>)
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


### Hebrew
{: #hebrew}

The following Hebrew translation models can be customized.

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
     <code>he-en</code>
    </td>
    <td>
     Hebrew (<code>he</code>)
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


### Hindi
{: #hindi}

The following Hindi translation models can be customized.

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

### Hungarian
{: #hungarian}

The following Hungarian translation models can be customized.

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

### Indonesian
{: #indonesian}

The following Indonesian translation models can be customized.

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
     <code>id-en</code>
    </td>
    <td>
     Indonesian (<code>id</code>)
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

### Irish
{: #irish}

The following Irish translation models can be customized.

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
     <code>ga-en</code>
    </td>
    <td>
     Irish (<code>ga</code>)
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

### Italian
{: #italian}

The following Italian translation models can be customized.

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

### Japanese
{: #japanese}

The following Japanese translation models can be customized.

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

### Korean
{: #korean}

The following Korean translation models can be customized.

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

### Latvian
{: #latvian}

The following Latvian translation models can be customized.

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
     <code>lv-en</code>
    </td>
    <td>
     Latvian (<code>lv</code>)
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

### Lithuanian
{: #lithuanian}

The following Lithuanian translation models can be customized.

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
     <code>lt-en</code>
    </td>
    <td>
     Lithuanian (<code>lt</code>)
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

### Malay
{: #malay}

The following Malay translation models can be customized.

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
     <code>ms-en</code>
    </td>
    <td>
     Malay (<code>ms</code>)
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

### Malayalam
{: #malayalam}

The following Malayalam translation models can be customized.

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
     <code>ml-en</code>
    </td>
    <td>
     Malayalam (<code>ml</code>)
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

### Maltese
{: #maltese}

The following Maltese translation models can be customized.

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
     <code>mt-en</code>
    </td>
    <td>
     Maltese (<code>mt</code>)
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

### Norwegian Bokmål
{: #norwegian-bokmal}

The following Norwegian Bokmål translation models can be customized.

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

### Polish
{: #polish}

The following Polish translation models can be customized.

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

### Portuguese
{: #portuguese}

The following Portuguese translation models can be customized.

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

### Romanian
{: #romanian}

The following Romanian translation models can be customized.

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
     <code>ro-en</code>
    </td>
    <td>
     Romanian (<code>ro</code>)
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

### Russian
{: #russian}

The following Russian translation models can be customized.

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

### Slovak
{: #slovak}

The following Slovak translation models can be customized.

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
     <code>sk-en</code>
    </td>
    <td>
     Slovak (<code>sk</code>)
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

### Slovenian
{: #slovenian}

The following Slovenian translation models can be customized.

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
     <code>sl-en</code>
    </td>
    <td>
     Slovenian (<code>sl</code>)
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

### Spanish
{: #spanish}

The following Spanish translation models can be customized.

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

### Swedish
{: #swedish}

The following Swedish translation models can be customized.

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

### Tamil
{: #tamil}

The following Tamil translation models can be customized.

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
     <code>ta-en</code>
    </td>
    <td>
     Tamil (<code>ta</code>)
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

### Telugu
{: #telugu}

The following Telugu translation models can be customized.

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
     <code>te-en</code>
    </td>
    <td>
     Telugu (<code>te</code>)
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

### Thai
{: #thai}

The following Thai translation models can be customized.

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
     <code>th-en</code>
    </td>
    <td>
     Thai (<code>th</code>)
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

### Turkish
{: #turkish}

The following Turkish translation models can be customized.

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

### Urdu
{: #urdu}

The following Urdu translation models can be customized.

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
     <code>ur-en</code>
    </td>
    <td>
     Urdu (<code>ur</code>)
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

### Vietnamese
{: #vietnamese}

The following Vietnamese translation models can be customized.

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
     <code>vi-en</code>
    </td>
    <td>
     Vietnamese (<code>vi</code>)
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

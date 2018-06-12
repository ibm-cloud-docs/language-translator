---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

# v3 Translation models
{: #translation-models}

This page lists translation models for the v3 API. The translation models for the v2 API are listed in [Translation models (v2)](translation-models-v2.html). 
{: tip}

{{site.data.keyword.languagetranslatorshort}} can translate the following languages.
Click a language in the list below to view a list of compatible translation models.

You can also use the **List models** API method to view the translation models that are available, including your custom models. You can filter results by language with the `source` and `target` parameters. The following example lists models that can translate English to Spanish.

```bash
curl --user {username}:{password} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}




  - [Arabic](#arabic)
  - [Chinese (Simplified)](#chinese-simplified)
  - [Chinese (Traditional)](#chinese-traditional)
  - [Dutch](#dutch)
  - [English](#english)
  - [French](#french)
  - [German](#german)
  - [Italian](#italian)
  - [Japanese](#japanese)
  - [Korean](#korean)
  - [Polish](#polish)
  - [Portuguese](#portuguese)
  - [Russian](#russian)
  - [Spanish](#spanish)
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
     ar-en
    </td>
    <td>
     Arabic (ar)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     zh-en
    </td>
    <td>
     Simplified Chinese (zh)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## Chinese (Traditional)
{: #chinese-traditional}

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
     zh-TW-en
    </td>
    <td>
     Traditional Chinese (zh-TW)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     nl-en
    </td>
    <td>
     Dutch (nl)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     en-ar
    </td>
    <td>
     English (en)
    </td>
    <td>
     Arabic (ar)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-de
    </td>
    <td>
     English (en)
    </td>
    <td>
     German (de)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-es
    </td>
    <td>
     English (en)
    </td>
    <td>
     Spanish (es)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-fr
    </td>
    <td>
     English (en)
    </td>
    <td>
     French (fr)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-it
    </td>
    <td>
     English (en)
    </td>
    <td>
     Italian (it)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-ja
    </td>
    <td>
     English (en)
    </td>
    <td>
     Japanese (ja)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-ko
    </td>
    <td>
     English (en)
    </td>
    <td>
     Korean (ko)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-nl
    </td>
    <td>
     English (en)
    </td>
    <td>
     Dutch (nl)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-pl
    </td>
    <td>
     English (en)
    </td>
    <td>
     Polish (pl)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-pt
    </td>
    <td>
     English (en)
    </td>
    <td>
     Portuguese (pt)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-ru
    </td>
    <td>
     English (en)
    </td>
    <td>
     Russian (ru)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-tr
    </td>
    <td>
     English (en)
    </td>
    <td>
     Turkish (tr)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-zh
    </td>
    <td>
     English (en)
    </td>
    <td>
     Simplified Chinese (zh)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-zh-TW
    </td>
    <td>
     English (en)
    </td>
    <td>
     Traditional Chinese (zh-TW)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     fr-de
    </td>
    <td>
     French (fr)
    </td>
    <td>
     German (de)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     fr-en
    </td>
    <td>
     French (fr)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     fr-es
    </td>
    <td>
     French (fr)
    </td>
    <td>
     Spanish (es)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     de-en
    </td>
    <td>
     German (de)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     de-fr
    </td>
    <td>
     German (de)
    </td>
    <td>
     French (fr)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     de-it
    </td>
    <td>
     German (de)
    </td>
    <td>
     Italian (it)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     it-de
    </td>
    <td>
     Italian (it)
    </td>
    <td>
     German (de)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     it-en
    </td>
    <td>
     Italian (it)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     ja-en
    </td>
    <td>
     Japanese (ja)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     ko-en
    </td>
    <td>
     Korean (ko)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     pl-en
    </td>
    <td>
     Polish (pl)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     pt-en
    </td>
    <td>
     Portuguese (pt)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     ru-en
    </td>
    <td>
     Russian (ru)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     es-en
    </td>
    <td>
     Spanish (es)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     es-fr
    </td>
    <td>
     Spanish (es)
    </td>
    <td>
     French (fr)
    </td>
    <td>
     general
    </td>
    <td>
     true
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
     tr-en
    </td>
    <td>
     Turkish (tr)
    </td>
    <td>
     English (en)
    </td>
    <td>
     general
    </td>
    <td>
     true
    </td>
   </tr>
  </tbody>
 </thead>
</table>


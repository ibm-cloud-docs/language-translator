---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-27"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

# v2 Translation models
{: #translation-models-v2}

Language Translator v3 is now available. **The v2 Language Translator API will no longer be available after July 31, 2018.** To take advantage of the latest service enhancements, migrate to the v3 API. View the [Migrating to Language Translator v3](migrating.html) page for more information.
{: tip}

{{site.data.keyword.languagetranslatorshort}} can translate the following languages.
Click a language in the list below to view a list of compatible translation models. 


  - [Arabic](#arabic)
  - [Chinese (Simplified)](#chinese-simplified)
  - [Chinese (Traditional)](#chinese-traditional)
  - [Dutch](#dutch)
  - [Egyptian Arabic](#egyptian-arabic)
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     ar-en-conversational
    </td>
    <td>
     Arabic (ar)
    </td>
    <td>
     English (en)
    </td>
    <td>
     conversational
    </td>
    <td>
     false
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
     zh-en&ast;
    </td>
    <td>
     Chinese (zh)
    </td>
    <td>
     English (en)
    </td>
    <td>
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     zh-en-patent
    </td>
    <td>
     Chinese (zh)
    </td>
    <td>
     English (en)
    </td>
    <td>
     patent
    </td>
    <td>
     false
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 

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
     zht-en&ast;
    </td>
    <td>
     Traditional Chinese (zht)
    </td>
    <td>
     English (en)
    </td>
    <td>
     news
    </td>
    <td>
     false
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 


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
     nl-en&ast;
    </td>
    <td>
     Dutch (nl)
    </td>
    <td>
     English (en)
    </td>
    <td>
     news
    </td>
    <td>
     true
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 


## Egyptian Arabic
{: #egyptian-arabic}

The following models can translate Egyptian Arabic text.

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
     arz-en
    </td>
    <td>
     Egyptian Arabic (arz)
    </td>
    <td>
     English (en)
    </td>
    <td>
     news
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-ar-conversational
    </td>
    <td>
     English (en)
    </td>
    <td>
     Arabic (ar)
    </td>
    <td>
     conversational
    </td>
    <td>
     false
    </td>
   </tr>
   <tr>
    <td>
     en-arz
    </td>
    <td>
     English (en)
    </td>
    <td>
     Egyptian Arabic (arz)
    </td>
    <td>
     news
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
     news
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-es-conversational
    </td>
    <td>
     English (en)
    </td>
    <td>
     Spanish (es)
    </td>
    <td>
     conversational
    </td>
    <td>
     false
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-fr-conversational
    </td>
    <td>
     English (en)
    </td>
    <td>
     French (fr)
    </td>
    <td>
     conversational
    </td>
    <td>
     false
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
     news
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
     news
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-nl&ast;
    </td>
    <td>
     English (en)
    </td>
    <td>
     Dutch (nl)
    </td>
    <td>
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-pl&ast;
    </td>
    <td>
     English (en)
    </td>
    <td>
     Polish (pl)
    </td>
    <td>
     news
    </td>
    <td>
     false
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-pt-conversational
    </td>
    <td>
     English (en)
    </td>
    <td>
     Portuguese (pt)
    </td>
    <td>
     conversational
    </td>
    <td>
     false
    </td>
   </tr>
   <tr>
    <td>
     en-ru&ast;
    </td>
    <td>
     English (en)
    </td>
    <td>
     Russian (ru)
    </td>
    <td>
     news
    </td>
    <td>
     false
    </td>
   </tr>
   <tr>
    <td>
     en-tr&ast;
    </td>
    <td>
     English (en)
    </td>
    <td>
     Turkish (tr)
    </td>
    <td>
     news
    </td>
    <td>
     false
    </td>
   </tr>
   <tr>
    <td>
     en-zh&ast;
    </td>
    <td>
     English (en)
    </td>
    <td>
     Chinese (zh)
    </td>
    <td>
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     en-zht&ast;
    </td>
    <td>
     English (en)
    </td>
    <td>
     Traditional Chinese (zht)
    </td>
    <td>
     news
    </td>
    <td>
     false
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 


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
     fr-de&ast;
    </td>
    <td>
     French (fr)
    </td>
    <td>
     German (de)
    </td>
    <td>
     news
    </td>
    <td>
     false
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     fr-en-conversational
    </td>
    <td>
     French (fr)
    </td>
    <td>
     English (en)
    </td>
    <td>
     conversational
    </td>
    <td>
     false
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 

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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     de-fr&ast;
    </td>
    <td>
     German (de)
    </td>
    <td>
     French (fr)
    </td>
    <td>
     news
    </td>
    <td>
     false
    </td>
   </tr>
   <tr>
    <td>
     de-it&ast;
    </td>
    <td>
     German (de)
    </td>
    <td>
     Italian (it)
    </td>
    <td>
     news
    </td>
    <td>
     false
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 

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
     it-de&ast;
    </td>
    <td>
     Italian (it)
    </td>
    <td>
     German (de)
    </td>
    <td>
     news
    </td>
    <td>
     false
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 

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
     news
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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     ko-en-patent
    </td>
    <td>
     Korean (ko)
    </td>
    <td>
     English (en)
    </td>
    <td>
     patent
    </td>
    <td>
     false
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
     pl-en&ast;
    </td>
    <td>
     Polish (pl)
    </td>
    <td>
     English (en)
    </td>
    <td>
     news
    </td>
    <td>
     false
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 


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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     pt-en-conversational
    </td>
    <td>
     Portuguese (pt)
    </td>
    <td>
     English (en)
    </td>
    <td>
     conversational
    </td>
    <td>
     false
    </td>
   </tr>
   <tr>
    <td>
     pt-en-patent
    </td>
    <td>
     Portuguese (pt)
    </td>
    <td>
     English (en)
    </td>
    <td>
     patent
    </td>
    <td>
     false
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
     ru-en&ast;
    </td>
    <td>
     Russian (ru)
    </td>
    <td>
     English (en)
    </td>
    <td>
     news
    </td>
    <td>
     false
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 


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
     news
    </td>
    <td>
     true
    </td>
   </tr>
   <tr>
    <td>
     es-en-conversational
    </td>
    <td>
     Spanish (es)
    </td>
    <td>
     English (en)
    </td>
    <td>
     conversational
    </td>
    <td>
     false
    </td>
   </tr>
   <tr>
    <td>
     es-en-patent
    </td>
    <td>
     Spanish (es)
    </td>
    <td>
     English (en)
    </td>
    <td>
     patent
    </td>
    <td>
     false
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
     news
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
     tr-en&ast;
    </td>
    <td>
     Turkish (tr)
    </td>
    <td>
     English (en)
    </td>
    <td>
     news
    </td>
    <td>
     false
    </td>
   </tr>
  </tbody>
 </thead>
</table>

\* This model is only available through the [Neural Machine Translation preview](release-notes.html#12-january-2018). 


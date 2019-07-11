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

# Übersetzungsmodelle
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}} bietet einen Übersetzungsservice für die nachfolgend aufgeführten Sprachen.
Klicken Sie auf eine Sprache in der folgenden Liste, um eine Liste kompatibler Übersetzungsmodelle aufzurufen.

Sie können auch die API-Methode zum **Auflisten von Modellen** verwenden, um die verfügbaren Übersetzungsmodelle, einschließlich Ihrer angepassten Modelle, anzuzeigen. Sie können die Ergebnisse mit den Parametern `source` und `target` nach der Sprache filtern. Im folgenden Beispiel werden Modelle aufgelistet, die aus dem Englischen ins Spanische übersetzen können.

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [Arabisch](#arabic)
  - [Katalanisch](#catalan)
  - [Chinesisch (vereinfacht)](#chinese-simplified)
  - [Chinesisch (traditionell)](#chinese-traditional)
  - [Tschechisch](#czech)
  - [Dänisch](#danish)
  - [Niederländisch](#dutch)
  - [Englisch](#english)
  - [Finnisch](#finnish)
  - [Französisch](#french)
  - [Deutsch](#german)
  - [Griechisch](#greek)
  - [Hebräisch](#hebrew)
  - [Hindi](#hindi)
  - [Ungarisch](#hungarian)
  - [Italienisch](#italian)
  - [Japanisch](#japanese)
  - [Koreanisch](#korean)
  - [Norwegisch (Bokmål)](#norwegian-bokmal)
  - [Polnisch](#polish)
  - [Portugiesisch](#portuguese)
  - [Russisch](#russian)
  - [Spanisch](#spanish)
  - [Schwedisch](#swedish)
  - [Türkisch](#turkish)

## Arabisch
{: #arabic}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung arabischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>ar-en</code>
    </td>
    <td>
     Arabisch (<code>ar</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Katalanisch
{: #catalan}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung katalanischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>ca-es</code>
    </td>
    <td>
     Katalanisch (<code>ca</code>)
    </td>
    <td>
     Spanisch (<code>es</code>)
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

## Chinesisch (vereinfacht)
{: #chinese-simplified}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung chinesischer Texte (vereinfachtes Chinesisch) möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     Vereinfachtes Chinesisch (<code>zh</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Chinesisch (Traditionell)
{: #chinese-traditional}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung chinesischer Texte (traditionelles Chinesisch) möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     Traditionelles Chinesisch (<code>zh-TW</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Tschechisch
{: #czech}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung tschechischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     Tschechisch (<code>cs</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Dänisch
{: #danish}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung dänischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     Dänisch (<code>da</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Niederländisch
{: #dutch}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung niederländischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     Niederländisch (<code>nl</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Englisch
{: #english}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung englischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     Englisch (<code>en</code>)
    </td>
    <td>
     Arabisch (<code>ar</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Tschechisch (<code>cs</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Dänisch (<code>da</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Deutsch (<code>de</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Griechisch (<code>el</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Spanisch (<code>es</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Finnisch (<code>fi</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Französisch (<code>fr</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Hebräisch (<code>he</code>)
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
     Englisch (<code>en</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Italienisch (<code>it</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Japanisch (<code>ja</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Koreanisch (<code>ko</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Norwegisch ((Bokmål) (<code>nb</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Niederländisch (<code>nl</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Polnisch (<code>pl</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Portugiesisch (<code>pt</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Russisch (<code>ru</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Schwedisch (<code>sv</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Türkisch (<code>tr</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Vereinfachtes Chinesisch (<code>zh</code>)
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
     Englisch (<code>en</code>)
    </td>
    <td>
     Traditionelles Chinesisch (<code>zh-TW</code>)
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

## Finnisch
{: #finnish}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung finnischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     Finnisch (<code>fi</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Französisch
{: #french}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung französischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     Französisch (<code>fr</code>)
    </td>
    <td>
     Deutsch (<code>de</code>)
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
     Französisch (<code>fr</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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
     Französisch (<code>fr</code>)
    </td>
    <td>
     Spanisch (<code>es</code>)
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

## Deutsch
{: #german}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung deutscher Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     Deutsch (<code>de</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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
     Deutsch (<code>de</code>)
    </td>
    <td>
     Französisch (<code>fr</code>)
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
     Deutsch (<code>de</code>)
    </td>
    <td>
     Italienisch (<code>it</code>)
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

## Griechisch
{: #greek}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung griechischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>el-en</code>
    </td>
    <td>
     Griechisch (<code>el</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Hebräisch
{: #hebrew}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung hebräischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>he-en</code>
    </td>
    <td>
     Hebräisch (<code>he</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung von Hindi-Texten möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
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
     Englisch (<code>en</code>)
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

## Ungarisch
{: #hungarian}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung ungarischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>hu-en</code>
    </td>
    <td>
     Ungarisch (<code>hu</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Italienisch
{: #italian}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung italienischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>it-de</code>
    </td>
    <td>
     Italienisch (<code>it</code>)
    </td>
    <td>
     Deutsch (<code>de</code>)
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
     Italienisch (<code>it</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Japanisch
{: #japanese}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung japanischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     Japanisch (<code>ja</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Koreanisch
{: #korean}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung koreanischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>ko-en</code>
    </td>
    <td>
     Koreanisch (<code>ko</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Norwegisch (Bokmål)
{: #norwegian-bokmal}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung von norwegischen Texte (Bokmål) möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     Norwegisch ((Bokmål) (<code>nb</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Polnisch
{: #polish}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung polnischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     Polnisch (<code>pl</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Portugiesisch
{: #portuguese}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung portugiesischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     Portugiesisch (<code>pt</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Russisch
{: #russian}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung russischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>ru-en</code>
    </td>
    <td>
     Russisch (<code>ru</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Spanisch
{: #spanish}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung spanischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     Spanisch (<code>es</code>)
    </td>
    <td>
     Katalanisch (<code>ca</code>)
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
     Spanisch (<code>es</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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
     Spanisch (<code>es</code>)
    </td>
    <td>
     Französisch (<code>fr</code>)
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

## Schwedisch
{: #swedish}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung schwedischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>sv-en</code>
    </td>
    <td>
     Schwedisch (<code>sv</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

## Türkisch
{: #turkish}

Mit den nachfolgend aufgeführten Modellen ist die Übersetzung türkischer Texte möglich.

<table>
 <thead>
  <th>
   Modell-ID
  </th>
  <th>
   Quelle
  </th>
  <th>
   Ziel
  </th>
  <th>
   Domäne
  </th>
  <th>
   Anpassungsfähigkeit
  </th>
  <tbody>
   <tr>
    <td>
     <code>tr-en</code>
    </td>
    <td>
     Türkisch (<code>tr</code>)
    </td>
    <td>
     Englisch (<code>en</code>)
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

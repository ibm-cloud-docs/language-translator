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

# Modelli di traduzione
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}} può tradurre le seguenti lingue.
Fai clic su una lingua nel seguente elenco per visualizzare un elenco di modelli di traduzione compatibili.

Puoi anche utilizzare il metodo API **List models** per visualizzare i modelli di traduzione disponibili, inclusi i tuoi modelli personalizzati. Puoi filtrare i risultati in base alla lingua con i parametri `source` e `target`. Il seguente esempio elenca i modelli che possono tradurre l'inglese in spagnolo.

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [Arabo](#arabic)
  - [Catalano](#catalan)
  - [Cinese (semplificato)](#chinese-simplified)
  - [Cinese (tradizionale)](#chinese-traditional)
  - [Ceco](#czech)
  - [Danese](#danish)
  - [Olandese](#dutch)
  - [Inglese](#english)
  - [Finlandese](#finnish)
  - [Francese](#french)
  - [Tedesco](#german)
  - [Greco](#greek)
  - [Ebraico](#hebrew)
  - [Hindi](#hindi)
  - [Ungherese](#hungarian)
  - [Italiano](#italian)
  - [Giapponese](#japanese)
  - [Coreano](#korean)
  - [Norvegese (Bokmål)](#norwegian-bokmal)
  - [Polacco](#polish)
  - [Portoghese](#portuguese)
  - [Russo](#russian)
  - [Spagnolo](#spanish)
  - [Svedese](#swedish)
  - [Turco](#turkish)

## Arabo
{: #arabic}

I seguenti modelli possono tradurre testo in arabo.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>ar-en</code>
    </td>
    <td>
     Arabo (<code>ar</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Catalano
{: #catalan}

I seguenti modelli possono tradurre testo in catalano.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>ca-es</code>
    </td>
    <td>
     Catalano (<code>ca</code>)
    </td>
    <td>
     Spagnolo (<code>es</code>)
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

## Cinese (semplificato)
{: #chinese-simplified}

I seguenti modelli possono tradurre testo in cinese (semplificato).

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     Cinese semplificato (<code>zh</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Cinese (tradizionale)
{: #chinese-traditional}

I seguenti modelli possono tradurre testo in cinese (tradizionale).

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     Cinese tradizionale (<code>zh-TW</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Ceco
{: #czech}

I seguenti modelli possono tradurre testo in ceco.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     Ceco (<code>cs</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Danese
{: #danish}

I seguenti modelli possono tradurre testo in danese.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     Danese (<code>da</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Olandese
{: #dutch}

I seguenti modelli possono tradurre testo in olandese.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     Olandese (<code>nl</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Inglese
{: #english}

I seguenti modelli possono tradurre testo in inglese.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     Inglese (<code>en</code>)
    </td>
    <td>
     Arabo (<code>ar</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Ceco (<code>cs</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Danese (<code>da</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Tedesco (<code>de</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Greco (<code>el</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Spagnolo (<code>es</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Finlandese (<code>fi</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Francese (<code>fr</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Ebraico (<code>he</code>)
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
     Inglese (<code>en</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Italiano (<code>it</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Giapponese (<code>ja</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Coreano (<code>ko</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Norvegese (Bokmål) (<code>nb</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Olandese (<code>nl</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Polacco (<code>pl</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Portoghese (<code>pt</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Russo (<code>ru</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Svedese (<code>sv</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Turco (<code>tr</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Cinese semplificato (<code>zh</code>)
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
     Inglese (<code>en</code>)
    </td>
    <td>
     Cinese tradizionale (<code>zh-TW</code>)
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

## Finlandese
{: #finnish}

I seguenti modelli possono tradurre testo in finlandese.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     Finlandese (<code>fi</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Francese
{: #french}

I seguenti modelli possono tradurre testo in francese.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     Francese (<code>fr</code>)
    </td>
    <td>
     Tedesco (<code>de</code>)
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
     Francese (<code>fr</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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
     Francese (<code>fr</code>)
    </td>
    <td>
     Spagnolo (<code>es</code>)
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

## Tedesco
{: #german}

I seguenti modelli possono tradurre testo in tedesco.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     Tedesco (<code>de</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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
     Tedesco (<code>de</code>)
    </td>
    <td>
     Francese (<code>fr</code>)
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
     Tedesco (<code>de</code>)
    </td>
    <td>
     Italiano (<code>it</code>)
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

## Greco
{: #greek}

I seguenti modelli possono tradurre testo in greco.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>el-en</code>
    </td>
    <td>
     Greco (<code>el</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Ebraico
{: #hebrew}

I seguenti modelli possono tradurre testo in ebraico.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>he-en</code>
    </td>
    <td>
     Ebraico (<code>he</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

I seguenti modelli possono tradurre testo in hindi.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
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
     Inglese (<code>en</code>)
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

## Ungherese
{: #hungarian}

I seguenti modelli possono tradurre testo in ungherese.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>hu-en</code>
    </td>
    <td>
     Ungherese (<code>hu</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Italiano
{: #italian}

I seguenti modelli possono tradurre testo in italiano.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>it-de</code>
    </td>
    <td>
     Italiano (<code>it</code>)
    </td>
    <td>
     Tedesco (<code>de</code>)
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
     Italiano (<code>it</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Giapponese
{: #japanese}

I seguenti modelli possono tradurre testo in giapponese.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     Giapponese (<code>ja</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Coreano
{: #korean}

I seguenti modelli possono tradurre testo in coreano.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>ko-en</code>
    </td>
    <td>
     Coreano (<code>ko</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Norvegese (Bokmål)
{: #norwegian-bokmal}

I seguenti modelli possono tradurre testo in norvegese (Bokmål).

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     Norvegese (Bokmål) (<code>nb</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Polacco
{: #polish}

I seguenti modelli possono tradurre testo in polacco.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     Polacco (<code>pl</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Portoghese
{: #portuguese}

I seguenti modelli possono tradurre testo in portoghese.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     Portoghese (<code>pt</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Russo
{: #russian}

I seguenti modelli possono tradurre testo in russo.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>ru-en</code>
    </td>
    <td>
     Russo (<code>ru</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Spagnolo
{: #spanish}

I seguenti modelli possono tradurre testo in spagnolo.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     Spagnolo (<code>es</code>)
    </td>
    <td>
     Catalano (<code>ca</code>)
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
     Spagnolo (<code>es</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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
     Spagnolo (<code>es</code>)
    </td>
    <td>
     Francese (<code>fr</code>)
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

## Svedese
{: #swedish}

I seguenti modelli possono tradurre testo in svedese.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>sv-en</code>
    </td>
    <td>
     Svedese (<code>sv</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

## Turco
{: #turkish}

I seguenti modelli possono tradurre testo in turco.

<table>
 <thead>
  <th>
   ID modello
  </th>
  <th>
   Origine
  </th>
  <th>
   Destinazione
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizzabile
  </th>
  <tbody>
   <tr>
    <td>
     <code>tr-en</code>
    </td>
    <td>
     Turco (<code>tr</code>)
    </td>
    <td>
     Inglese (<code>en</code>)
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

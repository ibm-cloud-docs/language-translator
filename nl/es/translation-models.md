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

# Modelos de traducción
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}} puede traducir los siguientes idiomas.
Pulse un idioma en la lista siguiente para ver una lista de modelos de traducción compatibles.

También puede utilizar el método de la API **Listar modelos** para ver los modelos de traducción que están disponibles, incluidos los modelos personalizados. Puede filtrar los resultados por idioma con los parámetros `source` y `target`. En el ejemplo siguiente se muestran los modelos que pueden traducir de inglés a español.

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [Árabe](#arabic)
  - [Catalán](#catalan)
  - [Chino (simplificado)](#chinese-simplified)
  - [Chino (tradicional)](#chinese-traditional)
  - [Checo](#czech)
  - [Danés](#danish)
  - [Holandés](#dutch)
  - [Inglés](#english)
  - [Finés](#finnish)
  - [Francés](#french)
  - [Alemán](#german)
  - [Griego](#greek)
  - [Hebreo](#hebrew)
  - [Hindi](#hindi)
  - [Húngaro](#hungarian)
  - [Italiano](#italian)
  - [Japonés](#japanese)
  - [Coreano](#korean)
  - [Noruego bokmål](#norwegian-bokmal)
  - [Polaco](#polish)
  - [Portugués](#portuguese)
  - [Ruso](#russian)
  - [Español](#spanish)
  - [Sueco](#swedish)
  - [Turco](#turkish)

## Árabe
{: #arabic}

Los siguientes modelos pueden traducir texto en árabe.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ar-en</code>
    </td>
    <td>
     Árabe (<code>ar</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Catalán
{: #catalan}

Los siguientes modelos pueden traducir texto en catalán.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ca-es</code>
    </td>
    <td>
     Catalán (<code>ca</code>)
    </td>
    <td>
     Español (<code>es</code>)
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

## Chino (simplificado)
{: #chinese-simplified}

Los siguientes modelos pueden traducir texto en chino (simplificado).

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     Chino simplificado (<code>zh</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Chino (tradicional)
{: #chinese-traditional}

Los siguientes modelos pueden traducir texto en chino (tradicional).

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     Chino tradicional (<code>zh-TW</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Checo
{: #czech}

Los siguientes modelos pueden traducir texto en checo.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     Checo (<code>cs</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Danés
{: #danish}

Los siguientes modelos pueden traducir texto en danés.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     Danés (<code>da</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Holandés
{: #dutch}

Los siguientes modelos pueden traducir texto en holandés.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     Holandés (<code>nl</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Inglés
{: #english}

Los siguientes modelos pueden traducir texto en inglés.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     Inglés (<code>en</code>)
    </td>
    <td>
     Árabe (<code>ar</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Checo (<code>cs</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Danés (<code>da</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Alemán (<code>de</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Griego (<code>el</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Español (<code>es</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Finés (<code>fi</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Francés (<code>fr</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Hebreo (<code>he</code>)
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
     Inglés (<code>en</code>)
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
     Inglés (<code>en</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Japonés (<code>ja</code>)
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
     Inglés (<code>en</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Noruego bokmål (<code>nb</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Holandés (<code>nl</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Polaco (<code>pl</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Portugués (<code>pt</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Ruso (<code>ru</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Sueco (<code>sv</code>)
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
     Inglés (<code>en</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Chino simplificado (<code>zh</code>)
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
     Inglés (<code>en</code>)
    </td>
    <td>
     Chino tradicional (<code>zh-TW</code>)
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

## Finés
{: #finnish}

Los siguientes modelos pueden traducir texto en finés.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     Finés (<code>fi</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Francés
{: #french}

Los siguientes modelos pueden traducir texto en francés.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     Francés (<code>fr</code>)
    </td>
    <td>
     Alemán (<code>de</code>)
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
     Francés (<code>fr</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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
     Francés (<code>fr</code>)
    </td>
    <td>
     Español (<code>es</code>)
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

## Alemán
{: #german}

Los siguientes modelos pueden traducir texto en alemán.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     Alemán (<code>de</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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
     Alemán (<code>de</code>)
    </td>
    <td>
     Francés (<code>fr</code>)
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
     Alemán (<code>de</code>)
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

## Griego
{: #greek}

Los siguientes modelos pueden traducir texto en griego.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>el-en</code>
    </td>
    <td>
     Griego (<code>el</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Hebreo
{: #hebrew}

Los siguientes modelos pueden traducir texto en hebreo.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>he-en</code>
    </td>
    <td>
     Hebreo (<code>he</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

Los siguientes modelos pueden traducir texto en hindi.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
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
     Inglés (<code>en</code>)
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

## Húngaro
{: #hungarian}

Los siguientes modelos pueden traducir texto en húngaro.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>hu-en</code>
    </td>
    <td>
     Húngaro (<code>hu</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

Los siguientes modelos pueden traducir texto en italiano.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
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
     Alemán (<code>de</code>)
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
     Inglés (<code>en</code>)
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

## Japonés
{: #japanese}

Los siguientes modelos pueden traducir texto en japonés.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     Japonés (<code>ja</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

Los siguientes modelos pueden traducir texto en coreano.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
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
     Inglés (<code>en</code>)
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

## Noruego bokmål
{: #norwegian-bokmal}

Los siguientes modelos pueden traducir texto en noruego bokmål.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     Noruego bokmål (<code>nb</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Polaco
{: #polish}

Los siguientes modelos pueden traducir texto en polaco.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     Polaco (<code>pl</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Portugués
{: #portuguese}

Los siguientes modelos pueden traducir texto en portugués.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     Portugués (<code>pt</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Ruso
{: #russian}

Los siguientes modelos pueden traducir texto en ruso.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>ru-en</code>
    </td>
    <td>
     Ruso (<code>ru</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

## Español
{: #spanish}

Los siguientes modelos pueden traducir texto en español.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     Español (<code>es</code>)
    </td>
    <td>
     Catalán (<code>ca</code>)
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
     Español (<code>es</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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
     Español (<code>es</code>)
    </td>
    <td>
     Francés (<code>fr</code>)
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

## Sueco
{: #swedish}

Los siguientes modelos pueden traducir texto en sueco.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
  </th>
  <tbody>
   <tr>
    <td>
     <code>sv-en</code>
    </td>
    <td>
     Sueco (<code>sv</code>)
    </td>
    <td>
     Inglés (<code>en</code>)
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

Los siguientes modelos pueden traducir texto en turco.

<table>
 <thead>
  <th>
   ID de modelo
  </th>
  <th>
   Origen
  </th>
  <th>
   Destino
  </th>
  <th>
   Dominio
  </th>
  <th>
   Personalizable
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
     Inglés (<code>en</code>)
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

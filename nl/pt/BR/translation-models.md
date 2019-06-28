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

# Modelos de tradução
{: #translation-models}

O {{site.data.keyword.languagetranslatorshort}} pode traduzir os seguintes idiomas.
Clique em um idioma na lista abaixo para visualizar uma lista de modelos de tradução compatíveis.

Também é possível usar o método de API **Listar modelos** para visualizar os modelos de tradução que estão disponíveis, incluindo seus modelos customizados. É possível filtrar os resultados por idioma com os parâmetros `source` e `target`. O exemplo a seguir lista os modelos que podem traduzir inglês para espanhol.

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [Árabe](#arabic)
  - [Catalão](#catalan)
  - [Chinês (simplificado)](#chinese-simplified)
  - [Chinês (Tradicional)](#chinese-traditional)
  - [     Tcheco
    ](#czech)
  - [     Dinamarquês
    ](#danish)
  - [     Holandês
    ](#dutch)
  - [Inglês](#english)
  - [     Finlandês
    ](#finnish)
  - [Francês](#french)
  - [Alemão](#german)
  - [     Grego
    ](#greek)
  - [     Hebraico
    ](#hebrew)
  - [     Hindi
    ](#hindi)
  - [     Húngaro
    ](#hungarian)
  - [Italiano](#italian)
  - [Japonês](#japanese)
  - [Koreano](#korean)
  - [Norueguês Bokmål](#norwegian-bokmal)
  - [     Polonês
    ](#polish)
  - [Português](#portuguese)
  - [     Russo
    ](#russian)
  - [Espanhol](#spanish)
  - [     Sueco
    ](#swedish)
  - [     Turco
    ](#turkish)

## Árabe
{: #arabic}

Os modelos a seguir podem traduzir texto em árabe.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
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
     Inglês (<code>en</code>)
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

## Catalão
{: #catalan}

Os modelos a seguir podem traduzir texto em catalão.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>ca-es</code>
    </td>
    <td>
     Catalão (<code>ca</code>)
    </td>
    <td>
     Espanhol (<code>es</code>)
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

## Chinês (Simplificado)
{: #chinese-simplified}

Os modelos a seguir podem traduzir texto em chinês (simplificado).

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     Chinês simplificado (<code>zh</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

## Chinês (Tradicional)
{: #chinese-traditional}

Os modelos a seguir podem traduzir texto em chinês (tradicional).

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     Chinês tradicional (<code>zh-TW</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

## Tcheco
{: #czech}

Os modelos a seguir podem traduzir texto em tcheco.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     Tcheco (<code>cs</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

## Dinamarquês
{: #danish}

Os modelos a seguir podem traduzir texto em dinamarquês.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     Dinamarquês (<code>da</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

## Holandês
{: #dutch}

Os modelos a seguir podem traduzir texto em holandês.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     Holandês (<code>nl</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

## Inglês
{: #english}

Os modelos a seguir podem converter texto em inglês.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     Inglês (<code>en</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Tcheco (<code>cs</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Dinamarquês (<code>da</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Alemão (<code>de</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Grego (<code>el</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Espanhol (<code>es</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Finlandês (<code>fi</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Francês (<code>fr</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Hebraico (<code>he</code>)
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
     Inglês (<code>en</code>)
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
     Inglês (<code>en</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Japonês (<code>ja</code>)
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
     Inglês (<code>en</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Bokmål norueguês (<code>nb</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Holandês (<code>nl</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Polonês (<code>pl</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Português (<code>pt</code>)
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
     Inglês (<code>en</code>)
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
     Inglês (<code>en</code>)
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
     Inglês (<code>en</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Chinês simplificado (<code>zh</code>)
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
     Inglês (<code>en</code>)
    </td>
    <td>
     Chinês tradicional (<code>zh-TW</code>)
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

## Finlandês
{: #finnish}

Os modelos a seguir podem traduzir texto em finlandês.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     Finlandês (<code>fi</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

## Francês
{: #french}

Os modelos a seguir podem converter texto em francês.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     Francês (<code>fr</code>)
    </td>
    <td>
     Alemão (<code>de</code>)
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
     Francês (<code>fr</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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
     Francês (<code>fr</code>)
    </td>
    <td>
     Espanhol (<code>es</code>)
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

## Alemão
{: #german}

Os modelos a seguir podem traduzir texto em alemão.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     Alemão (<code>de</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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
     Alemão (<code>de</code>)
    </td>
    <td>
     Francês (<code>fr</code>)
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
     Alemão (<code>de</code>)
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

## Grego
{: #greek}

Os modelos a seguir podem traduzir texto em grego.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>el-en</code>
    </td>
    <td>
     Grego (<code>el</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

## Hebraico
{: #hebrew}

Os modelos a seguir podem traduzir texto em hebraico.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>he-en</code>
    </td>
    <td>
     Hebraico (<code>he</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

Os modelos a seguir podem traduzir texto em hindi.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
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
     Inglês (<code>en</code>)
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

Os modelos a seguir podem traduzir texto em húngaro.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
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
     Inglês (<code>en</code>)
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

Os modelos a seguir podem converter texto em italiano.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
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
     Alemão (<code>de</code>)
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
     Inglês (<code>en</code>)
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

## Japonês
{: #japanese}

Os modelos a seguir podem converter texto em japonês.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     Japonês (<code>ja</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

Os modelos a seguir podem converter texto em coreano.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
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
     Inglês (<code>en</code>)
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

## Norueguês Bokmål
{: #norwegian-bokmal}

Os modelos a seguir podem traduzir o texto em bokmål norueguês.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     Bokmål norueguês (<code>nb</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

## Polonês
{: #polish}

Os modelos a seguir podem traduzir texto em polonês.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     Polonês (<code>pl</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

## Português
{: #portuguese}

Os modelos a seguir podem converter texto em português.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     Português (<code>pt</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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

Os modelos a seguir podem traduzir texto em russo.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
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
     Inglês (<code>en</code>)
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

## Espanhol
{: #spanish}

Os modelos a seguir podem converter texto em espanhol.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     Espanhol (<code>es</code>)
    </td>
    <td>
     Catalão (<code>ca</code>)
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
     Espanhol (<code>es</code>)
    </td>
    <td>
     Inglês (<code>en</code>)
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
     Espanhol (<code>es</code>)
    </td>
    <td>
     Francês (<code>fr</code>)
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

Os modelos a seguir podem traduzir texto em sueco.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
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
     Inglês (<code>en</code>)
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

Os modelos a seguir podem traduzir texto em turco.

<table>
 <thead>
  <th>
   ID do Modelo
  </th>
  <th>
   Origem
  </th>
  <th>
   Destino
  </th>
  <th>
   Domínio
  </th>
  <th>
   Customizável
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
     Inglês (<code>en</code>)
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

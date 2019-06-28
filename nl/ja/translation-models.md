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

# 翻訳モデル
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}} は、以下の言語を翻訳できます。
下記のリストの言語をクリックすると、対応する翻訳モデルのリストが表示されます。

また、**「モデルのリスト (List models)」**API メソッドを使用すると、カスタム・モデルを含む使用可能な翻訳モデルを表示できます。`source` および `target` パラメーターを使用して、言語を基準に結果をフィルター操作できます。以下の例は、英語をスペイン語に翻訳できるモデルをリストします。

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [アラビア語](#arabic)
  - [カタロニア語](#catalan)
  - [中国語 (簡体字)](#chinese-simplified)
  - [中国語 (繁体字)](#chinese-traditional)
  - [チェコ語](#czech)
  - [デンマーク語](#danish)
  - [オランダ語](#dutch)
  - [英語](#english)
  - [フィンランド語](#finnish)
  - [フランス語](#french)
  - [ドイツ語](#german)
  - [ギリシャ語](#greek)
  - [ヘブライ語](#hebrew)
  - [ヒンディ語](#hindi)
  - [ハンガリー語](#hungarian)
  - [イタリア語](#italian)
  - [日本語](#japanese)
  - [韓国語](#korean)
  - [ノルウェー語ブークモール](#norwegian-bokmal)
  - [ポーランド語](#polish)
  - [ポルトガル語](#portuguese)
  - [ロシア語](#russian)
  - [スペイン語](#spanish)
  - [スウェーデン語](#swedish)
  - [トルコ語](#turkish)

## アラビア語
{: #arabic}

以下のモデルはアラビア語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>ar-en</code>
    </td>
    <td>
     アラビア語 (<code>ar</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## カタロニア語
{: #catalan}

以下のモデルは、カタロニア語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>ca-es</code>
    </td>
    <td>
     カタロニア語 (<code>ca</code>)
    </td>
    <td>
     スペイン語 (<code>es</code>)
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

## 中国語 (簡体字)
{: #chinese-simplified}

以下のモデルは中国語 (簡体字) テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     中国語 (簡体字) (<code>zh</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## 中国語 (繁体字)
{: #chinese-traditional}

以下のモデルは中国語 (繁体字) テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     中国語 (繁体字) (<code>zh-TW</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## チェコ語
{: #czech}

以下のモデルは、チェコ語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     チェコ語 (<code>cs</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## デンマーク語
{: #danish}

以下のモデルは、デンマーク語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     デンマーク語 (<code>da</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## オランダ語
{: #dutch}

以下のモデルは、オランダ語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     オランダ語 (<code>nl</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## 英語
{: #english}

以下のモデルは英語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     英語 (<code>en</code>)
    </td>
    <td>
     アラビア語 (<code>ar</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     チェコ語 (<code>cs</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     デンマーク語 (<code>da</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     ドイツ語 (<code>de</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     ギリシャ語 (<code>el</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     スペイン語 (<code>es</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     フィンランド語 (<code>fi</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     フランス語 (<code>fr</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     ヘブライ語 (<code>he</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     ヒンディ語 (<code>hi</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     イタリア語 (<code>it</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     日本語 (<code>ja</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     韓国語 (<code>ko</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     ノルウェー語ブークモール (<code>nb</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     オランダ語 (<code>nl</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     ポーランド語 (<code>pl</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     ポルトガル語 (<code>pt</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     ロシア語 (<code>ru</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     スウェーデン語 (<code>sv</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     トルコ語 (<code>tr</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     中国語 (簡体字) (<code>zh</code>)
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
     英語 (<code>en</code>)
    </td>
    <td>
     中国語 (繁体字) (<code>zh-TW</code>)
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

## フィンランド語
{: #finnish}

以下のモデルは、フィンランド語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     フィンランド語 (<code>fi</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## フランス語
{: #french}

以下のモデルはフランス語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     フランス語 (<code>fr</code>)
    </td>
    <td>
     ドイツ語 (<code>de</code>)
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
     フランス語 (<code>fr</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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
     フランス語 (<code>fr</code>)
    </td>
    <td>
     スペイン語 (<code>es</code>)
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

## ドイツ語
{: #german}

以下のモデルはドイツ語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     ドイツ語 (<code>de</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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
     ドイツ語 (<code>de</code>)
    </td>
    <td>
     フランス語 (<code>fr</code>)
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
     ドイツ語 (<code>de</code>)
    </td>
    <td>
     イタリア語 (<code>it</code>)
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

## ギリシャ語
{: #greek}

以下のモデルは、ギリシャ語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>el-en</code>
    </td>
    <td>
     ギリシャ語 (<code>el</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## ヘブライ語
{: #hebrew}

以下のモデルは、ヘブライ語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>he-en</code>
    </td>
    <td>
     ヘブライ語 (<code>he</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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


## ヒンディ語
{: #hindi}

以下のモデルは、ヒンディ語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>hi-en</code>
    </td>
    <td>
     ヒンディ語 (<code>hi</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## ハンガリー語
{: #hungarian}

以下のモデルは、ハンガリー語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>hu-en</code>
    </td>
    <td>
     ハンガリー語 (<code>hu</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## イタリア語
{: #italian}

以下のモデルはイタリア語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>it-de</code>
    </td>
    <td>
     イタリア語 (<code>it</code>)
    </td>
    <td>
     ドイツ語 (<code>de</code>)
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
     イタリア語 (<code>it</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## 日本語
{: #japanese}

以下のモデルは日本語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     日本語 (<code>ja</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## 韓国語
{: #korean}

以下のモデルは韓国語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>ko-en</code>
    </td>
    <td>
     韓国語 (<code>ko</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## ノルウェー語ブークモール
{: #norwegian-bokmal}

以下のモデルは、ノルウェー語ブークモール・テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     ノルウェー語ブークモール (<code>nb</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## ポーランド語
{: #polish}

以下のモデルは、ポーランド語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     ポーランド語 (<code>pl</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## ポルトガル語
{: #portuguese}

以下のモデルはポルトガル語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     ポルトガル語 (<code>pt</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## ロシア語
{: #russian}

以下のモデルは、ロシア語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>ru-en</code>
    </td>
    <td>
     ロシア語 (<code>ru</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## スペイン語
{: #spanish}

以下のモデルはスペイン語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     スペイン語 (<code>es</code>)
    </td>
    <td>
     カタロニア語 (<code>ca</code>)
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
     スペイン語 (<code>es</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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
     スペイン語 (<code>es</code>)
    </td>
    <td>
     フランス語 (<code>fr</code>)
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

## スウェーデン語
{: #swedish}

以下のモデルは、スウェーデン語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>sv-en</code>
    </td>
    <td>
     スウェーデン語 (<code>sv</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

## トルコ語
{: #turkish}

以下のモデルは、トルコ語テキストを翻訳できます。

<table>
 <thead>
  <th>
   モデル ID
  </th>
  <th>
   ソース
  </th>
  <th>
   ターゲット
  </th>
  <th>
   ドメイン
  </th>
  <th>
   カスタマイズ可能
  </th>
  <tbody>
   <tr>
    <td>
     <code>tr-en</code>
    </td>
    <td>
     トルコ語 (<code>tr</code>)
    </td>
    <td>
     英語 (<code>en</code>)
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

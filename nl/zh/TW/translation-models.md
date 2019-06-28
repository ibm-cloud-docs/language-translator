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

# 翻譯模型
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}} 可以翻譯下列語言。
按一下底下清單中的語言，即可檢視相容翻譯模型的清單。

您也可以使用**列出模型** API 方法來檢視可用的翻譯模型，包括您的自訂模型。您可以使用 `source` 和 `target` 參數，依語言過濾結果。下列範例列出可將英文翻譯為西班牙文的模型。

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [阿拉伯文](#arabic)
  - [加泰蘭文](#catalan)
  - [簡體中文](#chinese-simplified)
  - [繁體中文](#chinese-traditional)
  - [     捷克文
    ](#czech)
  - [     丹麥文
    ](#danish)
  - [     荷蘭文
    ](#dutch)
  - [英文](#english)
  - [     芬蘭文
    ](#finnish)
  - [法文](#french)
  - [德文](#german)
  - [     希臘文
    ](#greek)
  - [     希伯來文
    ](#hebrew)
  - [     北印度文
    ](#hindi)
  - [     匈牙利文
    ](#hungarian)
  - [義大利文](#italian)
  - [日文](#japanese)
  - [韓文](#korean)
  - [巴克摩挪威文](#norwegian-bokmal)
  - [     波蘭文
    ](#polish)
  - [葡萄牙文](#portuguese)
  - [     俄文
    ](#russian)
  - [西班牙文](#spanish)
  - [     瑞典文
    ](#swedish)
  - [     土耳其文
    ](#turkish)

## 阿拉伯文
{: #arabic}

下列模型可以翻譯阿拉伯文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>ar-en</code>
    </td>
    <td>
     阿拉伯文 (<code>ar</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 加泰蘭文
{: #catalan}

下列模型可以翻譯加泰蘭文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>ca-es</code>
    </td>
    <td>
     加泰蘭文 (<code>ca</code>)
    </td>
    <td>
     西班牙文 (<code>es</code>)
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

## 簡體中文
{: #chinese-simplified}

下列模型可以翻譯簡體中文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     簡體中文 (<code>zh</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 繁體中文
{: #chinese-traditional}

下列模型可以翻譯繁體中文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     繁體中文 (<code>zh-TW</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

##      捷克文
    
{: #czech}

下列模型可以翻譯捷克文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     捷克文 (<code>cs</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

##      丹麥文
    
{: #danish}

下列模型可以翻譯丹麥文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     丹麥文 (<code>da</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

##      荷蘭文
    
{: #dutch}

下列模型可以翻譯荷蘭文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     荷蘭文 (<code>nl</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 英文
{: #english}

下列模型可以翻譯英文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     英文 (<code>en</code>)
    </td>
    <td>
     阿拉伯文 (<code>ar</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     捷克文 (<code>cs</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     丹麥文 (<code>da</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     德文 (<code>de</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     希臘文 (<code>el</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     西班牙文 (<code>es</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     芬蘭文 (<code>fi</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     法文 (<code>fr</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     希伯來文 (<code>he</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     北印度文 (<code>hi</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     義大利文 (<code>it</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     日文 (<code>ja</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     韓文 (<code>ko</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     巴克摩挪威文 (<code>nb</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     荷蘭文 (<code>nl</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     波蘭文 (<code>pl</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     葡萄牙文 (<code>pt</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     俄文 (<code>ru</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     瑞典文 (<code>sv</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     土耳其文 (<code>tr</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     簡體中文 (<code>zh</code>)
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
     英文 (<code>en</code>)
    </td>
    <td>
     繁體中文 (<code>zh-TW</code>)
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

##      芬蘭文
    
{: #finnish}

下列模型可以翻譯芬蘭文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     芬蘭文 (<code>fi</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 法文
{: #french}

下列模型可以翻譯法文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     法文 (<code>fr</code>)
    </td>
    <td>
     德文 (<code>de</code>)
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
     法文 (<code>fr</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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
     法文 (<code>fr</code>)
    </td>
    <td>
     西班牙文 (<code>es</code>)
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

## 德文
{: #german}

下列模型可以翻譯德文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     德文 (<code>de</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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
     德文 (<code>de</code>)
    </td>
    <td>
     法文 (<code>fr</code>)
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
     德文 (<code>de</code>)
    </td>
    <td>
     義大利文 (<code>it</code>)
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

##      希臘文
    
{: #greek}

下列模型可以翻譯希臘文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>el-en</code>
    </td>
    <td>
     希臘文 (<code>el</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

##      希伯來文
    
{: #hebrew}

下列模型可以翻譯希伯來文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>he-en</code>
    </td>
    <td>
     希伯來文 (<code>he</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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


##      北印度文
    
{: #hindi}

下列模型可以翻譯北印度文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>hi-en</code>
    </td>
    <td>
     北印度文 (<code>hi</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

##      匈牙利文
    
{: #hungarian}

下列模型可以翻譯匈牙利文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>hu-en</code>
    </td>
    <td>
     匈牙利文 (<code>hu</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 義大利文
{: #italian}

下列模型可以翻譯義大利文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>it-de</code>
    </td>
    <td>
     義大利文 (<code>it</code>)
    </td>
    <td>
     德文 (<code>de</code>)
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
     義大利文 (<code>it</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 日文
{: #japanese}

下列模型可以翻譯日文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     日文 (<code>ja</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 韓文
{: #korean}

下列模型可以翻譯韓文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>ko-en</code>
    </td>
    <td>
     韓文 (<code>ko</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 巴克摩挪威文
{: #norwegian-bokmal}

下列模型可以翻譯巴克摩挪威文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     巴克摩挪威文 (<code>nb</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

##      波蘭文
    
{: #polish}

下列模型可以翻譯波蘭文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     波蘭文 (<code>pl</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 葡萄牙文
{: #portuguese}

下列模型可以翻譯葡萄牙文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     葡萄牙文 (<code>pt</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

##      俄文
    
{: #russian}

下列模型可以翻譯俄文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>ru-en</code>
    </td>
    <td>
     俄文 (<code>ru</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

## 西班牙文
{: #spanish}

下列模型可以翻譯西班牙文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     西班牙文 (<code>es</code>)
    </td>
    <td>
     加泰蘭文 (<code>ca</code>)
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
     西班牙文 (<code>es</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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
     西班牙文 (<code>es</code>)
    </td>
    <td>
     法文 (<code>fr</code>)
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

##      瑞典文
    
{: #swedish}

下列模型可以翻譯瑞典文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>sv-en</code>
    </td>
    <td>
     瑞典文 (<code>sv</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

##      土耳其文
    
{: #turkish}

下列模型可以翻譯土耳其文文字。

<table>
 <thead>
  <th>
   模型 ID
  </th>
  <th>
   來源
  </th>
  <th>
   目標
  </th>
  <th>
   領域
  </th>
  <th>
   可自訂
  </th>
  <tbody>
   <tr>
    <td>
     <code>tr-en</code>
    </td>
    <td>
     土耳其文 (<code>tr</code>)
    </td>
    <td>
     英文 (<code>en</code>)
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

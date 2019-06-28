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

# 翻译模型
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}} 可以翻译以下语言。单击以下列表中的语言来查看兼容翻译模型的列表。

您还可以使用**列出模型** API 方法来查看可用的翻译模型，包括定制模型。可以使用 `source` 和 `target` 参数按语言对结果进行过滤。以下示例列出了可以将英语翻译成西班牙语的模型。

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [阿位伯语](#arabic)
  - [加泰罗尼亚语](#catalan)
  - [简体中文](#chinese-simplified)
  - [繁体中文](#chinese-traditional)
  - [     捷克语
    ](#czech)
  - [     丹麦语
    ](#danish)
  - [     荷兰语
    ](#dutch)
  - [英语](#english)
  - [     芬兰语
    ](#finnish)
  - [法语](#french)
  - [德语](#german)
  - [     希腊语
    ](#greek)
  - [     希伯来语
    ](#hebrew)
  - [     印地语
    ](#hindi)
  - [     匈牙利语
    ](#hungarian)
  - [意大利语](#italian)
  - [日语](#japanese)
  - [韩语](#korean)
  - [挪威博克马尔语](#norwegian-bokmal)
  - [     波兰语
    ](#polish)
  - [葡萄牙语](#portuguese)
  - [     俄语
    ](#russian)
  - [西班牙语](#spanish)
  - [     瑞典语
    ](#swedish)
  - [     土耳其语
    ](#turkish)

## 阿位伯语
{: #arabic}

以下模型可以翻译阿拉伯语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>ar-en</code>
    </td>
    <td>
     阿拉伯语 (<code>ar</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 加泰罗尼亚语
{: #catalan}

以下模型可以翻译加泰罗尼亚语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>ca-es</code>
    </td>
    <td>
     加泰罗尼亚语 (<code>ca</code>)
    </td>
    <td>
     西班牙语 (<code>es</code>)
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

## 简体中文
{: #chinese-simplified}

以下模型可以翻译简体中文文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     简体中文 (<code>zh</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 繁体中文
{: #chinese-traditional}

以下模型可以翻译繁体中文文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     繁体中文 (<code>zh-TW</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

##      捷克语
    
{: #czech}

以下模型可以翻译捷克语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     捷克语 (<code>cs</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

##      丹麦语
    
{: #danish}

以下模型可以翻译丹麦语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     丹麦语 (<code>da</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

##      荷兰语
    
{: #dutch}

以下模型可以翻译荷兰语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     荷兰语 (<code>nl</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 英语
{: #english}

以下模型可以翻译英语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     英语 (<code>en</code>)
    </td>
    <td>
     阿拉伯语 (<code>ar</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     捷克语 (<code>cs</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     丹麦语 (<code>da</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     德语 (<code>de</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     希腊语 (<code>el</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     西班牙语 (<code>es</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     芬兰语 (<code>fi</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     法语 (<code>fr</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     希伯来语 (<code>he</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     印地语 (<code>hi</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     意大利语 (<code>it</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     日语 (<code>ja</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     韩语 (<code>ko</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     挪威博克马尔语 (<code>nb</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     荷兰语 (<code>nl</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     波兰语 (<code>pl</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     葡萄牙语 (<code>pt</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     俄语 (<code>ru</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     瑞典语 (<code>sv</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     土耳其语 (<code>tr</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     简体中文 (<code>zh</code>)
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
     英语 (<code>en</code>)
    </td>
    <td>
     繁体中文 (<code>zh-TW</code>)
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

##      芬兰语
    
{: #finnish}

以下模型可以翻译芬兰语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     芬兰语 (<code>fi</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 法语
{: #french}

以下模型可以翻译法语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     法语 (<code>fr</code>)
    </td>
    <td>
     德语 (<code>de</code>)
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
     法语 (<code>fr</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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
     法语 (<code>fr</code>)
    </td>
    <td>
     西班牙语 (<code>es</code>)
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

## 德语
{: #german}

以下模型可以翻译德语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     德语 (<code>de</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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
     德语 (<code>de</code>)
    </td>
    <td>
     法语 (<code>fr</code>)
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
     德语 (<code>de</code>)
    </td>
    <td>
     意大利语 (<code>it</code>)
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

##      希腊语
    
{: #greek}

以下模型可以翻译希腊语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>el-en</code>
    </td>
    <td>
     希腊语 (<code>el</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

##      希伯来语
    
{: #hebrew}

以下模型可以翻译希伯来语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>he-en</code>
    </td>
    <td>
     希伯来语 (<code>he</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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


##      印地语
    
{: #hindi}

以下模型可以翻译印地语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>hi-en</code>
    </td>
    <td>
     印地语 (<code>hi</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

##      匈牙利语
    
{: #hungarian}

以下模型可以翻译匈牙利语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>hu-en</code>
    </td>
    <td>
     匈牙利语 (<code>hu</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 意大利语
{: #italian}

以下模型可以翻译意大利语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>it-de</code>
    </td>
    <td>
     意大利语 (<code>it</code>)
    </td>
    <td>
     德语 (<code>de</code>)
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
     意大利语 (<code>it</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 日语
{: #japanese}

以下模型可以翻译日语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     日语 (<code>ja</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 韩语
{: #korean}

以下模型可以翻译韩语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>ko-en</code>
    </td>
    <td>
     韩语 (<code>ko</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 挪威博克马尔语
{: #norwegian-bokmal}

以下模型可以翻译挪威博克马尔语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     挪威博克马尔语 (<code>nb</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

##      波兰语
    
{: #polish}

以下模型可以翻译波兰语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     波兰语 (<code>pl</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 葡萄牙语
{: #portuguese}

以下模型可以翻译葡萄牙语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     葡萄牙语 (<code>pt</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

##      俄语
    
{: #russian}

以下模型可以翻译俄语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>ru-en</code>
    </td>
    <td>
     俄语 (<code>ru</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

## 西班牙语
{: #spanish}

以下模型可以翻译西班牙语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     西班牙语 (<code>es</code>)
    </td>
    <td>
     加泰罗尼亚语 (<code>ca</code>)
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
     西班牙语 (<code>es</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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
     西班牙语 (<code>es</code>)
    </td>
    <td>
     法语 (<code>fr</code>)
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

##      瑞典语
    
{: #swedish}

以下模型可以翻译瑞典语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>sv-en</code>
    </td>
    <td>
     瑞典语 (<code>sv</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

##      土耳其语
    
{: #turkish}

以下模型可以翻译土耳其语文本。

<table>
 <thead>
  <th>
   模型标识
  </th>
  <th>
   源
  </th>
  <th>
   目标
  </th>
  <th>
   域
  </th>
  <th>
   可定制
  </th>
  <tbody>
   <tr>
    <td>
     <code>tr-en</code>
    </td>
    <td>
     土耳其语 (<code>tr</code>)
    </td>
    <td>
     英语 (<code>en</code>)
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

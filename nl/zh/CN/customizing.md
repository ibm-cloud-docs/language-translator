---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# 定制模型
{: #customizing}

可以对 {{site.data.keyword.languagetranslatorshort}} 中提供的大部分翻译模型进行扩展，以学习从翻译数据派生的定制词汇和短语或通用样式。请遵循以下指示信息来创建您自己的定制翻译模型。
{: shortdesc}

## 开始之前
{: #before-you-begin}

1. 确保 {{site.data.keyword.languagetranslatorshort}} 服务实例位于高级或高端价格套餐上。轻量套餐和标准套餐不支持定制。
1. 查找用于语言对的可定制基本模型。您需要基本模型的模型标识才能训练定制模型。
    - 搜索[翻译模型](/docs/services/language-translator?topic=language-translator-translation-models)页面上列出的模型。在**可定制**列中查找值“**true**”，并确保模型的**源**语言和**目标**语言与语言对相匹配。
    - 或者，可以使用[列出模型 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/apidocs/language-translator#list-models) API 方法以编程方式搜索模型。可以使用 `source` 和 `target` 参数按语言对结果进行过滤。

## 步骤 1：创建训练数据
{: #create-your-training-data}

服务需要以[翻译记忆交换 (TMX) 文件格式](#creating-tmx-files)提供训练数据。对于服务实例中的每个语言对，最多可以存储 10 个定制项。服务支持两种类型的定制请求。可以使用特殊词汇表或包含平行语句的语料库来定制模型。

- 使用[特殊词汇表](#forced-glossary-customization)可强制以特定方式翻译某些词汇和短语。
- 希望定制模型通过样本中的一般翻译模式学习时，请使用[平行语料库](#parallel-corpus-customization)。利用模型通过平行语料库学习的收获，可以改进模型未对其进行训练的输入文本的翻译结果。

创建[翻译记忆交换 (TMX) 文件](#creating-tmx-files)后，即可以随时训练模型。

## 步骤 2：训练模型
{: #train-your-model}

使用[创建模型 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/apidocs/language-translator#create-model) 方法来训练模型。在请求中，指定可定制基本模型的模型标识，并使用 `forced_glossary` 或 `parallel_corpus` 参数指定训练数据。

### 示例请求
{: #train-model-example-request}

以下示例请求使用特殊词汇表文件 _glossary.tmx_ 来定制 `en-es` 基本模型。有关示例特殊词汇表 TMX 文件，请参阅[特殊词汇表定制](#forced-glossary)部分。

```bash
curl --user apikey:{apikey} -X POST --form forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

API 响应将包含有关定制模型的详细信息，包括其模型标识。使用模型标识来检查模型的状态，并在模型的状态变为“available”后翻译语句。

```json
{
  "model_id": "96221b69-8e46-42e4-a3c1-808e17c787ca",
  "source": "en",
  "target": "es",
  "base_model_id": "en-es",
  "domain": "general",
  "customizable": false,
  "default_model": false,
  "owner": "4937aab7-0f3a-4a75-bee1-0b7a12b6b8",
  "status": "uploaded",
  "name": "custom-english-to-spanish",
  "train_log": null
}
```
{: codeblock}

## 步骤 3：检查模型的状态
{: #check-model-status}

模型训练可能需要几分钟（对于特殊词汇表）到几个小时（对于大型平行语料库），具体取决于涉及的训练数据量。要查看模型是否可用，请使用[获取模型 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/apidocs/language-translator#get-model-details) 方法，并指定在步骤 2 的服务响应中收到的模型标识。此外，还可以使用[列出模型 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/apidocs/language-translator#list-models) 方法来检查所有模型的状态。

`status` 响应属性描述训练过程中模型的状态：

- `uploading`
- `uploaded`
- `dispatching`
- `queued`
- `training`
- `trained`
- `publishing`
- `available`

模型状态为 `available` 时，说明模型已准备就绪，可以用于服务实例。如果模型已删除，或者如果模型在训练过程中遇到错误，那么可能会看到下列其中一个状态：

- `deleted`
- `error`

### 示例请求
{: #check-model-example-request}

以下示例获取模型标识 `96221b69-8e46-42e4-a3c1-808e17c787ca` 所标识的模型的信息。

```bash
curl --user apikey:{apikey_value} "https://gateway.watsonplatform.net/language-translator/api/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## 步骤 4：使用定制模型翻译文本
{: #translate-text}

要使用定制模型，请在[翻译 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/apidocs/language-translator#translate) 方法中指定要翻译的文本和定制模型的模型标识。

### 示例请求
{: #translate-text-example-request}

以下示例使用模型标识 `96221b69-8e46-42e4-a3c1-808e17c787ca` 所标识的定制模型来翻译文本。

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data '{"text":"Hello","model_id":"96221b69-8e46-42e4-a3c1-808e17c787ca"}' https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}


## 特殊词汇表定制
{: #forced-glossary-customization}

使用**特殊词汇表**可设置强制用于特定词汇和短语的翻译。如果希望对翻译行为进行特定控制，请使用特殊词汇表。

- 训练数据格式：[TMX](#creating-tmx-files)（UTF-8 编码）
- 最大文件大小：10 MB
- 可以将特殊词汇表应用于基本模型，或应用于已使用平行语料库定制的模型
- 每个模型只能有一个特殊词汇表

特殊词汇表示例区分大小写，因此请确保训练数据可反映出应用程序将遇到的内容的大小写。
{: tip}

### 特殊词汇表示例
{: #forced-glossary-example}

以下示例显示具有两个翻译对的 TMX 文件。第一对强制使“international business machines”在翻译期间保留为英语。如果要保留非正式交流中大小写不正确的公司名称，那么这种类型的强制翻译可能会很有用。第二对强制模型在翻译“patent”时始终使用“brevet”。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="phrase" o-tmf="" adminlang="en"
    srclang="en" datatype="PlainText" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>International Business Machines</seg>
      </tuv>
    </tu>
    <tu>
      <tuv xml:lang="en">
        <seg>patent</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>brevet</seg>
      </tuv>
    </tu>
  </body>
</tmx>
```
{: codeblock}



## 平行语料库定制
{: #parallel-corpus-customization}

使用**平行语料库**可提供其他翻译，供基本模型从中学习。这有助于将基本模型调整为针对特定领域。生成的定制模型如何翻译文本取决于模型对平行语料库和基本模型的综合理解。

- 训练数据格式：[TMX](#creating-tmx-files)（UTF-8 编码）
- 翻译对的最大长度：80 个字（源语言）
- 最小翻译对数：5,000
- 最大文件大小：250 MB
- 通过重复 `parallel_corpus` 多部分表单参数，可提交多个平行语料库文件，只要这些文件的累计大小不超过 250 MB 即可。

### 平行语料库示例
{: #parallel-corpus-example}

下面是从 OPUS 开放式平行语料库 Web 站点上提供的 [MultiUN 集合 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://opus.nlpl.eu/MultiUN.php) 中下载的英语到法语平行语料库中的一小部分。您可以在[此处 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz) 下载整个 TMX 文件的压缩版本。


```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
<header creationdate="Tue Jan 29 12:49:40 2013"
          srclang="en"
          adminlang="en"
          o-tmf="unknown"
          segtype="sentence"
          creationtool="Uplug"
          creationtoolversion="unknown"
          datatype="PlainText" />
  <body>
    <tu>
      <tuv xml:lang="en"><seg>RESOLUTION 55/100</seg></tuv>
      <tuv xml:lang="fr"><seg>RÉSOLUTION 55/100</seg></tuv>
    </tu>
    <tu>
      <tuv xml:lang="en"><seg>Adopted at the 81st plenary meeting, on 4 December 2000, on the recommendation of the Committee (A/55/602/Add.2 and Corr.1, para. 94),The draft resolution recommended in the report was sponsored in the Committee by: Bolivia, Cuba, El Salvador, Ghana and Honduras. by a recorded vote of 106 to 1, with 67 abstentions, as follows:</seg></tuv>
      <tuv xml:lang="fr"><seg>Adoptée à la 81e séance plénière, le 4 décembre 2000, sur la recommandation de la Commission (A/55/602/Add.2, par. 94)Le projet de résolution recommandé dans le rapport de la Commission avait pour auteurs les pays suivants: Bolivie, Cuba, El Salvador, Ghana et Honduras., par 106 voix contre une, avec 67 abstentions, à la suite d'un vote enregistré, les voix s'étant réparties comme suit:</seg></tuv>
    </tu>
    ...
```
{: codeblock}

通过平行语料库定制进行的一般改进的可预测性不如通过特殊词汇表定制所获得的强制翻译结果。例如，假设示例平行语料库（第 172-175 行）中有以下翻译单元。

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

如果使用基本 `en-fr` 模型来翻译“55/102. Globalization and its impact on the full enjoyment of all human rights”，那么服务会使用以下翻译进行响应。

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

通过使用示例语料库进行训练的定制模型来翻译同一输入语句时，服务响应的翻译与训练数据中提供的样本翻译不同。

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- 定制模型将“the full enjoyment”翻译成“le plein exercice”，而不是“la pleine jouissance”。对于这种与基本模型行为相偏离的情况，可能的解释是在语料库中有许多示例的“enjoyment”翻译成“exercice”。
- 定制模型将“of all human rights”翻译成“de tous les droits de l'homme”，而未采用翻译单元中的结果“des droits de l'homme”。此行为反映了经过训练的模型对基本模型以及对平行语料库中与“of all human rights”相关的所有翻译样本的综合性理解。

在某些情况下，似乎使用平行语料库训练的定制模型会忽略您提供的特定示例。对于这些情况，请尝试在训练数据中搜索可能会影响翻译行为的其他语句，或者如果要控制特定翻译，请考虑使用特殊词汇表。


## 创建 TMX 文件
{: #creating-tmx-files}

要提供用于训练 {{site.data.keyword.languagetranslatorshort}} 服务的术语的词汇表或语料库，请创建符合翻译记忆交换 (TMX) [V1.4 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ttt.org/oscarStandards/tmx/){: new_window} 规范的有效 UTF-8 编码文档。TMX 是针对机器翻译工具设计的 XML 规范。以下示例是 TMX 格式的词汇表文件，其中包含两个翻译单元（`<tu>` 元素）：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>International Business Machines</seg>
      </tuv>
    </tu>
    <tu>
      <tuv xml:lang="en">
        <seg>patent</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>brevet</seg>
      </tuv>
    </tu>
  </body>
</tmx>
```
{: codeblock}

每个词汇和翻译对都必须包含在 `<tu>` 标记中：

```xml
<tu>
  <tuv xml:lang="en">
    <seg>international business machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

`<tuv>` 标记中的`xml:lang` 属性标识用于表示词汇的语言，`<seg>` 标记包含词汇或翻译。

{{site.data.keyword.languagetranslatorshort}} 服务仅使用 `<tu>`、`<tuv>` 和 `<seg>` 元素。示例中的其他所有元素要么是生成有效 TMX 文件所必需的元素，要么是参考信息元素，但不由该服务使用。



### 将示例用作模板
{: #using-the-example-template}

要将提供的示例用作自己的词汇表或语料库的模板，请完成以下步骤：

1. 将示例复制并粘贴到文本编辑器中。

2. 将 `<header>` 标记的 `srclang` 属性更改为词汇表或平行语料库所用源语言的[语言代码 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}。

3. 将 `<tuv>` 标记的 `xml:lang` 属性更改为每个词汇或翻译的正确[语言代码 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}。

4. 使用扩展名 `.tmx` 和 UTF-8 编码保存文档。

### 将 TMX 文件更改为 UTF-8 编码
{: #changing-tmx-file-to-utf-8}

可以使用多种工具来创建或生成 TMX 文件。通常，生成的 TMX 文件缺省情况下采用 UTF-16 编码。{{site.data.keyword.languagetranslatorshort}} 服务仅接受 UTF-8 编码的 TMX 文件。要更改 TMX 文件的编码，请完成以下步骤：

1. 在文本编辑器中打开 TMX 文件。

1. 将 XML 头（如果存在）从 `<?xml ... encoding="utf-16"?>` 更改为 `<?xml ... encoding="utf-8"?>`。

1. 使用新名称和 UTF-8 编码输出保存文件。

此外，Mac 用户可以通过更新文档的 XML 头（如步骤 2 中所述），然后在“终端”中运行以下命令来更改文件编码：

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}


## 删除定制翻译模型
{: #deleting-a-custom-model}

要删除定制翻译模型，请使用[删除模型 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/apidocs/language-translator#delete-model) 方法。

以下命令将删除模型标识为 `3e7dfdbe-f757-4150-afee-458e71eb93fb` 的翻译模型。

```curl
curl --user apikey:{apikey_value} --request DELETE "https://gateway.watsonplatform.net/language-translator/api/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: codeblock}

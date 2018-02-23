---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

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

您是否打算创建翻译程序以供客户支持使用，并且有特定于公司的术语需要在对话中以某种方式进行处理？是否打算为一个国家或地区的工程师创建一种方法来查找采用其他语言的专利数据，并且您通常针对特定技术申报专利？请使用您自己的数据在 {{site.data.keyword.languagetranslatorshort}} API 中创建定制字典和定制翻译模型。
{: shortdesc}

您可以通过以下方式定制 {{site.data.keyword.languagetranslatorshort}} 模型：

- 使用源语言和目标语言中的匹配术语或短语对来培训服务。提供*必备词汇表*，其中包含的术语或短语对是您希望翻译服务视为必需的绝对而明确的术语。或者，提供*平行语料库*，其中包含的术语或短语对用作您希望翻译服务考虑的备用翻译建议。
- 上传目标语言的大量文本（称为*单语言语料库*）以用作语言样本，供服务评估和使用以提高总体翻译质量。

要查看可以定制的模型的列表，请使用 `GET /v2/models` 方法，并在每种语言模型的响应中查找响应参数 `customizable=true`。

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

每个可定制模型最多可以为每个服务实例存储 10 个定制项。

## 培训数据的结构
{: #structure}

要提供用于培训 {{site.data.keyword.languagetranslatorshort}} 服务的术语的词汇表或语料库，请创建符合翻译记忆交换 (TMX) [V1.4 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www.ttt.org/oscarstandards/tmx/tmx14.dtd){: new_window} 规范的有效 UTF-8 编码文档。TMX 是针对机器翻译工具设计的 XML 规范。以下示例是 TMX 格式的词汇表文件，其中包含两个术语和翻译项对：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>International Business Machines</seg>
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

每对术语和翻译项都必须包含在 `<tu>` 标记内：

```xml
<tu>
  <tuv xml:lang="en">
    <seg>International Business Machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

`<tuv>` 标记中的 `xml:lang` 属性确定用于表达术语的语言，而 `<seg>` 标记包含术语或翻译项。

{{site.data.keyword.languagetranslatorshort}} 服务仅使用 `<tu>`、`<tuv>` 和 `<seg>` 元素。示例中的其他所有元素要么是生成有效 TMX 文件所必需的元素，要么是参考信息元素，但不由该服务使用。

上面的示例说明如何明确地标准化技术术语（如“patent”）的翻译，以及如何定制公司名称（如“International Business Machines”）的翻译。在标准模式下，“International Business Machines”可能会翻译为“Machines Commerciales Internationales”，但实际上不应该对其进行翻译，因为这是公司名称。

## 将示例用作模板

要将提供的示例用作自己的词汇表或语料库的模板，请完成以下步骤：

1.  将示例复制并粘贴到文本编辑器中。

1.  将 `<header>` 标记的 `srclang` 属性更改为词汇表或平行语料库所用源语言的[语言代码 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}。

1.  将 `<tuv>` 标记的 `xml:lang` 属性更改为每个术语或翻译项的正确[语言代码 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}。

    {{site.data.keyword.languagetranslatorshort}} 服务对于除埃及阿拉伯语以外的其他所有语言，均使用 ISO 639-1 语言代码；埃及阿拉伯语使用 ISO 639-3 代码。

1.  使用扩展名 `.tmx` 和 UTF-8 编码保存文档。

### 将 TMX 文件更改为 UTF-8 编码

可以使用多种工具来创建或生成 TMX 文件。通常，生成的 TMX 文件缺省情况下采用 UTF-16 编码。{{site.data.keyword.languagetranslatorshort}} 服务仅接受 UTF-8 编码的 TMX 文件。要更改 TMX 文件的编码，请完成以下步骤：

1.  在文本编辑器中打开 TMX 文件。

1.  将 XML 头（如果存在）从 `<?xml ... encoding="utf-16"?>` 更改为 `<?xml ... encoding="utf-8"?>`。

1.  使用新名称和 UTF-8 编码输出保存文件。

此外，Mac 用户可以通过更新文档的 XML 头（如步骤 2 中所述），然后在“终端”中运行以下命令来更改文件编码：

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}

## 培训定制翻译模型
{: #training}

使用 `POST /v2/models` 方法来上传 TMX 文件并培训翻译模型。至少指定下列其中一个文件选项来培训定制模型：

- `forced_glossary`：UTF-8 编码的 TMX 文件，其中包含系统视为绝对的源语言和目标语言匹配术语对。此文件会完全覆盖原始域数据。

    必备词汇表的文件大小限制为 10 MB。目前，只能为每个翻译模型上传一个必备词汇表文件。
    
- `parallel_corpus`：UTF-8 编码的 TMX 文件，其中包含用作 Watson 示例的源语言和目标语言匹配短语。平行语料库与必备词汇表不同，因为平行语料库不会覆盖原始域数据。

    要成功培训定制模型，平行语料库文档必须至少包含 5,000 个术语和翻译项对。
    
- `monolingual_corpus`：UTF-8 编码的纯文本文件，其中包含与所翻译内容相关的大量目标语言文本。提供单语言语料库可使翻译更加流畅、自然，从而提高直译质量。

    要成功培训定制模型，单语言语料库文档必须至少包含 1,000 个语句。

所有上传的词汇表和语料库文件的累积文件大小限制为 250 MB。根据上传文件的大小，培训的范围可以从几分钟（一个词汇表）到数小时（一个大型语料库）不等。

以下 curl 示例使用的是 `forced_glossary` 文件选项。
1. 下载[培训数据的结构](#structure)部分中的 TMX 文件样本。
1. 使用法语新闻域 (en-fr) 作为基础模型。TMX 文件中指定的所有内容会完全覆盖原始域数据。

    要查找 {{site.data.keyword.languagetranslatorshort}} 服务支持的所有模型域，请使用 `GET v2/models` 方法：

```curl
curl -u "{username}":"{password}" -X POST -F base_model_id=en-fr -F name="test_glossary" -F forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

`POST /v2/models` 方法使用 `200` 代码和新的 `model_id` 进行响应。使用这一新定制的模型来翻译文本时，请使用 `model_id`。

## 监视培训

TMX 培训文件的大小会影响 `POST /v2/models` 请求的培训时间。要监视培训进度以及培训是否成功完成，请使用 `GET /v2/models/<model_id>` 方法，并查看响应中 `status` 参数的值。

此示例命令提供有关该模型的信息，并检查在[培训翻译模型](#training)部分中开始的培训的状态。此命令使用空主体请求。

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}

`STATUS` 响应参数描述培训过程中模型的状态：

- `uploading`
- `uploaded`
- `dispatching`
- `queued@<#>`
- `training`
- `trained`
- `publishing`
- `available`

模型状态为 `available` 时，说明模型已准备就绪，可以用于服务实例。如果模型已删除，或者如果在培训过程中遇到错误，那么可能会看到下列其中一个错误：

- `deleted`
- `error`

## 使用定制翻译模型

培训定制翻译模型后，指定该翻译模型的 model\_id 以用于 `POST /v2/translate` 或 `GET /v2/translate` 方法。

以下示例调用在[培训定制翻译模型](#training)部分中定制的“英语至法语”模型。

```curl
curl -u "{username}":"{password}" --header "Content-Type: application/json" -X POST --data "{\"model_id\": \"3e7dfdbe-f757-4150-afee-458e71eb93fb\",\"text\": \"Hello, my name is Watson, and I work for International Business Machines. How can I help you today?\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate 
```
{: codeblock}

{{site.data.keyword.languagetranslatorshort}} 服务使用 BLEU（双语评估替代技术）标准以及 IBM 开发的标准来评估翻译质量。结果可能因语言对、所用本地语言或数据域而异。

## 删除定制翻译模型

如果翻译模型过时，您可能想要将其删除。要删除定制翻译模型，请使用 `DELETE /v2/models/<model_id>` 方法。要检索所有翻译模型（不管是定制模型还是缺省模型）的模型标识，请使用 `GET /v2/models` 方法。

以下命令将删除在这些示例中创建的翻译模型。

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}


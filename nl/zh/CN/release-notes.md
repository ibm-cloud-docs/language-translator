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

# 发行说明

可以使用以下新功能和服务更改。
{: shortdesc}

## 2018 年 1 月 12 日
{: #12-january-2018}

新的 Neural Machine Translation (NMT) 模型可供预览。您可以尝试将 NMT 模型用于以下语言对。 

- 英语与以下语言互译：阿拉伯语、中文、荷兰语、法语、德语、意大利语、日语、韩语、波兰语、葡萄牙语（巴西）、俄语、西班牙语和土耳其语
- 法语与以下语言互译：德语和西班牙语
- 德语与以下语言互译：意大利语

*NMT 模型及其使用语法在预览期间可能会更改。目前，NMT 模型不支持语料库定制。仅支持必备词汇表定制。*

要使用 NMT 预览模型进行翻译，请指定 `X-Watson-Technology-Preview:2017-07-01` 头以及要使用的模型的源语言和目标语言的字符代码。以下示例显示如何使用 NMT 预览模型将英语翻译成西班牙语。

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}


## 2016 年 12 月 15 日
{: #15-december-2016}

添加了其他“新闻”翻译模型：英语与日语互译

## 2016 年 11 月 15 日
{: #15-november-2016}

先前可用于 {{site.data.keyword.languagetranslatorshort}} 服务的工具不再可用或不再受支持。 

有关如何使用 {{site.data.keyword.languagetranslatorshort}} API 来完成 {{site.data.keyword.languagetranslatorshort}} 工具支持的各项任务的信息，请联系销售代表或客户支持。

## 2016 年 9 月 1 日
{: #1-september-2016}

IBM Watson&trade; Language Translation 服务更名为 {{site.data.keyword.languagetranslatorshort}} 服务。

## 2016 年 3 月 22 日
{: #22-march-2016}

添加了对其他语言的支持：英语与意大利语互译，以及西班牙语与法语互译。

## 2015 年 12 月 3 日
{: #3-december-2015}

从 2016 年 1 月 15 日开始，标准套餐中的所有定制功能将停止使用。未使用定制功能的应用程序无需更改，因为对于与定制或定制模型无关的所有 API 调用，标准套餐会保持有效。要将 {{site.data.keyword.languagetranslatorshort}} 服务的 GA 定制功能（可培训套餐）与使用早先服务实例的 {{site.data.keyword.cloud}} 应用程序一起使用，请完成以下步骤：

1.  创建新的 Watson {{site.data.keyword.languagetranslatorshort}} 实例并指定 GA“可培训”套餐。
1.  将新的“可培训”服务实例绑定到 {{site.data.keyword.cloud_notm}} 中的应用程序。
1.  收集用于初始创建定制模型的数据。有关更多信息，请参阅[培训数据的结构](/docs/services/language-translator/customizing.html#structure)。
1.  上传培训数据以在“可训练”实例上创建新的定制模型。有关更多信息，请参阅[培训定制翻译模型](/docs/services/language-translator/customizing.html#training)。
1.  在应用程序中，使“ModelID”字段指向新的定制模型。
1.  取消早先服务与 {{site.data.keyword.cloud_notm}} 中应用程序的绑定，然后将其删除。

## 2015 年 11 月 6 日
{: #6-november-2015}

发布了 {{site.data.keyword.languagetranslatorshort}} 工具 Beta。该工具是一个 Web 应用程序，提供图形用户界面来管理和培训模型，以实现更准确的机器翻译。您可以创建项目，上传培训数据，培训定制模型以及翻译文本。

## 2014 年 12 月 1 日
{: #1-december-2014}

Beta Machine Translator 和 Beta Language Identification API 已升级并合并到 {{site.data.keyword.languagetranslatorshort}} API 中。要立即开始使用新服务，请了解并更新代码以反映以下更改：

- **新的 model\_id 参数**：在 Beta API 中，您定义了 `sid` 参数来选择要用于翻译的模型。在此版本中，`sid` 参数重命名为 `model_id` 参数。要检索 `model_id` 允许的值，请使用 `GET/language  translator/api/v2/models` 操作。这将返回所有模型及其对应的 `model_id` 值的列表。
- **语言对支持**：现在，可以不选择 `model_id`，而改为指定源语言和目标语言，并且模型将缺省为在常规新闻域上进行培训的语言。
- **JSON 请求主体支持**：现在，发出 POST 翻译请求时，可以将该请求作为 JSON 提交项发出。JSON 格式支持提交多段进行翻译，而不仅仅是以表单提交形式提交一段文本。
- **JSON 响应主体支持**：翻译请求返回支持 JSON 格式以及纯文本格式。JSON 格式允许支持以多段形式（而不是一段文本的形式）返回翻译后的字词。
- **Accept 头支持**：现在，可以使用 accept 头在所有操作中定义响应格式（text/plain 或 application/json）。
- **语言标识支持**：此 API 中添加了语言标识方法。此方法支持识别输入文本的语言，并列出此 API 可检测到的所有受支持的语言。


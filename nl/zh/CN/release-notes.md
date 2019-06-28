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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# 发行说明

可以使用以下新功能和服务更改。
{: shortdesc}

## 新的 API 认证过程
{: #iam-auth-process }

{{site.data.keyword.languagetranslatorshort}} 服务针对以下位置中托管的服务实例采用了新的 API 认证过程：

- 达拉斯（自 2018 年 6 月 15 日起）
- 法兰克福（自 2018 年 6 月 15 日起）
- 伦敦
- 悉尼（自 2018 年 6 月 12 日起）
- 东京
- 华盛顿（自 2018 年 6 月 12 日起）

{{site.data.keyword.cloud_notm}} 正在迁移到基于令牌的 Identity and Access Management (IAM) 认证。对于某些服务实例，可使用 IAM 向 API 进行认证。

- 对于在先前指示的位置中创建的_新_服务实例，可使用 IAM 进行认证。您可以传递不记名令牌或 API 密钥。令牌支持已认证的请求，而无需在每次调用中都嵌入服务凭证。API 密钥使用基本认证。

    使用任何 Watson SDK 时，都可以传递 API 密钥，并让 SDK 管理令牌的生命周期。有关更多信息和示例，请参阅 API 参考中的[认证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/apidocs/language-translator#authentication){: new_window}。
- 对于在所指示日期之前创建的_现有_服务实例，将继续通过为服务实例提供用户名和密码来进行认证。最终，需要将这些服务实例迁移到 IAM 认证。将提供有关迁移过程和日期的更新。有关迁移的更多信息，请参阅[将 Cloud Foundry 服务实例迁移到资源组](/docs/resources?topic=resources-migrate#migrate)。

要了解该使用哪种认证，请通过单击 [{{site.data.keyword.cloud_notm}} 资源页面 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/resources){: new_window} 上的服务实例来查看服务凭证。

## 服务 API 版本控制
{: shortdesc}

{{site.data.keyword.languagetranslatorshort}} V3 中的 API 请求需要使用 version 参数，该参数采用格式为 `version=YYYY-MM-DD` 的日期。每当我们以向后不兼容方式更改 API 时，都会发布该 API 的新的次版本。

version 参数随每个 API 请求一起发送。服务会使用您指定日期的 API 版本，或该日期之前的最新版本。不要缺省使用当前日期。请改为指定与应用程序兼容的版本的匹配日期，并且在应用程序准备好用于更高版本之前，不要对其进行更改。

当前版本为 `2018-05-01`。

## 2019 年 6 月 14 日
{: #14-june-2019}

现在，新的[翻译模型](/docs/services/language-translator?topic=language-translator-translation-models)可用于英语和希腊语。
- 英语到希腊语 (en-el)
- 希腊语到英语 (el-en)

## 2019 年 6 月 13 日
{: #13-june-2019}

现在，新的[翻译模型](/docs/services/language-translator?topic=language-translator-translation-models)可用于英语和希伯来语。
- 英语到希伯来语 (en-he)
- 希伯来语到英语 (he-en)

## 2019 年 3 月 21 日
{: #21-march-2019}

从 2019 年 3 月 21 日起，您只能查看与已分配给您 {{site.data.keyword.cloud_notm}} 帐户的角色关联的服务凭证信息。例如，如果您分配有`读取者`角色，那么不会显示任何`写入者`或更高级别的服务凭证。

此更改不会影响使用现有服务密钥凭证的用户或应用程序的 API 访问权。只有查看 {{site.data.keyword.cloud_notm}} 中的凭证受影响。

有关服务密钥和用户角色的更多信息，请参阅 [IAM 服务 API 密钥](/docs/services/watson?topic=watson-api-key-bp#api-key-bp)。

## 2018 年 12 月 14 日
{: #14-december-2018}

- 现在，您可以在 {{site.data.keyword.cloud_notm}} 伦敦位置创建 {{site.data.keyword.languagetranslatorshort}} 服务实例。

## 2018 年 11 月 16 日
{: #16-november-2018}

- [翻译文档 (Beta)](/docs/services/language-translator?topic=language-translator-translating-documents) 现在通过新的 API 端点提供。请提交具有受支持文件格式的 Microsoft Office 文档、PDF 或其他文档，然后 {{site.data.keyword.languagetranslatorshort}} 将提供保留原始格式的翻译副本。

  - [受支持文件格式](/docs/services/language-translator?topic=language-translator-translating-documents#supported-file-types)包括 `.doc`、`.ppt` 和 `.pdf` 等。

- 现在，用于匈牙利语的新[翻译模型](/docs/services/language-translator?topic=language-translator-translation-models)可用：
  - 匈牙利语到英语 (hu-en)
  - 英语到匈牙利语 (en-hu)

## 2018 年 11 月 8 日
{: #8-november-2018}

- 现在，您可以在 {{site.data.keyword.cloud_notm}} 东京位置创建 {{site.data.keyword.languagetranslatorshort}} 服务实例。

## 2018 年 8 月 9 日
{: #9-august-2018}

现在，用于挪威博克马尔语的新[翻译模型](/docs/services/language-translator?topic=language-translator-translation-models)可用：
  - 挪威博克马尔语到英语 (nb-en)
  - 英语到挪威博克马尔语 (en-nb)

## 2018 年 6 月 27 日
{: #27-june-2018}

现在，具有六种新语言的新[翻译模型](/docs/services/language-translator?topic=language-translator-translation-models)可用：
  - 加泰罗尼亚语
    - 加泰罗尼亚语到西班牙语 (ca-es)
    - 西班牙语到加泰罗尼亚语 (es-ca)
  -      捷克语
    
    - 捷克语到英语 (cs-en)
    - 英语到捷克语 (en-cs)
  -      丹麦语
    
    - 丹麦语到英语 (da-en)
    - 英语到丹麦语 (en-da)
  -      芬兰语
    
    - 芬兰语到英语 (fi-en)
    - 英语到芬兰语 (en-fi)
  -      印地语
    
    - 印地语到英语 (hi-en)
    - 英语到印地语 (en-hi)
  -      瑞典语
    
    - 瑞典语到英语 (sv-en)
    - 英语到瑞典语 (en-sv)
  

## 2018 年 6 月 15 日
{: #15-june-2018}

从 2018 年 6 月 15 日开始，在德国和美国南部区域创建的新服务实例将使用 [Identity and Access Management (IAM) 认证](#iam-auth-process)。

在德国和美国南部创建的新服务实例将不再与 Language Translator V2 兼容。如果使用的是 Language Translator V2，并且计划在应用程序中使用新的服务实例，那么需要[迁移到 V3 API](/docs/services/language-translator?topic=language-translator-migrating)。

## 2018 年 6 月 12 日
{: #12-june-2018}

{{site.data.keyword.languagetranslatorshort}} V3 现在可用。V2 Language Translator API 在 2018 年 7 月 31 日后将不再可用。要利用最新的服务增强功能，请迁移到 V3 API。请查看[迁移到 Language Translator V3](/docs/services/language-translator?topic=language-translator-migrating) 页面以获取更多信息。

### V3 中的新增功能
{: #whats-new}

-  {{site.data.keyword.languagetranslatorshort}} API V3 随附 **Neural Machine Translation** (NMT) 模型，翻译结果有显著改进。现在，所有 NMT 模型都可进行定制。
-  将定制模型用作特殊词汇表定制的基本模型。
-  API V3 是已引退 API V2 的经过简化的全 JSON 子集。
-  引入了 API 版本日期，以支持开发者自由地按自己的节奏采用未来的 API 更改。

### 重大更改
{: #breaking-changes}

- 强制所有 API 端点使用版本日期：API V3 请求需要格式为 `version=YYYY-MM-DD` 的版本日期查询参数。最新的 API 版本为 `version=2018-05-01`。
- 简化后的 API：
  - **翻译**和**识别**方法不提供在 V3 中返回纯文本响应的选项。这两个方法仅返回 JSON 响应。
  - V3 中不支持 `GET /translate` 和 `GET /identify` 方法。请改为使用 `POST /translate` 和 `POST /identify` 方法。 
- V3 中不支持单语言语料库定制。
- 现在，要创建使用平行语料库和特殊词汇表的定制模型，需要在两个 API 调用中执行。首先，使用平行语料库来定制模型。在定制模型完成训练后，使用特殊词汇表再次对该模型进行定制。此更改允许您将以平行语料库训练的定制模型用作特殊词汇表定制的基础。
- 专用的专利和会话领域模型在 V3 API 中不可用。与旧版专业模型相比，专利和会话领域中的 NMT 模型提供的翻译质量总体上有所提高。
- 重命名了错误对象键，以使其与其他 Watson API 一致。`error_code` 已重命名为 `code`，`error_message` 已重命名为 `error`。

### IAM 认证

从 2018 年 6 月 12 日开始，在悉尼和美国东部区域创建的新服务实例将使用 [Identity and Access Management (IAM) 认证](#iam-auth-process)。

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

您可以观看 [YouTube 上的引导视频 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://youtu.be/L6ZC0QaUZ2k)，此视频通过 NMT 预览说明了如何设置 {{site.data.keyword.languagetranslatorshort}}。


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

从 2016 年 1 月 15 日开始，标准套餐中的所有定制功能将停止使用。未使用定制功能的应用程序无需更改，因为对于与定制或定制模型无关的所有 API 调用，标准套餐会保持有效。要将 {{site.data.keyword.languagetranslatorshort}} 服务的 GA 定制功能（可训练套餐）与使用早先服务实例的 {{site.data.keyword.cloud}} 应用程序一起使用，请完成以下步骤：

1.  创建新的 Watson {{site.data.keyword.languagetranslatorshort}} 实例并指定 GA“可训练”套餐。
2.  将新的“可训练”服务实例绑定到 {{site.data.keyword.cloud_notm}} 中的应用程序。
3.  收集用于初始创建定制模型的数据。有关更多信息，请参阅[训练数据的结构](/docs/services/language-translator?topic=language-translator-customizing#structure)。
4.  上传训练数据以在“可训练”实例上创建新的定制模型。有关更多信息，请参阅[训练定制翻译模型](/docs/services/language-translator?topic=language-translator-customizing#training)。
5.  在应用程序中，使“ModelID”字段指向新的定制模型。
6.  取消早先服务与 {{site.data.keyword.cloud_notm}} 中应用程序的绑定，然后将其删除。

## 2015 年 11 月 6 日
{: #6-november-2015}

发布了 {{site.data.keyword.languagetranslatorshort}} 工具 Beta。该工具是一个 Web 应用程序，提供图形用户界面来管理和训练模型，以实现更准确的机器翻译。您可以创建项目，上传训练数据，训练定制模型以及翻译文本。

## 2014 年 12 月 1 日
{: #1-december-2014}

Beta Machine Translator 和 Beta Language Identification API 已升级并合并到 {{site.data.keyword.languagetranslatorshort}} API 中。要立即开始使用新服务，请了解并更新代码以反映以下更改：

- **新的 model\_id 参数**：在 Beta API 中，您定义了 `sid` 参数来选择要用于翻译的模型。在此版本中，`sid` 参数重命名为 `model_id` 参数。要检索 `model_id` 允许的值，请使用 `GET/language  translator/api/v2/models` 操作。这将返回所有模型及其对应的 `model_id` 值的列表。
- **语言对支持**：现在，可以不选择 `model_id`，而改为指定源语言和目标语言，并且模型将缺省为在常规新闻域上进行训练的语言。
- **JSON 请求主体支持**：现在，发出 POST 翻译请求时，可以将该请求作为 JSON 提交项发出。JSON 格式支持提交多段进行翻译，而不仅仅是以表单提交形式提交一段文本。
- **JSON 响应主体支持**：翻译请求返回支持 JSON 格式以及纯文本格式。JSON 格式允许支持以多段形式（而不是一段文本的形式）返回翻译后的字词。
- **Accept 头支持**：现在，可以使用 accept 头在所有操作中定义响应格式（text/plain 或 application/json）。
- **语言标识支持**：此 API 中添加了语言标识方法。此方法支持识别输入文本的语言，并列出此 API 可检测到的所有受支持的语言。

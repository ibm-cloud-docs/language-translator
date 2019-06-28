---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-04"

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

# 信息安全
{: #information-security}

IBM 致力于为客户和合作伙伴提供创新的数据隐私、安全和监管解决方案。
{: shortdesc}

**声明：**
客户应负责确保自身遵守各种法律和法规，包括《欧盟一般数据保护条例》。客户须自行负责从合格的法律顾问那里，就可能会影响客户业务和客户为了遵守此类法律和法规需要采取的任何行动，获得关于任何相关法律和法规的认定和解释的意见。

此处描述的产品、服务和其他功能并不适用于所有客户情形，并且在可用性方面可能有限制。IBM 不提供法律、核算或审计建议，也不表示或保证其服务或产品可以确保客户遵守任何法律或法规。

如果需要为创建的 {{site.data.keyword.cloud}} {{site.data.keyword.watson}} 资源请求 GDPR 支持

-   在欧盟 (EU)，请参阅[请求对欧盟内创建的 IBM Cloud Watson 资源的支持](/docs/services/watson/getting-started-gdpr-sar.html#request-EU)。
-   在欧盟以外的地区，请参阅[请求对欧盟以外的资源的支持](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU)。

## 欧盟一般数据保护条例 (GDPR)
{: #gdpr}

IBM 致力于为客户和合作伙伴提供创新的数据隐私、安全和监管解决方案，以协助用户实现 GDPR 合规性。

在[此处 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](../../icons/launch-glyph.svg "外部链接图标")](http://www.ibm.com/gdpr) 了解有关 IBM 自己的 GDPR 就绪性旅程以及支持您合规旅程的 GDPR 功能和产品的更多信息。{: new_window}.

## 在 Language Translator 中标注和删除数据
{: #gdpr-in-service}

{{site.data.keyword.languagetranslatorshort}} 服务对翻译请求中的翻译数据临时进行高速缓存，并存储用于创建定制模型的训练数据。

### 翻译数据和文档
{: #translation-data-and-documents}

在**翻译**方法中将文本发送到 {{site.data.keyword.languagetranslatorshort}} 时，服务会对源文本和翻译结果进行高速缓存，以在后续**翻译**请求中收到相同文本时提高性能。仅当高速缓存的翻译文本在 15 天内未使用时，才会将其删除。

提交给服务以通过**翻译文档**方法翻译的文档会在内部存储，以提供已翻译的文件，并通过引用原始上传的文档来支持其他**翻译文档**请求。仅当原始文档和任何关联的已翻译文档在 15 天内未在后续**翻译文档**请求中使用时，才会删除这些文档。在删除截止期限之前，可以使用**删除文档**方法来删除文档。 

翻译数据和文档会进行动态和静态加密。

### 定制模型训练数据
{: #custom-model-training-data}

训练定制模型时，会存储用于创建模型的训练数据，以向您提供定制模型。定制模型和训练数据都会进行动态和静态加密。加密的训练数据会持久存储在存储器中，直到使用**删除模型**方法删除模型为止。

定制模型只能在模型级别删除。无法删除用于创建定制模型的组件数据。如果在创建定制模型时使用了个人数据，那么必须为每个客户创建一个单独的定制模型，并对模型`名称`进行标注以标识客户，以便可以根据请求删除该模型。 

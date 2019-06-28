---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-04"

---
<!-- Attribute definitions -->
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# 入门教程
{: #gettingstarted}

通过 {{site.data.keyword.languagetranslatorfull}}，您能以编程方式将文本从一种语言翻译成另一种语言。
{:shortdesc}
{: hide-dashboard}

本教程将逐步引导您完成各项命令，以将文本从英语翻译成西班牙语以及确定文本样本的语言。

## 开始之前
{: #prerequisites}

- {: hide-dashboard}创建服务的实例：
    1.  {: hide-dashboard}转至 {{site.data.keyword.Bluemix_notm}}“目录”中的 [{{site.data.keyword.languagetranslatorshort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/catalog/services/language-translator){: new_window} 页面。
    2.  注册免费的 {{site.data.keyword.Bluemix_notm}} 帐户或登录。
    3.  单击**创建**。
- 复制凭证以向服务实例进行认证：
    1.  在**管理**页面上，单击**显示**以查看凭证。
    2.  复制 `API 密钥`和 `URL` 值。
- 确保您有 `curl` 命令：
    - 示例使用 `curl` 命令来调用 HTTP 接口的方法。通过 [curl.haxx.se ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://curl.haxx.se/){: new_window} 来安装适用于您操作系统的版本。请安装支持安全套接字层 (SSL) 协议的版本。确保在 `PATH` 环境变量中包含安装的二进制文件。

本教程使用 API 密钥进行认证。对于生产用途，请确保查看 API 密钥[最佳实践](/docs/services/watson/apikey-bp.html#api-bp)。
{: tip}

## 步骤 1：翻译文本
{: #translate-text}

使用以下示例将“Hello， world!”和“How are you?”这两个短语从英语翻译成西班牙语。<span class="hide-dashboard">将 `{apikey}` 和 `{url}` 替换为您的服务凭证。</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## 步骤 2：确定语言
{: #identify-language}

使用以下示例来确定文本的语言。<span class="hide-dashboard">将 `{apikey}` 和 `{url}` 替换为您的服务凭证。</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## 后续步骤
{: #next-steps}

- 了解如何[定制](/docs/services/language-translator?topic=language-translator-customizing) {{site.data.keyword.languagetranslatorshort}} 以适合您的用例
- 试用[翻译文档 (Beta)](/docs/services/language-translator?topic=language-translator-document-translator-tutorial)
- 查看 [API 参考](https://{DomainName}/apidocs/language-translator)
- 探索[样本应用程序](/docs/services/language-translator?topic=language-translator-sample-applications)
- 查看语言支持信息：
    - [翻译模型](/docs/services/language-translator?topic=language-translator-translation-models)
    - [可识别语言](/docs/services/language-translator?topic=language-translator-identifiable-languages)

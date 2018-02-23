---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

---
<!-- Attribute definitions -->
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# 入门教程
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} 支持以编程方式翻译新闻、对话和专利域中的文本。本教程将逐步引导您完成各项命令，以将一些样本内容从英语翻译成西班牙语以及选择域。
{:shortdesc}

## 开始之前
{: #prerequisites}

- 创建服务的实例：
    - {: download} 如果您看到此内容，说明您已创建服务实例。现在，请获取凭证。
    - 通过服务创建项目：
        1.  转至 {{site.data.keyword.watson}} 开发者控制台[服务 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.{DomainName}/developer/watson/services){: new_window} 页面。
        1.  选择 {{site.data.keyword.languagetranslatorshort}}，单击**添加服务**，然后注册免费 {{site.data.keyword.Bluemix_notm}} 帐户或登录。
        1.  输入 `language-tutorial` 作为项目名称，然后单击**创建项目**。
- 复制凭证以向服务实例进行认证：
    - {: download} 在服务仪表板（您正在查看的对象）中：
        1.  单击**服务凭证**选项卡。
        1.  单击**操作**下的**查看凭证**。
        1.  复制 `username`、`password` 和 `url` 值。
        {: download}
    - 在开发者控制台的 **language-tutorial** 项目中，复制**凭证**部分中 `"language_translator"` 的 `username`、`password` 和 `url` 值。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

如果使用的是 {{site.data.keyword.Bluemix_dedicated_notm}}，请在“目录”的 [{{site.data.keyword.languagetranslatorshort}} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.{DomainName}/catalog/services/language-translator/){: new_window} 页面中创建服务实例。有关如何找到服务凭证的详细信息，请参阅 [Watson 服务的服务凭证 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 步骤 1：翻译文本
{: #translate-text}

使用以下示例将“Hello, world!”从英语翻译成西班牙语。将 `{username}` 和 `{password}` 替换为在上一步中复制的服务凭证。

```bash
curl -X POST --user {username}:{password} --header "Accept: application/json" --data "{\"text\":\"Hello, world\",\"source\":\"en\",\"target\":\"es\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{:codeblock}

现在，提供改进翻译的新 Neural Machine Translation 模型可供预览。有关更多详细信息，请参阅[发行说明](release-notes.html#12-january-2018)。
{: tip}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  version: 'v2',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
});
language_translator.translate({
    text: 'Hello, world!',
    source: 'en',
    target: 'es'
  },
  function(err, translation) {
    if (err)
      console.log(err)
    else
      console.log(translation);
});
```
{:node}
{:codeblock} -->

<!-- ```java
LanguageTranslator service = new LanguageTranslator();
service.setUsernameAndPassword("username","password");

TranslationResult result = service.translate("Hello, world!", "en", "es");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
    username="username",
    password="password")

translation = language_translator.translate(
    text="Hello, world!",
    source="en",
    target="es"
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->


## 步骤 2：尝试特定于域的模型
{: #specify-model}

{{site.data.keyword.languagetranslatorshort}} 具有针对新闻、对话和专利域的专用模型。在步骤 2 中指定 `source` 和 `target` 语言时，该服务通常缺省为该翻译路径的新闻域模型。要使用特定于域的模型，请指定 `model_id`，而不是 `source` 和 `target` 语言。如果创建了[定制模型](customizing.html)，还可以使用定制模型。

_包含 [NMT 预览头](release-notes.html#12-january-2018)的请求不支持特定于域的模型。_

以下示例使用英语到西班牙语对话模型翻译“Hey world, whats up?”。请将 `{username}` 和 `{password}` 替换为您的信息：

```bash
curl -X POST --user {username}:{password} --header "Content-Type: application/json" --header "Accept: application/json" --data "{\"text\":\"Hey world, whats up?\",\"model_id\":\"en-es-conversational\"}" "https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{:codeblock}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
  version: 'v2',
});
language_translator.translate({
    text: 'Hey, world! What's up?',
    model_id: 'en-es-conversational'
  },
  function(err, translation) {
    if (err)
      console.log(err)
    else
      console.log(translation);
});
```
{:node}
{:codeblock} -->

<!-- ```java
LanguageTranslator service = new LanguageTranslator();
service.setUsernameAndPassword("username","password");

TranslationResult result = service.translate("Hey, world! What's up?", "en-es-conversational");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```python
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
  username="username",
  password="password"
)

translation = language_translator.translate(
  text="Hey, world! What's up?",
  model_id="en-es-conversational"
)
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->

可以使用 [List models ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models){: new_window} 方法来查看服务实例的可用模型。
{:tip}

## 后续步骤
{: #next-steps}

- 了解如何[定制](/docs/services/language-translator/customizing.html) {{site.data.keyword.languagetranslatorshort}} 以适合您的用例。
- 查看 [API 参考 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){:new_window}。
- 在 [API Explorer ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){:new_window} 中与 API 进行交互。
- 试用 [Node.js 样本应用程序 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/language-translator-nodejs){:new_window}。

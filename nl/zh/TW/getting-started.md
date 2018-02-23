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

# 入門指導教學
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} 可讓您以程式方式翻譯新聞、交談式及專利領域中的文字。此指導教學會透過指令逐步引導您將部分範例內容從英文翻譯為西班牙文，以及選擇領域。
{:shortdesc}

## 開始之前
{: #prerequisites}

- 建立服務的實例：
    - {: download} 如果看到這個，表示您已建立服務實例。現在請取得您的認證。
    - 從服務中建立專案：
        1.  移至「{{site.data.keyword.watson}} 開發人員主控台[服務」![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/developer/watson/services){: new_window} 頁面。
        1.  選取 {{site.data.keyword.languagetranslatorshort}}、按一下**新增服務**，然後註冊以取得免費的 {{site.data.keyword.Bluemix_notm}} 帳戶或登入。
        1.  鍵入 `language-tutorial` 作為專案名稱，然後按一下**建立專案**。
- 複製認證以對您的服務實例進行鑑別：
    - {: download} 從服務儀表板（您正在查看之處）中：
        1.  按一下**服務認證**標籤。
        1.  按一下**動作**下的**檢視認證**。
        1.  複製 `username`、`password` 及 `url` 值。
        {: download}
    - 從 Developer Console 中的 **language-tutorial** 專案中，複製來自**認證**區段之 `"language_translator"` 的 `username`、`password` 及 `url` 值。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

如果您使用 {{site.data.keyword.Bluemix_dedicated_notm}}，請從「型錄」中的 [{{site.data.keyword.languagetranslatorshort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/catalog/services/language-translator/){: new_window} 頁面建立服務實例。如需如何尋找服務認證的詳細資料，請參閱 [Watson 服務的服務認證 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 步驟 1：翻譯文字
{: #translate-text}

請使用下列範例，將 "Hello, world!" 從英文翻譯成西班牙文。將 `{username}` 及 `{password}` 換成已在前一個步驟中複製的服務認證。

```bash
curl -X POST --user {username}:{password} --header "Accept: application/json" --data "{\"text\":\"Hello, world\",\"source\":\"en\",\"target\":\"es\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{:codeblock}

新的「神經機器翻譯」模型現在可供預覽，此模型提供了改善的翻譯。如需詳細資料，請參閱[版本注意事項](release-notes.html#12-january-2018)。
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


## 步驟 2：嘗試領域特定模型
{: #specify-model}

{{site.data.keyword.languagetranslatorshort}} 已特殊化新聞、交談式及專利領域的模型。當您在步驟 2 中指定 `source` 及 `target` 語言時，服務通常會預設為該翻譯路徑的新聞領域模型。若要使用領域特定模型，請指定 `model_id`，而不是 `source` 及 `target` 語言。如果已建立[自訂模型](customizing.html)，則您也可以使用它。

_包含 [NMT 預覽標頭](release-notes.html#12-january-2018)的要求中不支援領域特定模型。_

下列範例會使用英文至西班牙文交談式模型，翻譯 "Hey world, whats up?"。將 `{username}` 及 `{password}` 換成您的資訊：

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

您可以使用[清單模型 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models){: new_window} 方法，來檢視可供服務實例使用的方法。
{:tip}

## 後續步驟
{: #next-steps}

- 學習如何[自訂](/docs/services/language-translator/customizing.html) {{site.data.keyword.languagetranslatorshort}}，為您的使用案例工作。
- 檢視 [API 參考資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){:new_window}。
- 與 [API 瀏覽器中的 API 互動 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){:new_window}。
- 嘗試 [Node.js 範例應用程式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/language-translator-nodejs){:new_window}。

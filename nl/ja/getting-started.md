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

# 入門チュートリアル
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} を使用すると、ニュース・ドメイン、会話ドメイン、特許ドメインのテキストをプログラムで翻訳できます。このチュートリアルでは、サンプル・コンテンツを英語からスペイン語に翻訳するコマンドや、ドメインを選択するコマンドの使用方法について説明します。
{:shortdesc}

## 始めに
{: #prerequisites}

- サービスのインスタンスを作成します。
    - {: download} これが表示されたら、サービス・インスタンスは作成されています。資格情報を入手してください。
    - 以下のようにして、サービスからプロジェクトを作成します。
        1.  {{site.data.keyword.watson}} Developer Console の[サービス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.{DomainName}/developer/watson/services){: new_window} のページに移動します。
        1.  「{{site.data.keyword.languagetranslatorshort}}」を選択し、**「サービスの追加」**をクリックし、無料の {{site.data.keyword.Bluemix_notm}} アカウントに登録するか、ログインします。
        1.  プロジェクト名として `language-tutorial` と入力し、**「Create Project (プロジェクトの作成)」**をクリックします。
- サービス・インスタンスに認証されるための資格情報をコピーします。
    - {: download} サービス・ダッシュボード (現在表示されているもの) から以下を実行します。
        1.  **「サービス資格情報」**タブをクリックします。
        1.  **「アクション」**の下の**「資格情報の表示」**をクリックします。
        1.  `username`、`password`、`url` の値をコピーします。
        {: download}
    - Developer Console で**「language-tutorial」**プロジェクトの**「資格情報」**セクションから、`"language_translator"` の `username`、`password`、`url` 値をコピーします。

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

{{site.data.keyword.Bluemix_dedicated_notm}} を使用している場合は、カタログ内の [{{site.data.keyword.languagetranslatorshort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.{DomainName}/catalog/services/language-translator/){: new_window} のページからサービス・インスタンスを作成します。サービス資格情報を見つける方法について詳しくは、[Watson サービスのサービス資格情報 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window} を参照してください。

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 手順 1: テキストの翻訳
{: #translate-text}

以下の例を使用して、「Hello, world!」を英語からスペイン語に翻訳します。`{username}` と `{password}` を、前の手順でコピーしたサービス資格情報に置き換えます。

```bash
curl -X POST --user {username}:{password} --header "Accept: application/json" --data "{\"text\":\"Hello, world\",\"source\":\"en\",\"target\":\"es\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{:codeblock}

現在、優れた翻訳品質の新しいニューラル機械翻訳モデルのプレビュー版が提供されています。詳細については、[リリース・ノート](release-notes.html#12-january-2018)を参照してください。
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


## 手順 2: ドメイン固有のモデルの試用
{: #specify-model}

{{site.data.keyword.languagetranslatorshort}} には、ニュース・ドメイン、会話ドメイン、特許ドメインのために特化したモデルが用意されています。手順 2 のように `source` と `target` の言語を指定すると、通常、サービスはその翻訳パスにニュース・ドメイン・モデルを使用します。ドメイン固有のモデルを使用するには、`source` と `target` の言語ではなく `model_id` を指定してください。[カスタム・モデル](customizing.html)を作成した場合は、そのモデルを使用することもできます。

_[NMT プレビュー・ヘッダー](release-notes.html#12-january-2018)を含む要求では、ドメイン固有のモデルはサポートされません。_

以下の例では、英語からスペイン語への会話モデルを使用して、「Hey world, whats up?」を翻訳します。`{username}` と `{password}` は、ご自分の情報に置き換えてください。

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

[モデルをリストする ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models){: new_window} メソッドを使用して、サービス・インスタンスで使用できるモデルを表示できます。
{:tip}

## 次の手順
{: #next-steps}

- ユース・ケースに合わせて、{{site.data.keyword.languagetranslatorshort}} を[カスタマイズ](/docs/services/language-translator/customizing.html)する方法を学びます。
- [API リファレンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){:new_window} を参照してください。
- [API Explorer ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){:new_window} の API と対話します。
- [Node.js サンプル・アプリ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/language-translator-nodejs){:new_window}を試します。

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

# 시작하기 튜토리얼
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}}를 사용하면 뉴스, 대화식 및 특허 도메인의 텍스트를 프로그래밍 방식으로 변환할 수 있습니다. 이 튜토리얼에서는 일부 영어 샘플 컨텐츠를 스페인어로 변환하고 도메인을 선택하는 명령을 안내합니다.
{:shortdesc}

## 시작하기 전에 
{: #prerequisites}

- 서비스의 인스턴스를 작성하십시오. 
    - {: download} 이를 볼 수 있으면 서비스 인스턴스가 작성된 것입니다. 이제 신임 정보를 가져오십시오. 
    - 서비스에서 프로젝트를 작성하십시오. 
        1.  {{site.data.keyword.watson}} 개발자 콘솔 [서비스 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/developer/watson/services){: new_window} 페이지로 이동하십시오. 
        1.  {{site.data.keyword.languagetranslatorshort}}를 선택하고 **서비스 추가**를 클릭한 후에 무료 {{site.data.keyword.Bluemix_notm}} 계정에 등록하거나 로그인하십시오. 
        1.  `language-tutorial`을 프로젝트 이름으로 입력하고 **프로젝트 작성**을 클릭하십시오. 
- 서비스 인스턴스의 인증을 위한 신임 정보를 복사하십시오. 
    - {: download} (현재 보이는) 서비스 대시보드에서 다음을 수행하십시오. 
        1.  **서비스 신임 정보** 탭을 클릭하십시오. 
        1.  **조치** 아래에서 **신임 정보 보기**를 클릭하십시오. 
        1.  `username`, `password` 및 `url` 값을 복사하십시오.
        {: download}
    - 개발자 콘솔의 **language-tutorial** 프로젝트에서 **신임 정보** 섹션의 `"language_translator"`에 대한 `username`, `password` 및 `url` 값을 복사하십시오. 

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

{{site.data.keyword.Bluemix_dedicated_notm}}를 사용하는 경우에는 카탈로그의 [{{site.data.keyword.languagetranslatorshort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/catalog/services/language-translator/){: new_window} 페이지에서 서비스 인스턴스를 작성하십시오. 서비스 신임 정보를 찾는 방법에 대한 세부사항은 [Watson 서비스의 서비스 신임 정보 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}를 참조하십시오. 

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## 1단계: 텍스트 변환
{: #translate-text}

다음 예제를 사용하여 영어 "Hello, world!"를 스페인어로 변환할 수 있습니다. `{username}` 및 `{password}`를 이전 단계에서 복사한 서비스 신임 정보로 대체하십시오. 

```bash
curl -X POST --user {username}:{password} --header "Accept: application/json" --data "{\"text\":\"Hello, world\",\"source\":\"en\",\"target\":\"es\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{:codeblock}

개선된 변환을 제공하는 새 NMT(Neural Machine Translation) 모델의 미리보기를 이제 사용할 수 있습니다. 추가 세부사항은 [릴리스 정보](release-notes.html#12-january-2018)를 참조하십시오.
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


## 2단계: 도메인 특정 모델 시도
{: #specify-model}

{{site.data.keyword.languagetranslatorshort}}에는 뉴스, 대화식 및 특허 도메인에 대한 특정 모델이 있습니다. 2단계의 경우처럼 `source` 및 `target` 언어를 지정하는 경우, 서비스는 일반적으로 해당 변환 경로에 대한 뉴스 도메인 모델을 기본값으로 사용합니다. 도메인 특정 모델을 사용하려면 `source` 및 `target` 언어 대신에 `model_id`를 지정하십시오. [사용자 정의 모델](customizing.html)을 작성했으면 이를 사용할 수도 있습니다. 

_도메인 특정 모델은 [NMT 미리보기 헤더](release-notes.html#12-january-2018)가 포함된 요청에서는 지원되지 않습니다._

다음 예제는 "Hey world, whats up?"을 영어-스페인어 대화식 모델로 변환합니다. `{username}` 및 `{password}`를 사용자의 정보로 대체하십시오. 

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

[모델 나열 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models){: new_window} 메소드를 사용하여 서비스 인스턴스에 대해 사용 가능한 모델을 볼 수 있습니다.
{:tip}

## 다음 단계
{: #next-steps}

- 유스 케이스에 대해 작업하기 위한 {{site.data.keyword.languagetranslatorshort}} [사용자 정의](/docs/services/language-translator/customizing.html) 방법을 학습합니다. 
- [API 참조서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){:new_window}를 봅니다. 
- [API 탐색기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){:new_window}에서 API와 상호작용합니다. 
- [Node.js 샘플 앱 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/watson-developer-cloud/language-translator-nodejs){:new_window}을 사용해 봅니다. 

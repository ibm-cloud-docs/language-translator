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

# 시작하기 튜토리얼
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}}를 사용하면 프로그래밍 방식으로 텍스트를 한 언어에서 다른 언어로 번역할 수 있습니다.
{:shortdesc}
{: hide-dashboard}

이 튜토리얼에서는 텍스트를 영어에서 스페인어로 번역하고 텍스트 샘플의 언어를 식별하는 명령을 단계별로 안내합니다.

## 시작하기 전에
{: #prerequisites}

- {: hide-dashboard}서비스의 인스턴스를 작성하십시오.
    1.  {: hide-dashboard} {{site.data.keyword.Bluemix_notm}} 카탈로그에서 [{{site.data.keyword.languagetranslatorshort}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/catalog/services/language-translator){: new_window} 페이지로 이동하십시오.
    2.  무료 {{site.data.keyword.Bluemix_notm}} 계정에 가입하거나 로그인하십시오.
    3.  **작성**을 클릭하십시오.
- 서비스 인스턴스의 인증을 위한 신임 정보를 복사하십시오.
    1.  **관리** 페이지에서 **표시**를 클릭하여 인증 정보를 보십시오.
    2.  `API Key` 및 `URL` 값을 복사하십시오.
- 다음과 같이 `curl` 명령이 있는지 확인하십시오.
    - 예제에서는 `curl` 명령을 사용하여 HTTP 인터페이스의 메소드를 호출합니다. [curl.haxx.se ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://curl.haxx.se/){: new_window}에서 운영 체제의 버전을 설치하십시오. SSL(Secure Sockets Layer) 프로토콜을 지원하는 버전을 설치하십시오. `PATH` 환경 변수에 설치된 2진 파일을 포함하십시오.

이 튜토리얼에서는 API 키를 사용하여 인증합니다. 프로덕션 용도로 API 키 [우수 사례](/docs/services/watson/apikey-bp.html#api-bp)를 검토하십시오.
{: tip}

## 1단계: 텍스트 번역
{: #translate-text}

다음 예제를 사용하여 두 개의 문구, "Hello, world!" 와 "How are you?"를 스페인어로 변환할 수 있습니다. <span class="hide-dashboard">`{apikey}`와 `{url}`을 서비스 인증 정보로 바꾸십시오.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## 2단계: 언어 식별
{: #identify-language}

다음 예제를 사용하여 텍스트의 언어를 식별하십시오. <span class="hide-dashboard">`{apikey}`와 `{url}`을 서비스 인증 정보로 바꾸십시오.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## 다음 단계
{: #next-steps}

- 유스 케이스에 대해 작업하기 위해 {{site.data.keyword.languagetranslatorshort}} [사용자 정의](/docs/services/language-translator?topic=language-translator-customizing) 방법 알아보기
- [문서 번역(베타)](/docs/services/language-translator?topic=language-translator-document-translator-tutorial)
- [API 참조서](https://{DomainName}/apidocs/language-translator) 보기
- [샘플 애플리케이션](/docs/services/language-translator?topic=language-translator-sample-applications) 탐색
- 언어 지원 정보 보기:
    - [번역 모델](/docs/services/language-translator?topic=language-translator-translation-models)
    - [식별 가능한 언어](/docs/services/language-translator?topic=language-translator-identifiable-languages)

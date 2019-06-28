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

# 릴리스 정보

서비스에 대해 다음의 새 기능과 변경사항을 사용할 수 있습니다.
{: shortdesc}

## 새 API 인증 프로세스
{: #iam-auth-process }

{{site.data.keyword.languagetranslatorshort}} 서비스에는 다음 위치에서 호스팅되는 서비스 인스턴스의 새로운 API 인증 프로세스가 있습니다.

- 2018년 6월 15일 현재, 댈러스
- 2018년 6월 15일 현재, 프랑크푸르트
- 런던
- 2018년 6월 12일 현재, 시드니
- 토쿄
- 2018년 6월 12일 현재, 워싱턴, DC

{{site.data.keyword.cloud_notm}}은 토큰 기반 IAM(Identity and Access Management) 인증으로 마이그레이션합니다. IAM에서 몇 가지 서비스 인스턴스를 사용하여 API를 인증합니다.

- 이전에 표시된 위치에 작성된 _새_ 서비스 인스턴스의 경우 인증에 IAM을 사용합니다. bearer 토큰 또는 API 키를 전달할 수 있습니다. 토큰은 모든 호출에 서비스 인증 정보를 임베드하지 않고 인증된 요청을 지원합니다. API 키에서 기본 인증을 사용합니다.

    Watson SDK를 사용할 때 API 키를 전달하고 SDK를 통해 토큰의 라이프사이클을 관리할 수 있습니다. 자세한 정보와 예는 API 참조서의 [인증 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/apidocs/language-translator#authentication){: new_window}을 참조하십시오.
- 표시된 날짜 전에 작성된 _기존_ 서비스 인스턴스의 경우 서비스 인스턴스의 사용자 이름과 비밀번호를 제공하여 계속 인증합니다. 결국 이 서비스 인스턴스를 IAM 인증으로 마이그레이션해야 합니다. 마이그레이션 프로세스와 날짜에 관한 업데이트가 제공됩니다. 마이그레이션에 관한 자세한 정보는 [Cloud Foundry 서비스 인스턴스를 리소스 그룹에 마이그레이션](/docs/resources?topic=resources-migrate#migrate)을 참조하십시오.

사용할 인증을 찾으려면 [{{site.data.keyword.cloud_notm}} 리소스 페이지 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/resources){: new_window}에서 서비스 인스턴스를 클릭하여 서비스 인증 정보를 확인하십시오.

## 서비스 API 버전화
{: shortdesc}

{{site.data.keyword.languagetranslatorshort}} v3에서 API 요청을 수행하려면 `version=YYYY-MM-DD` 형식의 날짜를 사용하는 버전 매개변수가 필요합니다. 역호환 가능하게 API를 변경할 때마다 새로운 부 버전의 API를 릴리스합니다.

API 요청을 보낼 때마다 버전 매개변수를 함께 보내십시오. 서비스에서는 사용자가 지정한 날짜의 API 버전 또는 해당 날짜 전의 최신 버전을 사용합니다. 기본값을 현재 날짜로 지정하지 마십시오. 대신 앱과 호환 가능한 버전과 일치하는 날짜를 지정하고 앱의 이후 버전이 준비될 때까지 변경하지 마십시오.

현재 버전은 `2018-05-01`입니다.

## 2019년 6월 14일
{: #14-june-2019}

새로운 [번역 모델](/docs/services/language-translator?topic=language-translator-translation-models)은 이제 영어와 그리스어에 사용할 수 있습니다.
- 영어에서 그리스어로(en-el)
- 그리스어에서 영어로(el-en)

## 2019년 6월 13일
{: #13-june-2019}

새로운 [번역 모델](/docs/services/language-translator?topic=language-translator-translation-models)은 이제 영어와 히브리어에 사용할 수 있습니다.
- 영어에서 히브리어로(en-he)
- 히브리어에서 영어로(he-en)

## 2019년 3월 21일
{: #21-march-2019}

2019년 3월 21일부터 {{site.data.keyword.cloud_notm}} 계정에 지정된 역할과 연관된 서비스 인증 정보만 볼 수 있습니다. 예를 들어 `reader` 역할을 지정한 경우 서비스 인증 정보의 `writer` 이상 레벨이 표시되지 않습니다.

이 변경사항은 기존 서비스 키 인증 정보가 있는 사용자나 애플리케이션의 API 액세스에는 영향을 미치지 않습니다. {{site.data.keyword.cloud_notm}}에서 인증 정보를 보는 데만 영향을 미칩니다.

서비스 키와 사용자 역할에 관한 자세한 정보는 [IAM 서비스 API 키](/docs/services/watson?topic=watson-api-key-bp#api-key-bp)를 참조하십시오.

## 2018년 12월 14일
{: #14-december-2018}

- 이제 {{site.data.keyword.cloud_notm}} 런던 위치에 {{site.data.keyword.languagetranslatorshort}} 서비스 인스턴스를 작성할 수 있습니다.

## 2018년 11월 16일
{: #16-november-2018}

- 이제 [번역 문서(베타)](/docs/services/language-translator?topic=language-translator-translating-documents)는 새 API 엔드포인트를 통해 사용할 수 있습니다. Microsoft Office 문서, PDF 또는 지원되는 파일 형식의 기타 문서를 제출하십시오. 그러면 {{site.data.keyword.languagetranslatorshort}}에서 원래 형식을 유지하는 번역된 사본을 제공합니다.
  - [지원되는 파일 형식](/docs/services/language-translator?topic=language-translator-translating-documents#supported-file-types)에는 `.doc`, `.ppt`, `.pdf` 등이 포함됩니다.

- 새로운 헝가리어용 [번역 모델](/docs/services/language-translator?topic=language-translator-translation-models)을 사용할 수 있습니다.
  - 헝가리어에서 영어로(hu-en)
  - 영어에서 헝가리어로(en-hu)

## 2018년 11월 8일
{: #8-november-2018}

- 이제 {{site.data.keyword.cloud_notm}} 토쿄 위치에 {{site.data.keyword.languagetranslatorshort}} 서비스 인스턴스를 작성할 수 있습니다.

## 2018년 8월 9일
{: #9-august-2018}

새로운 노르웨이 부크몰어용 [번역 모델](/docs/services/language-translator?topic=language-translator-translation-models)을 사용할 수 있습니다.
  - 노르웨이 부크몰어에서 영어로(nb-en)
  - 영어에서 노르웨이 부크몰어로)en-nb)

## 2018년 6월 27일
{: #27-june-2018}

이제 6개의 새 언어를 제공하는 새로운 [번역 모델](/docs/services/language-translator?topic=language-translator-translation-models)을 사용할 수 있습니다.
  - 카탈로니아어
    - 카탈로니아어에서 스페인어로(ca-es)
    - 스페인어에서 카탈로니아어로(es-ca)
  -      체코어
    - 체코어에서 영어로(cs-en)
    - 영어에서 체코어로(en-cs)
  -      덴마크어
    - 덴마크어에서 영어로(da-en)
    - 영어에서 덴마크어로(en-da)
  -      핀란드어
    - 핀란드어에서 영어로(fi-en)
    - 영어에서 핀란드어로(en-fi)
  -      힌디어
    - 힌디어에서 영어로(hi-en)
    - 영어에서 힌디어로(en-hi)
  -      스웨덴어
    - 스웨덴어에서 영어로(sv-en)
    - 영어에서 스웨덴어로(en-sv)
  

## 2018년 6월 15일
{: #15-june-2018}

2018년 6월 15일 현재, 독일과 미국 남부 지역에서 작성한 새 서비스 인스턴스에서는 [IAM(Identity and Access Management) 인증](#iam-auth-process)을 사용합니다.

독일과 미국 남부에서 작성하는 새 서비스 인스턴스는 Language Translator v2와 호환 가능하지 않습니다. Language Translator v2를 사용하고 애플리케이션에서 새로운 서비스 인스턴스를 사용하려는 경우 [v3 API로 마이그레이션](/docs/services/language-translator?topic=language-translator-migrating)해야 합니다.

## 2018년 6월 12일
{: #12-june-2018}

이제 {{site.data.keyword.languagetranslatorshort}} v3을 사용할 수 있습니다. 2018년 7월 31일 이후로 v2 Language Translator API는 더 이상 사용할 수 없습니다. 최신 서비스 개선사항을 이용하려면 v3 API로 마이그레이션하십시오. 자세한 정보는 [Language Translator v3으로 마이그레이션](/docs/services/language-translator?topic=language-translator-migrating) 페이지를 보십시오.

### v3의 새로운 기능
{: #whats-new}

-  {{site.data.keyword.languagetranslatorshort}} API v3에는 상당히 개선된 번역 결과를 제공하는 NMT(**Neural Machine Translation**) 모델이 함께 제공됩니다. 이제 모든 NMT 모델을 사용자 정의할 수 있습니다.
-  강제 실행 용어집 사용자 정의용 기본 모델로 사용자 정의 모델을 사용합니다.
-  API v3은 폐기된 API v2의 간소화된 모든 JSON 서브세트입니다.
-  개발자가 자체 진도에 맞게 향후 API 변경사항을 자유롭게 도입할 수 있도록 API 버전 날짜를 소개합니다.

### 장애 유발 변경 사항(Breaking changes)
{: #breaking-changes}

- 모든 API 엔드포인트의 필수 버전 날짜: API v3 요청을 사용하려면 `version=YYYY-MM-DD` 양식의 버전 날짜 조회 매개변수가 필요합니다. 최신 API 버전은 `version=2018-05-01`입니다.
- 간소화된 API:
  - **번역** 및 **식별** 메소드에서는 v3의 일반 텍스트 응답을 리턴하는 옵션을 제공하지 않습니다. 이 메소드에서는 JSON 응답만 리턴합니다.
  - `GET /translate` 및 `GET /identify` 메소드는 v3에서 지원되지 않습니다. 대신 `POST /translate`와 `POST /identify` 메소드를 사용하십시오. 
- 단일 언어 말뭉치 사용자 정의는 v3에서 지원되지 않습니다.
- 병렬 말뭉치와 강제 실행 용어집을 모두 사용하여 사용자 정의 모델을 작성하려면 두 개의 API 호출을 통해 수행해야 합니다. 먼저 병렬 말뭉치로 모델을 사용자 정의하십시오. 사용자 정의 모델의 훈련을 완료하면 강제 실행 용어집으로 다시 사용자 정의하십시오. 이와 같이 변경하면 병렬 말뭉치로 훈련된 사용자 정의 모델을 강제 실행 용어집 사용자 정의의 기본으로 사용할 수 있습니다.
- 특수 특허 및 대화 도메인 모델은 v3 API에서 사용할 수 없습니다. 특허 및 대화 도메인의 NMT 모델에서 제공하는 번역 품질은 전문화된 이전 모델과 비교하여 일반적으로 개선되었습니다.
- 다른 Watson API와 일관되도록 오류 오브젝트 키의 이름이 변경되었습니다. `error_code`의 이름은 `code`로 변경되었으며 `error_message`의 이름은 `error`로 변경되었습니다.

### IAM 인증

2018년 6월 12일 현재, 시드니와 미국 동부 지역에서 작성한 새 서비스 인스턴스에서는 [IAM(Identity and Access Management) 인증](#iam-auth-process)을 사용합니다.

## 2018년 1월 12일
{: #12-january-2018}

새 NMT(Neural Machine Translation) 모델의 미리보기를 사용할 수 있습니다. 다음의 언어 쌍에 대해 NMT 모델을 사용해 볼 수 있습니다. 

- 영어(양방향): 아랍어, 중국어, 네덜란드어, 프랑스어, 독일어, 이탈리아어, 일본어, 한국어, 폴란드어, 포르투갈어(브라질), 러시아어, 스페인어 및 터키어
- 프랑스어(양방향): 독일어, 스페인어
- 독일어(양방향): 이탈리아어

*NMT 모델 및 이를 사용하기 위한 구문은 미리보기 기간 중에 변경될 수 있습니다. 현재 NMT 모델은 말뭉치 사용자 정의를 지원하지 않습니다. 오직 자동 설정된 용어집 사용자 정의만 지원됩니다. *

NMT 미리보기 모델을 사용하여 번역하려면 사용할 모델의 소스 및 대상 언어에 대한 문자 코드와 함께 `X-Watson-Technology-Preview:2017-07-01` 헤더를 지정하십시오. 다음 예제는 NMT 미리보기 모델에서 영어를 스페인어로 번역하는 방법을 표시합니다.

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}

NMT 미리보기를 통해 {{site.data.keyword.languagetranslatorshort}} 설정 방법을 설명하는 [유튜브의 단계별 안내 동영상![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://youtu.be/L6ZC0QaUZ2k)을 시청하십시오.


## 2016년 12월 15일
{: #15-december-2016}

뉴스 번역 모델이 더 추가됨: 영어와 일본어(양방향)

## 2016년 11월 15일
{: #15-november-2016}

{{site.data.keyword.languagetranslatorshort}} 서비스에 대해 이전에 사용 가능하던 도구가 더 이상 사용 가능하지 않거나 지원되지 않습니다. 

{{site.data.keyword.languagetranslatorshort}} API를 사용하여 {{site.data.keyword.languagetranslatorshort}} 도구에서 지원하는 태스크를 완료하는 방법에 대한 정보는 영업 담당자 또는 고객 지원 센터에 문의하십시오.

## 2016년 9월 1일
{: #1-september-2016}

IBM Watson&trade; Language Translation 서비스의 새 브랜드는 {{site.data.keyword.languagetranslatorshort}} 서비스입니다.

## 2016년 3월 22일
{: #22-march-2016}

언어에 대한 지원이 더 추가됨: 영어와 이탈리아어(양방향) 및 스페인어와 프랑스어(양방향).

## 2015년 12월 3일
{: #3-december-2015}

2016년 1월 15일 현재, 표준 플랜 내의 모든 사용자 정의 기능이 중단됩니다. 사용자 정의 또는 사용자 정의된 모델과 관련되지 않은 모든 API 호출에 대해 표준 플랜이 계속 사용되므로, 사용자 정의 기능을 사용하지 않는 애플리케이션은 변경이 필요하지 않습니다. 서비스의 이전 인스턴스를 사용하는 {{site.data.keyword.cloud}} 애플리케이션에서 {{site.data.keyword.languagetranslatorshort}} 서비스의 GA 사용자 정의 기능(훈련 가능 플랜)을 사용하려면 다음 단계를 완료하십시오.

1.  새 Watson {{site.data.keyword.languagetranslatorshort}} 인스턴스를 작성하고 GA "훈련 가능" 플랜을 지정하십시오.
2.  {{site.data.keyword.cloud_notm}}의 앱에 서비스의 새 "훈련 가능" 인스턴스를 바인드하십시오.
3.  처음에 사용자 정의된 모델을 작성하는 데 사용된 데이터를 수집하십시오. 자세한 정보는 [훈련 데이터의 구조](/docs/services/language-translator?topic=language-translator-customizing#structure)를 참조하십시오.
4.  훈련 데이터를 업로드하여 "훈련 가능" 인스턴스의 새 사용자 정의된 모델을 작성하십시오. 자세한 정보는 [사용자 정의 번역 모델 훈련](/docs/services/language-translator?topic=language-translator-customizing#training)을 참조하십시오.
5.  앱에서 "ModelID" 필드가 새 사용자 정의된 모델을 지시하도록 하십시오.
6.  {{site.data.keyword.cloud_notm}}에서 앱의 이전 서비스를 바인드 해제한 후에 이를 삭제하십시오.

## 2015년 11월 6일
{: #6-november-2015}

{{site.data.keyword.languagetranslatorshort}} 도구 베타가 릴리스되었습니다. 이 도구는 보다 정확한 기계 번역을 위해 모델을 관리하고 훈련하기 위한 그래픽 사용자 인터페이스를 제공하는 웹 애플리케이션입니다. 프로젝트 작성, 훈련 데이터 업로드, 사용자 정의 모델 훈련 및 텍스트 번역을 수행할 수 있습니다.

## 2014년 12월 1일
{: #1-december-2014}

베타 Machine Translator 및 베타 Language Identification API가 업그레이드되었으며 {{site.data.keyword.languagetranslatorshort}} API에 결합되었습니다. 새 서비스의 사용을 바로 시작하려면 코드를 파악하고 다음 변경사항을 반영하도록 업데이트하십시오.

- **새 model\_id 매개변수**: 베타 API에서는 번역에 사용할 모델을 선택하기 위한 `sid` 매개변수를 정의했습니다. 이 버전에서 `sid` 매개변수의 이름은 `model_id` 매개변수로 변경되었습니다. `model_id` 허용 값을 검색하려면 `GET/language  translator/api/v2/models` 조작을 사용하십시오. 이는 모든 모델 및 이에 대응되는 `model_id` 값의 목록을 리턴합니다.
- **언어 쌍 지원**: `model_id`를 선택하는 대신에 이제는 소스 및 대상 언어를 대신 지정할 수 있으며, 모델은 일반 뉴스 도메인에서 훈련된 대상을 기본값으로 사용합니다.
- **JSON 요청 본문 지원**: POST 번역 요청을 작성할 때 이제는 JSON 제출로서 요청을 작성할 수 있습니다. JSON 형식화를 사용하면 단지 양식 제출 형식의 단일 텍스트 부분이 아니라 번역을 위해 다중 단락을 제출할 수 있습니다.
- **JSON 응답 본문 지원**: 번역 요청 리턴은 일반 텍스트 형식화는 물론 JSON 형식화를 지원합니다. JSON 형식을 사용하면 번역된 단어가 단일 텍스트 부분이 아닌 다중 단락으로 리턴될 수 있도록 지원이 제공됩니다.
- **승인 헤더 지원**: 이제 승인 헤더를 사용하여 모든 조작에서 응답의 형식을 정의할 수 있습니다(text/plain 또는 application/json).
- **Language Identification 지원**: 언어 식별 메소드가 이 API에 추가되었습니다. 이를 사용하면 입력 텍스트의 언어를 식별할 수 있으며 API에서 감지할 수 있는 모든 지원 언어가 나열됩니다.

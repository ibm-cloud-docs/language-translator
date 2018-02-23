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

# 릴리스 정보

서비스에 대해 다음의 새 기능과 변경사항을 사용할 수 있습니다.
{: shortdesc}

## 2018년 1월 12일
{: #12-january-2018}

새 NMT(Neural Machine Translation) 모델의 미리보기를 사용할 수 있습니다. 다음의 언어 쌍에 대해 NMT 모델을 사용해 볼 수 있습니다.  

- 영어(양방향): 아랍어, 중국어, 네덜란드어, 프랑스어, 독일어, 이탈리아어, 일본어, 한국어, 폴란드어, 포르투갈어(브라질), 러시아어, 스페인어 및 터키어
- 프랑스어(양방향): 독일어, 스페인어
- 독일어(양방향): 이탈리아어

*NMT 모델 및 이를 사용하기 위한 구문은 미리보기 기간 중에 변경될 수 있습니다. 현재 NMT 모델은 말뭉치 사용자 정의를 지원하지 않습니다. 오직 자동 설정된 용어집 사용자 정의만 지원됩니다. *

NMT 미리보기 모델을 사용하여 변환하려면 사용할 모델의 소스 및 대상 언어에 대한 문자 코드와 함께 `X-Watson-Technology-Preview:2017-07-01` 헤더를 지정하십시오. 다음 예제는 NMT 미리보기 모델에서 영어를 스페인어로 변환하는 방법을 표시합니다. 

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}


## 2016년 12월 15일
{: #15-december-2016}

뉴스 변환 모델이 더 추가됨: 영어와 일본어(양방향)

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
1.  {{site.data.keyword.cloud_notm}}의 앱에 서비스의 새 "훈련 가능" 인스턴스를 바인드하십시오. 
1.  처음에 사용자 정의된 모델을 작성하는 데 사용된 데이터를 수집하십시오. 자세한 정보는 [훈련 데이터의 구조](/docs/services/language-translator/customizing.html#structure)를 참조하십시오. 
1.  훈련 데이터를 업로드하여 "훈련 가능" 인스턴스의 새 사용자 정의된 모델을 작성하십시오. 자세한 정보는 [사용자 정의 변환 모델 훈련](/docs/services/language-translator/customizing.html#training)을 참조하십시오. 
1.  앱에서 "ModelID" 필드가 새 사용자 정의된 모델을 지시하도록 하십시오. 
1.  {{site.data.keyword.cloud_notm}}에서 앱의 이전 서비스를 바인드 해제한 후에 이를 삭제하십시오. 

## 2015년 11월 6일 
{: #6-november-2015}

{{site.data.keyword.languagetranslatorshort}} 도구 베타가 릴리스되었습니다. 이 도구는 보다 정확한 기계 번역을 위해 모델을 관리하고 훈련하기 위한 그래픽 사용자 인터페이스를 제공하는 웹 애플리케이션입니다. 프로젝트 작성, 훈련 데이터 업로드, 사용자 정의 모델 훈련 및 텍스트 변환을 수행할 수 있습니다. 

## 2014년 12월 1일
{: #1-december-2014}

베타 Machine Translator 및 베타 Language Identification API가 업그레이드되었으며 {{site.data.keyword.languagetranslatorshort}} API에 결합되었습니다. 새 서비스의 사용을 바로 시작하려면 코드를 파악하고 다음 변경사항을 반영하도록 업데이트하십시오. 

- **새 model\_id 매개변수**: 베타 API에서는 변환에 사용할 모델을 선택하기 위한 `sid` 매개변수를 정의했습니다. 이 버전에서 `sid` 매개변수의 이름은 `model_id` 매개변수로 변경되었습니다. `model_id` 허용 값을 검색하려면 `GET/language  translator/api/v2/models` 조작을 사용하십시오. 이는 모든 모델 및 이에 대응되는 `model_id` 값의 목록을 리턴합니다. 
- **언어 쌍 지원**: `model_id`를 선택하는 대신에 이제는 소스 및 대상 언어를 대신 지정할 수 있으며, 모델은 일반 뉴스 도메인에서 훈련된 대상을 기본값으로 사용합니다. 
- **JSON 요청 본문 지원**: POST 변환 요청을 작성할 때 이제는 JSON 제출로서 요청을 작성할 수 있습니다. JSON 형식화를 사용하면 단지 양식 제출 형식의 단일 텍스트 부분이 아니라 변환을 위해 다중 단락을 제출할 수 있습니다. 
- **JSON 응답 본문 지원**: 변환 요청 리턴은 일반 텍스트 형식화는 물론 JSON 형식화를 지원합니다. JSON 형식을 사용하면 변환된 단어가 단일 텍스트 부분이 아닌 다중 단락으로 리턴될 수 있도록 지원이 제공됩니다. 
- **승인 헤더 지원**: 이제 승인 헤더를 사용하여 모든 조작에서 응답의 형식을 정의할 수 있습니다(text/plain 또는 application/json).
- **Language Identification 지원**: 언어 식별 메소드가 이 API에 추가되었습니다. 이를 사용하면 입력 텍스트의 언어를 식별할 수 있으며 API에서 감지할 수 있는 모든 지원 언어가 나열됩니다. 


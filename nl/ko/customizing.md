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

# 모델의 사용자 정의
{: #customizing}

고객 지원 팀에서 사용할 변환기를 작성 중이며 대화에 특정 방식으로 처리할 회사 특정 용어가 있습니까? 한 국가의 기술자가 다른 언어로 특허 데이터를 검색하는 방법을 작성 중이며 일반적으로 특정 기술 관련 특허를 파일링합니까? 자체 데이터를 사용하여 {{site.data.keyword.languagetranslatorshort}} API에서 사용자 정의 사전 및 사용자 정의 변환 모델을 작성할 수 있습니다.
{: shortdesc}

다음 방법으로 {{site.data.keyword.languagetranslatorshort}} 모델을 사용자 정의할 수 있습니다. 

- 소스 및 대상 언어의 일치 용어 또는 문구 쌍에 대해 서비스에 알려주십시오. 변환 서비스가 반드시 처리해야 할 완벽하고 최종적인 용어 쌍이 포함된 *자동 설정된 용어집*을 제공하십시오. 또는 변환 서비스가 고려해야 할 대체 변환 제안으로서 제공되는 용어 또는 문구 쌍이 포함된 *병렬 말뭉치*를 제공하십시오. 
- 서비스가 전체 변환 품질의 개선을 위해 평가하고 사용할 수 있는 언어 샘플로서 제공될 수 있도록 대상 언어의 대형 텍스트 본문(*단일어 말뭉치*라고 함)을 업로드하십시오. 

사용자 정의할 수 있는 모델의 목록을 보려면 `GET /v2/models` 메소드를 사용하고 각 언어 모델에 대한 응답에서 응답 매개변수 `customizable=true`를 찾으십시오. 

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

각각의 사용자 정의할 수 있는 모델은 서비스 인스턴스당 최대 10개의 사용자 정의를 저장할 수 있습니다. 

## 훈련 데이터의 구조
{: #structure}

{{site.data.keyword.languagetranslatorshort}} 서비스의 훈련을 위한 용어의 말뭉치 또는 용어집을 제공하려면 TMX(Translation Memory Exchange) [버전 1.4 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ttt.org/oscarstandards/tmx/tmx14.dtd){: new_window} 스펙을 준수하는 올바른 UTF-8 인코딩된 문서를 작성하십시오. TMX은 기계 번역 도구용으로 설계된 XML 스펙입니다. 다음 예제는 2개의 용어 및 변환 쌍이 있는 TMX 형식화된 용어집 파일입니다. 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>International Business Machines</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>International Business Machines</seg>
      </tuv>
    </tu>
    <tu>
      <tuv xml:lang="en">
        <seg>patent</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>brevet</seg>
      </tuv>
    </tu>
  </body>
</tmx>
```
{: codeblock}

각각의 용어 및 변환 쌍은 `<tu>` 태그 안에 있어야 합니다. 

```xml
<tu>
  <tuv xml:lang="en">
    <seg>International Business Machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

`xml:lang` 속성(`<tuv>` 태그의)은 용어가 표현되는 언어를 식별하며, `<seg>` 태그에는 용어 또는 변환이 포함되어 있습니다. 

{{site.data.keyword.languagetranslatorshort}} 서비스는 `<tu>`, `<tuv>` 및 `<seg>` 요소만 사용합니다. 예제의 기타 모든 요소는 올바른 TMX 파일의 작성에 필요하거나 정보용으로 제공되지만, 서비스는 이를 사용하지 않습니다. 

이전 예제는 'patent'와 같은 기술 용어의 변환을 정확하게 표준화하는 방법과 'International Business Machines'와 같은 회사 이름의 변환을 사용자 정의하는 방법을 보여줍니다. 표준 모델에서 'International Business Machines'는 'Machines Commerciales Internationales'로 변환될 수 있지만, 회사 이름이므로 이는 실제로 변환되지 않아야 합니다. 

## 예제를 템플리트로서 사용

제공된 예제를 자체 용어집 또는 말뭉치에 대한 템플리트로서 사용하려면 다음 단계를 완료하십시오. 

1.  예제를 복사하여 텍스트 편집기에 붙여넣으십시오. 

1.  `srclang` 속성(`<header>` 태그의)을 용어집 또는 병렬 말뭉치가 사용하는 소스 언어의 [언어 코드 ![코드 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}로 변경하십시오. 

1.  `xml:lang` 속성(`<tuv>` 태그의)을 각각의 용어 또는 변환에 대한 올바른 [언어 코드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}로 변경하십시오. 

    {{site.data.keyword.languagetranslatorshort}} 서비스는 ISO 639-3 코드를 사용하는 이집트 아랍어를 제외한 모든 언어에 대해 ISO 639-1 언어 코드를 사용합니다. 

1.  UTF-8 인코딩 및 `.tmx` 확장자의 문서를 저장하십시오. 

### TMX 파일을 UTF-8 인코딩으로 변경

다수의 도구를 사용하여 TMX 파일을 작성하거나 생성할 수 있습니다. 종종 생성된 TMX 파일은 기본적으로 UTF-16 인코딩되어 있습니다. {{site.data.keyword.languagetranslatorshort}} 서비스는 UTF-8 인코딩된 TMX 파일만 허용합니다. TMX 파일의 인코딩을 변경하려면 다음 단계를 완료하십시오. 

1.  텍스트 편집기에서 TMX 파일을 여십시오. 

1.  XML 헤더(존재하는 경우)를 `<?xml ... encoding="utf-16"?>`에서 다음으로 변경하십시오. `<?xml ... encoding="utf-8"?>`.

1.  새 이름으로 및 UTF-8 인코딩 출력으로 파일을 저장하십시오. 

Mac 사용자는 2단계에서 설명한 대로 문서의 XML 헤더를 업데이트한 후에 터미널에서 다음 명령을 실행하여 파일 인코딩을 변경할 수도 있습니다. 

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}

## 사용자 정의 변환 모델 훈련
{: #training}

`POST /v2/models` 메소드를 사용하여 TMX 파일을 업로드하고 변환 모델을 훈련할 수 있습니다. 사용자 정의 모델을 훈련하려면 다음의 파일 옵션 중 최소한 하나를 지정하십시오. 

- `forced_glossary`: 시스템이 완벽하다고 보는 소스 및 대상 언어의 일치 용어 쌍이 포함된 UTF-8 인코딩된 TMX 파일입니다. 이 파일은 원래 도메인 데이터를 완전히 겹쳐씁니다. 

    자동 설정된 용어집은 10MB의 파일 크기로 제한됩니다. 현재는 변환 모델당 하나의 자동 설정된 용어집 파일만 업로드할 수 있습니다. 
    
- `parallel_corpus`: Watson용 예제로서 제공되는 소스 및 대상 언어의 일치 구문이 포함된 UTF-8 인코딩된 TMX 파일입니다. 원래 도메인 데이터를 겹쳐쓰지 않으므로, 병렬 말뭉치는 자동 설정된 용어집과는 다릅니다. 

    사용자 정의 모델을 성공적으로 훈련하려면 병렬 말뭉치 문서에 최소한 5,000개의 용어 및 변환 쌍이 포함되어야 합니다. 
    
- `monolingual_corpus`: 변환 중인 내용과 관련된 대상 언어의 텍스트 본문이 포함된 UTF-8 인코딩된 일반 텍스트 파일입니다. 단일어 말뭉치를 제공하면 변환이 보다 유연하고 자연스러워지므로 문자 그대로의 변환(즉, 직역)이 개선됩니다. 

    사용자 정의 모델을 성공적으로 훈련하려면 단일어 말뭉치 문서에 최소한 1,000개의 문장이 포함되어야 합니다. 

모든 업로드된 용어집 및 말뭉치 파일의 누적 파일 크기는 250MB로 제한됩니다. 업로드된 파일의 크기에 따라 훈련에 수 분(용어집의 경우)에서 수 시간(대형 말뭉치의 경우)이 소요될 수 있습니다. 

다음의 curl 예제는 `forced_glossary` 파일 옵션을 사용합니다. 
1. [훈련 데이터의 구조](#structure) 섹션에서 TMX 파일 샘플 다운로드
1. 프랑스어 뉴스 도메인(en-fr)을 기본 모델로서 사용하십시오. TMX 파일에 지정된 모든 항목이 원래 도메인 데이터를 완전히 겹쳐씁니다. 

    {{site.data.keyword.languagetranslatorshort}} 서비스가 지원하는 모든 모델 도메인을 검색하려면 `GET v2/models` 메소드를 사용하십시오. 

```curl
curl -u "{username}":"{password}" -X POST -F base_model_id=en-fr -F name="test_glossary" -F forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

`POST /v2/models` 메소드는 `200` 코드와 새 `model_id`로 응답합니다. 새로 사용자 정의된 이 모델로 텍스트를 변환하는 경우에는 `model_id`를 사용하십시오. 

## 훈련 모니터링

TMX 훈련 파일의 크기는 `POST /v2/models` 요청의 훈련 시간에 영향을 줍니다. 훈련의 진행상태 및 훈련의 성공적 완료 여부를 모니터하려면 `GET /v2/models/<model_id>` 메소드를 사용하고 응답에서 `status` 매개변수의 값을 확인하십시오. 

이 예제 명령은 모델에 대한 정보를 제공하며 [변환 모델 훈련](#training) 섹션에서 시작된 훈련의 상태를 확인합니다. 이 명령은 비어 있는 본문 요청을 사용합니다. 

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}

`STATUS` 응답 매개변수는 훈련 프로세스의 모델 상태를 설명합니다. 

- `uploading`
- `uploaded`
- `dispatching`
- `queued@<#>`
- `training`
- `trained`
- `publishing`
- `available`

모델 상태가 `available`인 경우에는 모델이 서비스 인스턴스에서 사용 준비가 된 것입니다. 모델이 삭제되었거나 훈련 프로세스에서 오류가 발생한 경우에는 다음 오류 중 하나가 나타날 수 있습니다. 

- `deleted`
- `error`

## 사용자 정의 변환 모델 사용

사용자 정의 변환 모델을 훈련한 후에는 `POST /v2/translate` 또는 `GET /v2/translate` 메소드에서 이를 사용할 수 있도록 해당 변환 모델의 model\_id를 지정하십시오. 

다음 예제는 [사용자 정의 변환 모델 훈련](#training) 섹션에서 사용자 정의된 영어-프랑스어 모델을 호출합니다. 

```curl
curl -u "{username}":"{password}" --header "Content-Type: application/json" -X POST --data "{\"model_id\": \"3e7dfdbe-f757-4150-afee-458e71eb93fb\",\"text\": \"Hello, my name is Watson, and I work for International Business Machines. How can I help you today?\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate 
```
{: codeblock}

{{site.data.keyword.languagetranslatorshort}} 서비스는 IBM에서 개발한 표준은 물론 BLEU(Bilingual Evaluation Understudy) 표준을 사용하여 변환 품질을 평가합니다. 결과는 언어 쌍, 사용된 토착어(방언) 또는 사용자 데이터의 도메인에 따라 다양할 수 있습니다. 

## 사용자 정의 변환 모델 삭제

변환 모델을 더 이상 사용할 수 없게 되면 이를 삭제하고자 할 수 있습니다. 변환 모델을 삭제하려면 `DELETE /v2/models/<model_id>` 메소드를 사용하십시오. 모든 변환 모델의 모델 ID를 검색하려면 사용자 정의 또는 기본 여부와 무관하게 `GET /v2/models` 메소드를 사용하십시오. 

다음 명령은 이러한 예제에서 작성된 변환 모델을 삭제합니다. 

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}


---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-13"

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

{{site.data.keyword.languagetranslatorshort}}에 제공된 대부분의 번역 모델은 번역 데이터에서 파생된 일반 스타일이나 사용자 정의 용어 및 구문까지 확장할 수 있습니다. 이 지시사항을 따라 고유 사용자 정의 번역 모델을 작성하십시오.
{: shortdesc}

## 시작하기 전에
{: #before-you-begin}

1. {{site.data.keyword.languagetranslatorshort}} 서비스 인스턴스의 가격 플랜이 Advanced인지 아니면 Premium인지 확인하십시오. Lite와 Standard 플랜에서는 사용자 정의를 지원하지 않습니다.
1. 언어 쌍에 맞는 사용자 정의 가능한 기본 모델을 찾으십시오. 사용자 정의 모델을 훈련하려면 기본 모델의 모델 ID가 필요합니다.
    - [번역 모델](/docs/services/language-translator?topic=language-translator-translation-models) 페이지에 나열된 모델을 검색하십시오. **사용자 정의 가능** 열에서 "**true**" 값을 찾고 모델의 **소스** 및 **대상** 언어가 언어 쌍과 일치하는지 확인하십시오.
    - 또는 [모델 나열 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/apidocs/language-translator#list-models) API 메소드를 사용하여 프로그래밍 방식으로 모델을 검색할 수 있습니다. `source` 및 `target` 매개변수를 사용하여 언어별로 결과를 필터링할 수 있습니다.

## 1단계: 훈련 데이터 작성
{: #create-your-training-data}

이 서비스를 사용하려면 [TMX(Translation Memory Exchange) 파일 형식](#creating-tmx-files)으로 학습 데이터를 제공해야 합니다. 서비스 인스턴스에 언어 쌍당 최대 10개의 사용자 정의를 저장할 수 있습니다. 이 서비스에서는 두 가지 유형의 사용자 정의 요청을 지원합니다. 병렬 문장을 포함하는 말뭉치 또는 강제 실행 설정 용어집을 사용하여 모델을 사용자 정의할 수 있습니다.

- [강제 실행 용어집](#forced-glossary-customization)을 사용하여 특정 용어와 문구를 특정 방식으로 번역하십시오.
- 사용자 정의 모델을 사용하여 샘플의 일반 번역 패턴을 통해 학습하려면 [병렬 말뭉치](#parallel-corpus-customization)를 사용하십시오. 모델이 병렬 말뭉치에서 배우는 내용을 통해 모델이 훈련되지 않은 입력 텍스트의 번역 결과를 향상시킬 수 있습니다.

[TMX(Translation Memory Exchange) 파일](#creating-tmx-files)을 작성하고 나면 모델을 훈련할 준비가 됩니다.

## 2단계: 모델 훈련
{: #train-your-model}

[모델 작성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/apidocs/language-translator#create-model) 메소드를 사용하여 모델을 훈련하십시오. 요청에서 사용자 정의할 수 있는 기본 모델의 모델 ID와 훈련 데이터를 `forced_glossary` 또는 `parallel_corpus` 매개변수로 지정하십시오.

### 예제 요청
{: #train-model-example-request}

다음 예제 요청에서는 강제 실행 용어집 파일, _glossary.tmx_를 사용하여 `en-es` 기본 모델을 사용자 정의할 수 있습니다. 예제 강제 실행 용어집 TMX 파일은 [강제 실행 용어집 사용자 정의](#forced-glossary) 절을 참조하십시오.

```bash
curl --user apikey:{apikey} -X POST --form forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

API 응답에는 모델 ID를 포함하여 사용자 정의 모델에 관한 세부사항이 들어 있습니다. 모델 ID를 사용하여 모델의 상태를 확인하고 모델의 상태가 "사용 가능"이 되면 문장을 번역하십시오.

```json
{
  "model_id": "96221b69-8e46-42e4-a3c1-808e17c787ca",
  "source": "en",
  "target": "es",
  "base_model_id": "en-es",
  "domain": "general",
  "customizable": false,
  "default_model": false,
  "owner": "4937aab7-0f3a-4a75-bee1-0b7a12b6b8",
  "status": "uploaded",
  "name": "custom-english-to-spanish",
  "train_log": null
}
```
{: codeblock}

## 3단계: 모델의 상태 확인
{: #check-model-status}

모델 훈련은 사용되는 훈련 데이터 양에 따라 몇 분(강제 실행 용어집)에서 몇 시간(대규모 병렬 말뭉치)이 걸릴 수 있습니다. 모델을 사용할 수 있는지 확인하려면 [모델 가져오기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/apidocs/language-translator#get-model-details) 메소드를 사용하고 2단계에서 서비스 응답으로 받은 모델 ID를 지정하십시오. 또한 [모델 나열 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/apidocs/language-translator#list-models) 메소드를 사용하여 모든 모델의 상태를 확인할 수 있습니다.

`status` 응답 속성을 통해서는 훈련 프로세스의 모델 상태를 설명합니다.

- `uploading`
- `uploaded`
- `dispatching`
- `queued`
- `training`
- `trained`
- `publishing`
- `available`

모델 상태가 `available`인 경우에는 모델이 서비스 인스턴스에서 사용 준비가 된 것입니다. 모델이 삭제되었거나 훈련 프로세스에서 오류가 발생한 경우에는 다음 상태 중 하나가 표시될 수 있습니다. 

- `deleted`
- `error`

### 예제 요청
{: #check-model-example-request}

다음 예제에서는 모델 ID `96221b69-8e46-42e4-a3c1-808e17c787ca`로 식별된 모델의 정보를 가져옵니다.

```bash
curl --user apikey:{apikey_value} "https://gateway.watsonplatform.net/language-translator/api/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## 4단계: 사용자 정의 모델로 텍스트 번역
{: #translate-text}

사용자 정의 모델을 사용하려면 [번역 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/apidocs/language-translator#translate) 메소드로 번역할 텍스트와 사용자 정의 모델의 모델 ID를 지정하십시오.

### 예제 요청
{: #translate-text-example-request}

다음 예제에서는 모델 ID `96221b69-8e46-42e4-a3c1-808e17c787ca`로 식별된 사용자 정의 모델로 텍스트를 번역합니다.

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data '{"text":"Hello","model_id":"96221b69-8e46-42e4-a3c1-808e17c787ca"}' https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}


## 강제 실행 용어집 사용자 정의
{: #forced-glossary-customization}

**강제 실행 용어집**을 사용하여 특정 용어와 문구의 필수 번역을 설정하십시오. 번역 동작을 고유하게 제어하려면 강제 실행 용어집을 사용하십시오.

- 훈련 데이터 형식: [TMX](#creating-tmx-files)(UTF-8 인코딩)
- 최대 파일 크기: 10MB
- 기본 모델 또는 병렬 말뭉치로 사용자 정의된 모델에 강제 실행 용어집 적용 가능
- 모델당 하나의 강제 실행 용어집으로 제한

강제 실행 용어집 예제는 대소문자를 구분하므로, 훈련 데이터가 애플리케이션에 나타나는 컨텐츠의 대소문자를 반영합니다.
{: tip}

### 강제 실행 용어집 예제
{: #forced-glossary-example}

다음 예에서는 두 개의 번역 쌍이 있는 TMX 파일을 보여줍니다. 첫 번째 쌍에서는 번역하는 동안 "international business machines"를 영어로 유지하도록 강제 실행합니다. 이 유형의 강제 실행 번역은 비공식적인 의사소통에서 대소문자가 잘못 지정된 회사 이름을 유지하려는 경우 유용할 수 있습니다. 두 번째 쌍에서는 "patent"를 번역할 때 모델이 항상 "brevet"을 사용하도록 강제 실행합니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="phrase" o-tmf="" adminlang="en"
    srclang="en" datatype="PlainText" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
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



## 병렬 말뭉치 사용자 정의
{: #parallel-corpus-customization}

**병렬 말뭉치**를 사용하여 훈련의 소스가 될 기본 모델을 위해 추가 번역을 제공하십시오. 그러면 기본 모델을 특정 도메인에 맞게 조정할 수 있습니다. 결과적으로 생성된 사용자 정의 모델에서 텍스트를 번역하는 방식은 모델에서 병렬 말뭉치와 기본 모델을 결합하여 이해한 내용에 따라 달라집니다.

- 훈련 데이터 형식: [TMX](#creating-tmx-files)(UTF-8 인코딩)
- 번역된 쌍의 최대 길이: 80개의 소스 단어
- 최소 번역 쌍 수: 5,000개
- 최대 파일 크기: 250MB
- 파일의 누적 크기가 250MB를 초과하지 않는 범위에서 `parallel_corpus` 다중 파트 양식 매개변수를 반복하여 여러 병렬 말뭉치 파일을 제출할 수 있습니다.

### 병렬 말뭉치 예제
{: #parallel-corpus-example}

다음은 OPUS 개방형 병렬 말뭉치 웹 사이트에서 사용 가능한 [MultiUN 콜렉션 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://opus.nlpl.eu/MultiUN.php)에서 다운로드한 영어에서 프랑스어로 번역된 작은 병렬 말뭉치입니다. 전체 TMX 파일의 압축된 버전을 [여기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz)에서 다운로드할 수 있습니다.


```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
<header creationdate="Tue Jan 29 12:49:40 2013"
          srclang="en"
          adminlang="en"
          o-tmf="unknown"
          segtype="sentence"
          creationtool="Uplug"
          creationtoolversion="unknown"
          datatype="PlainText" />
  <body>
    <tu>
      <tuv xml:lang="en"><seg>RESOLUTION 55/100</seg></tuv>
      <tuv xml:lang="fr"><seg>RÉSOLUTION 55/100</seg></tuv>
    </tu>
    <tu>
      <tuv xml:lang="en"><seg>Adopted at the 81st plenary meeting, on 4 December 2000, on the recommendation of the Committee (A/55/602/Add.2 and Corr.1, para. 94),The draft resolution recommended in the report was sponsored in the Committee by: Bolivia, Cuba, El Salvador, Ghana and Honduras. by a recorded vote of 106 to 1, with 67 abstentions, as follows:</seg></tuv>
      <tuv xml:lang="fr"><seg>Adoptée à la 81e séance plénière, le 4 décembre 2000, sur la recommandation de la Commission (A/55/602/Add.2, par. 94)Le projet de résolution recommandé dans le rapport de la Commission avait pour auteurs les pays suivants: Bolivie, Cuba, El Salvador, Ghana et Honduras., par 106 voix contre une, avec 67 abstentions, à la suite d'un vote enregistré, les voix s'étant réparties comme suit:</seg></tuv>
    </tu>
    ...
```
{: codeblock}

일반적으로 병렬 말뭉치 사용자 정의는 강제 실행 용어집 사용자 정의에서 얻을 수 있는 필수 결과에 비해 예측하기가 어렵게 개선되었습니다. 예를 들어, 예제 병렬 말뭉치(172-175행)의 다음 번역 단위를 고려해 보겠습니다.

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

"55/102. Globalization and its impact on the full enjoyment of all human rights"를 기본 `en-fr` 모델로 번역하면 서비스에서 다음과 같은 번역으로 응답합니다.

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

예제 말뭉치로 훈련된 사용자 정의 모델을 사용하여 동일한 입력 문장을 번역하면 서비스에서 훈련 데이터에 제공된 샘플 번역과 같지 않은 다른 번역으로 응답합니다.

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- 사용자 정의 모델에서는 "the full enjoyment"를 "la pleine jouissance"가 아니라 "le plein exercice"로 번역합니다. 이와 같이 기본 모델 동작과 다르게 번역되는 이유는 말뭉치에서 "enjoyment"가 "exercice"로 번역되는 예제가 많기 때문일 가능성이 큽니다.
- 사용자 정의 모델에서는 "of all human rights"를 번역 단위의 결과인  "des droits de l'homme"를 복제하지 않고 "de tous les droits de l'homme"로 번역합니다. 이 동작은 훈련된 모델에서 병렬 말뭉치에 있는 "of all human rights"와 관련된 모든 번역 샘플과 기본 모델을 결합하여 파악한 결과로 나타납니다.

경우에 따라 병렬 말뭉치로 훈련된 사용자 정의 모델에서 사용자가 제공하는 특정 예제를 무시하는 것으로 보일 수 있습니다. 이 경우 훈련 데이터에서 번역 동작에 영향을 줄 수 있는 다른 문장을 검색해 보십시오. 아니면 특정 번역을 제어하려는 경우 강제 실행 용어집을 사용해 보십시오.


## TMX 파일 작성
{: #creating-tmx-files}

{{site.data.keyword.languagetranslatorshort}} 서비스의 훈련을 위한 용어의 말뭉치 또는 용어집을 제공하려면 TMX(Translation Memory Exchange) [버전 1.4 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ttt.org/oscarStandards/tmx/){: new_window} 스펙을 준수하는 올바른 UTF-8 인코딩된 문서를 작성하십시오. TMX은 기계 번역 도구용으로 설계된 XML 스펙입니다. 다음 예제는 두 개의 번역 단위(`<tu>` 요소)가 있는 TMX 형식 용어집 파일입니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
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

각 용어와 번역 쌍은 `<tu>` 태그로 묶어야 합니다.

```xml
<tu>
  <tuv xml:lang="en">
    <seg>international business machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

`<tuv>` 태그의 `xml:lang` 속성은 용어를 표현하는 언어를 나타내며 `<seg>` 태그에는 용어나 번역이 포함되어 있습니다.

{{site.data.keyword.languagetranslatorshort}} 서비스에서는 `<tu>`, `<tuv>` 및 `<seg>` 요소만 사용합니다. 예제의 기타 모든 요소는 올바른 TMX 파일의 작성에 필요하거나 정보용으로 제공되지만, 서비스는 이를 사용하지 않습니다.



### 예제를 템플리트로서 사용
{: #using-the-example-template}

제공된 예제를 자체 용어집 또는 말뭉치에 대한 템플리트로서 사용하려면 다음 단계를 완료하십시오.

1. 예제를 복사하여 텍스트 편집기에 붙여넣으십시오.

2. `srclang` 속성(`<header>` 태그의)을 용어집 또는 병렬 말뭉치가 사용하는 소스 언어의 [언어 코드 ![코드 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}로 변경하십시오.

3. `<tuv>` 태그의 `xml:lang` 속성을 용어 또는 번역에 올바른 [언어 코드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}로 변경하십시오.

4. UTF-8 인코딩 및 `.tmx` 확장자의 문서를 저장하십시오.

### TMX 파일을 UTF-8 인코딩으로 변경
{: #changing-tmx-file-to-utf-8}

다수의 도구를 사용하여 TMX 파일을 작성하거나 생성할 수 있습니다. 종종 생성된 TMX 파일은 기본적으로 UTF-16 인코딩되어 있습니다. {{site.data.keyword.languagetranslatorshort}} 서비스는 UTF-8 인코딩된 TMX 파일만 허용합니다. TMX 파일의 인코딩을 변경하려면 다음 단계를 완료하십시오.

1. 텍스트 편집기에서 TMX 파일을 여십시오.

1. XML 헤더(있는 경우)를 `<?xml ... encoding="utf-16"?>`에서 `<?xml ... encoding="utf-8"?>`로 변경하십시오.

1. 새 이름으로 및 UTF-8 인코딩 출력으로 파일을 저장하십시오.

Mac 사용자는 2단계에서 설명한 대로 문서의 XML 헤더를 업데이트한 후에 터미널에서 다음 명령을 실행하여 파일 인코딩을 변경할 수도 있습니다.

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}


## 사용자 정의 번역 모델 삭제
{: #deleting-a-custom-model}

사용자 정의 번역 모델을 삭제하려면 [모델 삭제 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com/apidocs/language-translator#delete-model) 메소드를 사용하십시오.

다음 명령을 실행하면 모델 ID가 `3e7dfdbe-f757-4150-afee-458e71eb93fb`인 번역 모델을 삭제합니다.

```curl
curl --user apikey:{apikey_value} --request DELETE "https://gateway.watsonplatform.net/language-translator/api/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: codeblock}

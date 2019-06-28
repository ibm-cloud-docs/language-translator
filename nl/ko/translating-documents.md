---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

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

# 문서 번역(베타)
{: #document-translator-tutorial}


원래 형식을 유지하면서 파일을 한 언어에서 다른 언어로 번역하십시오. MS Office, Open Office 및 PDF를 포함하여 12개가 넘는 여러 다른 파일 형식을 번역할 수 있습니다.
{:shortdesc}

## 시작하기 전에
{: #prerequisites}

- {{site.data.keyword.languagetranslatorshort}} [시작하기](/docs/services/language-translator?topic=language-translator-getting-started)를 수행하십시오. {{site.data.keyword.languagetranslatorshort}} 서비스 인증 정보(`apikey` 및 `url`)가 필요합니다.
- 번역하려는 문서가 다음 요구사항을 만족하는지 확인하십시오.
    - 최대 파일 크기: **20MB**
    - [지원되는 파일 형식](#supported-file-formats)
    - [지원되는 번역 모델](/docs/services/language-translator?topic=language-translator-translation-models)

## 1단계: 번역할 문서 제출
{: #submit-document-to-translate}

다음 예제 요청에서는 예제 파일 *curriculum.pdf*를 서비스에 제출하고 영어에서 프랑스어로 번역합니다. `{apikey}`와 `{url}`을 서비스 인증 정보로 바꾸고 `curriculum.pdf`를 파일의 상대 경로로 바꾸십시오.

예제 요청:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

[사용자 정의 모델](/docs/services/language-translator?topic=language-translator-customizing)로 문서를 번역하려면 **model_id** 매개변수를 사용하십시오. 다음 예제에서는 모델 ID `96221b69-8e46-42e4-a3c1-808e17c787ca`로 식별된 사용자 정의 모델로 문서를 번역합니다.

예제 요청:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
{url}/v3/documents?version=2018-05-01
```
{: pre}


요청에 성공하면 응답으로 `document_id`를 리턴합니다.


예제 응답:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "processing",
  "created": "2018-10-11T03:31:25"
}
```
{: codeblock}

## 2단계: 번역 상태 확인
{: #check-translation-status}

번역할 문서를 제출한 다음 번역 상태를 확인하여 번역된 문서를 다운로드할 수 있게 되는 시기를 알아보십시오. 다음 예제 요청에서는 문서 ID가 `bae02796-0d28-435c-9115-888359fdde62`인 문서의 번역 상태를 확인합니다. 

예제 요청:
```bash
curl -X GET \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

예제 응답:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "available",
  "created": "2018-10-11T03:31:25",
  "completed": "2018-10-11T03:31:38"
}
```
{: codeblock}

응답의 `status`가 `available`이면 번역된 문서를 다운로드할 준비가 된 것입니다.

## 3단계: 번역된 문서 다운로드
{: #download-translated-document}

다음 예제 요청에서는 문서 ID가 `bae02796-0d28-435c-9115-888359fdde62`인 번역된 문서를 *curriculum-fr.pdf*에 저장합니다. 

예제 요청:
```bash
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01
```
{: pre}

## 4단계: 이전에 제출한 문서 번역
{: #translate-document-by-reference}

다음 예제 요청에서는 `document_id`가 `bae02796-0d28-435c-9115-888359fdde62`인 원본 영어 *curriculum.pdf* 파일을 참조하여 포르투갈어로 번역합니다.

예제 요청:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

예제 응답:
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

응답에는 새 `document_id`가 포함되어 있습니다. 새로운 `document_id`로 2단계와 3단계를 반복하여 번역 상태를 확인하고 번역된 파일이 사용 가능하게 되면 다운로드하십시오.

## 5단계: 문서 삭제
{: #delete-documents}

원본 문서 및 연관돈 모든 번역 문서는 특정 기간 동안 사용하지 않으면 자동으로 삭제됩니다. 자세한 정보는 [정보 보안](/docs/services/language-translator?topic=language-translator-information-security)을 참조하십시오.
{: tip}

수동으로 문서를 삭제하려면 **문서 삭제 ** 메소드를 사용하십시오. 이 튜토리얼에서 영어 *curriculum.pdf* 파일에는 두 개의 번역이 관련되어 있으므로, 원본 문서의 사본을 모두 삭제하려면 두 개의 요청이 필요합니다.

제출된 원본 *curriculum.pdf*와 프랑스어 번역을 삭제하십시오.
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

원본 *curriculum.pdf* 파일의 복제본과 포르투갈어 번역을 삭제하십시오.
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01
```
{: pre}

## 지원되는 파일 형식
{: #supported-file-formats}

-  Microsoft Office
    - Word: `.doc`, `.docx`
    - PowerPoint: `.ppt`, `.pptx`
    - Excel: `.xls`, `.xlsx`
    - Rich Text Format: `.rtf`
- Open Office
    - Writer: `.odt`
    - Impress: `.odp`
    - Calc: `.ods`
- 기타 형식
    - PDF: `.pdf`
    - HTML: `.htm`, `.html`
    - XML: `.xml`
    - JSON: `.json`(`string` 또는 `string array` 유형의 값이 번역됨)
    - 텍스트: `.txt`

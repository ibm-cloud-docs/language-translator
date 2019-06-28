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

# 翻譯文件（測試版）
{: #document-translator-tutorial}


將檔案從某種語言翻譯為另一種語言的同時保留原始格式。可以翻譯超過 12 種不同的檔案格式，包括 MS Office、Open Office 及 PDF。
{:shortdesc}

## 開始之前
{: #prerequisites}

- [開始使用](/docs/services/language-translator?topic=language-translator-getting-started) {{site.data.keyword.languagetranslatorshort}}。您將需要 {{site.data.keyword.languagetranslatorshort}} 服務認證（`apikey` 和 `url`）。
- 確定您想要翻譯的文件符合下列需求：
    - 檔案大小上限：**20 MB**
    - [受支援檔案格式](#supported-file-formats)
    - [受支援翻譯模型](/docs/services/language-translator?topic=language-translator-translation-models)

## 步驟 1：提交要翻譯的文件
{: #submit-document-to-translate}

下列範例要求會將範例檔案 *curriculum.pdf* 提交給服務，並將它從英文翻譯為法文。將 `{apikey}` 和 `{url}` 取代為您的服務認證，並將 `curriculum.pdf` 取代為您檔案的相對路徑。

範例要求：
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

若要使用[自訂模型](/docs/services/language-translator?topic=language-translator-customizing)來翻譯文件，請使用 **model_id** 參數。下列要求會使用模型 ID `96221b69-8e46-42e4-a3c1-808e17c787ca` 所識別的自訂模型來翻譯文件。

範例要求：
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
{url}/v3/documents?version=2018-05-01
```
{: pre}


成功要求將在回應中傳回 `document_id`。


範例回應：
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

## 步驟 2：檢查翻譯狀態
{: #check-translation-status}

在已提交文件進行翻譯之後，您可以檢查翻譯狀態，以瞭解何時可以下載已翻譯的文件。下列範例要求會檢查文件 ID 為 `bae02796-0d28-435c-9115-888359fdde62` 之文件的翻譯狀態。 

範例要求：
```bash
curl -X GET \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

範例回應：
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

當回應中的 `status` 為 `available` 時，已翻譯文件即準備好可供下載。

## 步驟 3：下載已翻譯文件
{: #download-translated-document}

下列範例要求會將文件 ID 為 `bae02796-0d28-435c-9115-888359fdde62` 的已翻譯文件儲存至 *curriculum-fr.pdf* 檔案。 

範例要求：
```bash
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01
```
{: pre}

## 步驟 4：翻譯先前提交的文件
{: #translate-document-by-reference}

下列範例要求會參照 `document_id` 為 `bae02796-0d28-435c-9115-888359fdde62` 的原始英文 *curriculum.pdf* 檔案，並將它翻譯為葡萄牙文。

範例要求：
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

範例回應：
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

回應包含新的 `document_id`。請使用新的 `document_id` 重複步驟 2 和 3，來檢查翻譯的狀態，並在已翻譯檔案可用時，立即下載該檔案。

## 步驟 5：刪除文件
{: #delete-documents}

在特定一段時間未使用原始文件及任何關聯的已翻譯文件之後，自動將其刪除。如需詳細資料，請參閱[資訊安全](/docs/services/language-translator?topic=language-translator-information-security)。
{: tip}

若要手動刪除文件，請使用**刪除文件**方法。在本指導教學中，英文 *curriculum.pdf* 檔案隨附兩個翻譯，因此需要兩個要求，才能刪除原始文件的所有副本。

刪除原始提交的 *curriculum.pdf* 和法文翻譯：
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

刪除複製的原始 *curriculum.pdf* 檔案和葡萄牙文翻譯：
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01
```
{: pre}

## 受支援檔案格式
{: #supported-file-formats}

-  Microsoft Office
    - Word：`.doc`、`.docx`
    - PowerPoint：`.ppt`、`.pptx`
    - Excel：`.xls`、`.xlsx`
    - Rich Text 格式：`.rtf`
- Open Office
    - Writer：`.odt`
    - Impress：`.odp`
    - Calc：`.ods`
- 其他格式
    - PDF：`.pdf`
    - HTML：`.htm`、`.html`
    - XML：`.xml`
    - JSON：`.json`（翻譯類型為 `string` 或 `string array` 的值）
    - Text：`.txt`

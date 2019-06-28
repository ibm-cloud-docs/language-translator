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

# 翻译文档 (Beta)
{: #document-translator-tutorial}


将文件从一种语言翻译成另一种语言，同时保留原始格式。可以翻译 12 种不同文件格式，包括 MS Office、Open Office 和 PDF。
{:shortdesc}

## 开始之前
{: #prerequisites}

- [开始使用](/docs/services/language-translator?topic=language-translator-getting-started) {{site.data.keyword.languagetranslatorshort}}。您将需要 {{site.data.keyword.languagetranslatorshort}} 服务凭证（`apikey` 和 `url`）。
- 确保要翻译的文档满足以下需求：
    - 最大文件大小：**20 MB**
    - [支持的文件格式](#supported-file-formats)
    - [支持的翻译模型](/docs/services/language-translator?topic=language-translator-translation-models)

## 步骤 1：提交要翻译的文档
{: #submit-document-to-translate}

以下示例请求将示例文件 *curriculum.pdf* 提交给服务，并将其从英语翻译成法语。将 `{apikey}` 和 `{url}` 替换为您的服务凭证，将 `curriculum.pdf` 替换为您文件的相对路径。

示例请求：
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

要使用[定制模型](/docs/services/language-translator?topic=language-translator-customizing)来翻译文档，请使用 **model_id** 参数。以下请求使用模型标识 `96221b69-8e46-42e4-a3c1-808e17c787ca` 所标识的定制模型来翻译文档。

示例请求：
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
{url}/v3/documents?version=2018-05-01
```
{: pre}


成功的请求将在响应中返回 `document_id`。


示例响应：
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

## 步骤 2：检查翻译状态
{: #check-translation-status}

提交文档进行翻译后，可以检查翻译状态，以了解已翻译的文档何时可供下载。以下示例请求检查文档标识为 `bae02796-0d28-435c-9115-888359fdde62` 的文档的翻译状态。 

示例请求：
```bash
curl -X GET \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

示例响应：
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

当响应中的 `status` 为 `availavaily` 时，说明已翻译的文档可随时下载。

## 步骤 3：下载已翻译的文档
{: #download-translated-document}

以下示例请求将文档标识为 `bae02796-0d28-435c-9115-888359fdde62` 的已翻译文档保存为 *curriculum-fr.pdf* 文件。 

示例请求：
```bash
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01
```
{: pre}

## 步骤 4：翻译先前提交的文档
{: #translate-document-by-reference}

以下示例请求引用 `document_id` 为 `bae02796-0d28-435c-9115-888359fdde62` 的原始英语 *curriculum.pdf* 文件，并将其翻译成葡萄牙语。

示例请求：
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

示例响应：
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

响应包含新的 `document_id`。对新的 `document_id` 重复步骤 2 和 3 以检查翻译的状态，并在已翻译文件可用后下载该文件。

## 步骤 5：删除文档
{: #delete-documents}

原始文档和任何关联的已翻译文档在一段特定时间内未使用后会被自动删除。有关更多详细信息，请参阅[信息安全](/docs/services/language-translator?topic=language-translator-information-security)。
{: tip}

要手动删除文档，请使用**删除文档**方法。在本教程中，英语 *curriculum.pdf* 文件参与了两个翻译，因此需要两个请求来删除原始文档的所有副本。

删除原始提交的 *curriculum.pdf* 和法语翻译：
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

删除原始 *curriculum.pdf* 文件的副本和葡萄牙语翻译：
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01
```
{: pre}

## 受支持文件格式
{: #supported-file-formats}

-  Microsoft Office
    - Word：`.doc` 和 `.docx`
    - PowerPoint：`.ppt` 和 `.pptx`
    - Excel：`.xls` 和 `.xlsx`
    - 富文本格式：`.rtf`
- Open Office
    - Writer：`.odt`
    - Impress：`.odp`
    - Calc：`.ods`
- 其他格式
    - PDF：`.pdf`
    - HTML：`.htm` 和 `.html`
    - XML：`.xml`
    - JSON：`.json`（将翻译类型为 `string` 或 `string array` 的值）
    - 文本：`.txt`

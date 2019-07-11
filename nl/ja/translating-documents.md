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

# 文書の翻訳 (ベータ)
{: #document-translator-tutorial}


元の形式を維持しながら、ファイルを 1 つの言語から他の言語に翻訳します。MS Office、Open Office、PDF など、12 を超えるさまざまなファイル・フォーマットを翻訳することができます。
{:shortdesc}

## 始めに
{: #prerequisites}

- {{site.data.keyword.languagetranslatorshort}} の使用を[開始](/docs/services/language-translator?topic=language-translator-getting-started)します。{{site.data.keyword.languagetranslatorshort}} サービス資格情報 (`apikey` と `url`) が必要です。
- 翻訳する文書が以下の要件を満たすことを確認してください。
    - 最大ファイル・サイズ: **20 MB**
    - [サポートされるファイル・フォーマット](#supported-file-formats)
    - [サポートされる翻訳モデル](/docs/services/language-translator?topic=language-translator-translation-models)

## ステップ 1: 翻訳する文書を送信する
{: #submit-document-to-translate}

以下の要求例では、サンプル・ファイル *curriculum.pdf* をサービスに送信し、それを英語からフランス語に翻訳します。`{apikey}` と `{url}` を実際のサービス資格情報に置き換え、`curriculum.pdf` をファイルの相対パスに置き換えてください。

要求例:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

[カスタム・モデル](/docs/services/language-translator?topic=language-translator-customizing)を使用して文書を翻訳するには、**model_id** パラメーターを使用します。以下の要求は、モデル ID `96221b69-8e46-42e4-a3c1-808e17c787ca` で識別されるカスタム・モデルを使用して文書を翻訳します。

要求例:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
{url}/v3/documents?version=2018-05-01
```
{: pre}


要求が成功すると、応答で `document_id` が返されます。


応答の例:
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

## ステップ 2: 翻訳状況を確認する
{: #check-translation-status}

翻訳用に文書を送信した後、翻訳状況を確認すると、翻訳済み文書がダウンロード可能になったことを知ることができます。以下の要求例では、文書 ID `bae02796-0d28-435c-9115-888359fdde62` の文書の翻訳状況を確認します。 

要求例:
```bash
curl -X GET \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

応答の例:
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

応答内の `status` が `available` である場合は、翻訳済み文書をダウンロードできます。

## ステップ 3: 翻訳済み文書をダウンロードする
{: #download-translated-document}

以下の要求例は、文書 ID `bae02796-0d28-435c-9115-888359fdde62` の翻訳済み文書をファイル *curriculum-fr.pdf* に保存します。 

要求例:
```bash
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01
```
{: pre}

## ステップ 4: 以前に送信した文書を翻訳する
{: #translate-document-by-reference}

以下の要求例は、`document_id` が `bae02796-0d28-435c-9115-888359fdde62` である元の英語の *curriculum.pdf* ファイルを参照し、それをポルトガル語に翻訳します。

要求例:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

応答の例:
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

応答には新しい `document_id` が含まれています。新しい `document_id` を使用してステップ 2 と 3 を繰り返して、翻訳の状況を確認し、翻訳済みファイルが使用可能になったらダウンロードします。

## ステップ 5: ドキュメントを削除する
{: #delete-documents}

元の文書および関連する翻訳済み文書は、一定期間使用されない場合、自動的に削除されます。詳しくは、[機密保護](/docs/services/language-translator?topic=language-translator-information-security)を参照してください。
{: tip}

文書を手動で削除するには、**「文書の削除 (Delete document)」**メソッドを使用します。このチュートリアルでは、英語の *curriculum.pdf* ファイルが 2 つの翻訳に関連しているので、元の文書のすべてのコピーを削除するには 2 つの要求が必要です。

次のようにして、*curriculum.pdf* の元の送信とフランス語の翻訳を削除します。
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

以下のようにして、元の *curriculum.pdf* ファイルの複製とポルトガル語の翻訳を削除します。
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01
```
{: pre}

## サポートされるファイル・フォーマット
{: #supported-file-formats}

-  Microsoft Office
    - Word: `.doc`、`.docx`
    - PowerPoint: `.ppt`、`.pptx`
    - Excel: `.xls`、`.xlsx`
    - RTF (リッチ・テキスト・フォーマット): `.rtf`
- Open Office
    - Writer: `.odt`
    - Impress: `.odp`
    - Calc: `.ods`
- その他のフォーマット
    - PDF: `.pdf`
    - HTML: `.htm`、`.html`
    - XML: `.xml`
    - JSON: `.json` (`string` または `string array` タイプの値が翻訳されます)
    - テキスト: `.txt`

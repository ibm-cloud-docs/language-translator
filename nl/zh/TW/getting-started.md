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

# 入門指導教學
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} 可讓您以程式設計方式將文字從某種語言翻譯為另一種語言。
{:shortdesc}
{: hide-dashboard}

本指導教學透過指令逐步引導您將文字從英文翻譯為西班牙文，以及識別文字範例的語言。

## 開始之前
{: #prerequisites}

- {: hide-dashboard}建立服務的實例：
    1.  {: hide-dashboard}移至「{{site.data.keyword.Bluemix_notm}} 型錄」中的 [{{site.data.keyword.languagetranslatorshort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/catalog/services/language-translator){: new_window} 頁面。
    2.  註冊免費的 {{site.data.keyword.Bluemix_notm}} 帳戶，或者登入。
    3.  按一下**建立**。
- 複製認證以對您的服務實例進行鑑別：
    1.  在**管理**頁面上，按一下**顯示**以檢視您的認證。
    2.  複製 `API 金鑰`及 `URL` 值。
- 確定您有 `curl` 指令：
    - 這些範例會使用 `curl` 指令來呼叫 HTTP 介面的方法。請從 [curl.haxx.se ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://curl.haxx.se/){: new_window} 安裝您的作業系統適用的版本。請安裝支援 Secure Sockets Layer (SSL) 通訊協定的版本。請務必在 `PATH` 環境變數中併入已安裝的二進位檔。

本指導教學使用 API 金鑰來進行鑑別。若為正式作業用途，請務必檢閱 API 金鑰的[最佳作法](/docs/services/watson/apikey-bp.html#api-bp)。
{: tip}

## 步驟 1：翻譯文字
{: #translate-text}

請使用下列範例，將兩個詞組 "Hello, world!" 和 "How are you?" 從英文翻譯為西班牙文。<span class="hide-dashboard">將 `{apikey}` 及 `{url}` 取代為服務認證。</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## 步驟 2：識別語言
{: #identify-language}

請使用下列範例來識別文字的語言。<span class="hide-dashboard">將 `{apikey}` 及 `{url}` 取代為服務認證。</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## 後續步驟
{: #next-steps}

- 學習如何[自訂](/docs/services/language-translator?topic=language-translator-customizing) {{site.data.keyword.languagetranslatorshort}}，為您的使用案例工作
- 嘗試[翻譯文件（測試版）](/docs/services/language-translator?topic=language-translator-document-translator-tutorial)
- 檢視 [API 參考資料](https://{DomainName}/apidocs/language-translator)
- 探索[範例應用程式](/docs/services/language-translator?topic=language-translator-sample-applications)
- 檢視支援語言資訊：
    - [翻譯模型](/docs/services/language-translator?topic=language-translator-translation-models)
    - [可識別語言](/docs/services/language-translator?topic=language-translator-identifiable-languages)

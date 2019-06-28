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

# 入門チュートリアル
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} を使用して、テキストを 1 つの言語から他の言語へプログラマチックに翻訳することができます。
{:shortdesc}
{: hide-dashboard}

このチュートリアルでは、テキストを英語からスペイン語に翻訳するコマンドと、テキスト・サンプルの言語を識別するコマンドについて説明します。

## 始めに
{: #prerequisites}

- {: hide-dashboard} サービスのインスタンスを作成します。
    1.  {: hide-dashboard} {{site.data.keyword.Bluemix_notm}} カタログの [{{site.data.keyword.languagetranslatorshort}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/services/language-translator){: new_window} ページに移動します。
    2.  無料の {{site.data.keyword.Bluemix_notm}} アカウントを登録するか、ログインします。
    3.  **「作成」**をクリックします。
- サービス・インスタンスに認証されるための資格情報をコピーします。
    1.  **「管理」**ページで、 **「表示」**をクリックして資格情報を表示します。
    2.  `「API キー」`の値と`「URL」`の値をコピーします。
- `curl` コマンドを使用できることを確認します。
    - 例では `curl` コマンドを使用して HTTP インターフェースのメソッドを呼び出します。 [curl.haxx.se ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://curl.haxx.se/){: new_window} から、ご使用のオペレーティング・システムに対応したバージョンをインストールします。 Secure Sockets Layer (SSL) プロトコルをサポートするバージョンをインストールしてください。 必ず、インストールしたバイナリー・ファイルを `PATH` 環境変数に含めてください。

このチュートリアルでは、API 鍵を使用して認証します。 実動で使用する場合には、必ず API 鍵の[ベスト・プラクティス](/docs/services/watson/apikey-bp.html#api-bp)を確認してください。
{: tip}

## 手順 1: テキストの翻訳
{: #translate-text}

以下の例を使用して、「Hello, world!」と「How are you?」の 2 つの句を英語からスペイン語に翻訳します。<span class="hide-dashboard">`{apikey}` と `{url}` はご使用のサービス資格情報に置き換えてください。</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## 手順 2: 言語の識別
{: #identify-language}

以下の例を使用して、テキストの言語を識別します。<span class="hide-dashboard">`{apikey}` と `{url}` はご使用のサービス資格情報に置き換えてください。</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## 次の手順
{: #next-steps}

- 実際のユース・ケースに合わせて、{{site.data.keyword.languagetranslatorshort}} を[カスタマイズ](/docs/services/language-translator?topic=language-translator-customizing)する方法を学ぶ
- [文書を翻訳 (ベータ)](/docs/services/language-translator?topic=language-translator-document-translator-tutorial) してみる
- [API リファレンス](https://{DomainName}/apidocs/language-translator)を参照する
- [サンプル・アプリケーション](/docs/services/language-translator?topic=language-translator-sample-applications)を探索する
- 言語サポート情報を参照する。
    - [翻訳モデル](/docs/services/language-translator?topic=language-translator-translation-models)
    - [識別可能な言語](/docs/services/language-translator?topic=language-translator-identifiable-languages)

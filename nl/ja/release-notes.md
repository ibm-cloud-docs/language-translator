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

# リリース・ノート

本サービスには以下の新機能と変更が導入されました。
{: shortdesc}

## 2018 年 1 月 12 日
{: #12-january-2018}

新しいニューラル機械翻訳 (New Neural Machine Translation: NMT) モデルのプレビュー版を使用できます。以下の言語ペアで NMT モデルを試すことができます。 

- 英語と次の言語 (双方向): アラビア語、中国語、オランダ語、フランス語、ドイツ語、イタリア語、日本語、韓国語、ポーランド語、ポルトガル語 (ブラジル)、ロシア語、スペイン語、トルコ語
- フランス語と次の言語 (双方向): ドイツ語、スペイン語
- ドイツ語と次の言語 (双方向): イタリア語

*NMT モデルとこのモデルの使用構文は、プレビュー期間中に変更される可能性があります。現時点では、NMT モデルはコーパスのカスタマイズをサポートしていません。強制グロッサリーのカスタマイズのみをサポートしています。*

NMT プレビュー・モデルを使用して翻訳するには、ヘッダー `X-Watson-Technology-Preview:2017-07-01` と、使用するモデルのソース言語とターゲット言語の文字コードを指定します。次の例は、NMT プレビュー・モデルを使用して英語をスペイン語に翻訳する方法を示しています。

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}


## 2016 年 12 月 15 日
{: #15-december-2016}

ニュース翻訳モデルとして、英語 - 日本語 (双方向) が追加されました。

## 2016 年 11 月 15 日
{: #15-november-2016}

{{site.data.keyword.languagetranslatorshort}} サービスでこれまで提供されていたツールがなくなり、サポートも廃止されました。 

{{site.data.keyword.languagetranslatorshort}} ツールでサポートされていた作業を {{site.data.keyword.languagetranslatorshort}} API を使用して行う方法については、営業担当員またはお客様サポートにお問い合わせください。

## 2016 年 9 月 1 日
{: #1-september-2016}

IBM Watson&trade; Language Translation サービスのブランドが変更され、{{site.data.keyword.languagetranslatorshort}} サービスになりました。

## 2016 年 3 月 22 日
{: #22-march-2016}

言語のサポートとして、英語 - イタリア語 (双方向) と、スペイン語 - フランス語 (双方向) が追加されました。

## 2015 年 12 月 3 日
{: #3-december-2015}

2016 年 1 月 15 日の時点で、標準プランに含まれるカスタマイズ機能はすべて廃止されました。カスタマイズやカスタマイズ・モデルに無関係の API 呼び出しでは標準プランは有効なままですので、カスタマイズ機能を使用しないアプリケーションを変更する必要はありません。以前のサービス・インスタンスを使用する {{site.data.keyword.cloud}} アプリケーションで {{site.data.keyword.languagetranslatorshort}} サービスの GA カスタマイズ機能 (トレーニング可能なプラン) を使用するには、以下の手順に従ってください。

1.  Watson {{site.data.keyword.languagetranslatorshort}} インスタンスを新規作成し、GA の「トレーニング可能」なプランを指定します。
1.  この新しい「トレーニング可能」なサービス・インスタンスを {{site.data.keyword.cloud_notm}} 内のアプリにバインドします。
1.  カスタマイズ・モデルを最初に作成したときに使用したデータを集めます。詳しくは、[トレーニング・データの構造](/docs/services/language-translator/customizing.html#structure)を参照してください。
1.  トレーニング・データをアップロードして、「トレーニング可能な」インスタンスに新しいカスタマイズ・モデルを作成します。詳しくは、[カスタム翻訳モデルをトレーニングする](/docs/services/language-translator/customizing.html#training)を参照してください。
1.  アプリ内で、この新しいカスタマイズ・モデルを「ModelID」フィールドに指定します。
1.  {{site.data.keyword.cloud_notm}} 内のアプリから以前のサービスをアンバインドし、削除します。

## 2015 年 11 月 6 日
{: #6-november-2015}

{{site.data.keyword.languagetranslatorshort}} ツールのベータ版がリリースされました。このツールは、より正確な機械翻訳を実現するためにモデルの管理とトレーニングを行うグラフィカル・ユーザー・インターフェースを備えた Web アプリケーションです。プロジェクトの作成、トレーニング・データのアップロード、カスタム・モデルのトレーニング、テキストの翻訳を行えます。

## 2014 年 12 月 1 日
{: #1-december-2014}

ベータ版 Machine Translator API とベータ版 Language Identification API がアップグレードされて、{{site.data.keyword.languagetranslatorshort}} API にまとめられました。新しいサービスをすぐに使い始めるには、以下の変更点を理解したうえで、コードを更新して変更点を反映させてください。

- **新しい model\_id パラメーター**: ベータ版 API では、翻訳に使用するモデルを選択するために、`sid` パラメーターを定義していました。このバージョンでは、`sid` パラメーターの名前が `model_id` パラメーターに変更されました。使用できる `model_id` 値を検索するには、`GET/language  translator/api/v2/models` 操作を使用します。この操作により、すべてのモデルとそれらの対応する `model_id` 値のリストが返されます。
- **言語ペアのサポート**: `model_id` を選択する代わりに、ソース言語とターゲット言語を指定できるようになりました。指定すると、汎用ニュース・ドメインでトレーニングされたモデルが、デフォルトのモデルとして設定されます。
- **JSON 要求本文のサポート**: POST で翻訳を要求するときに、JSON 送信として要求できるようになりました。JSON 形式を使用することで、テキスト 1 文ではなく複数の段落をフォーム送信形式で送信して翻訳できます。
- **JSON 応答本文のサポート**: 翻訳要求に対する応答で、プレーン・テキスト形式だけでなく、サポート JSON 形式もサポートされます。JSON 形式によって、テキスト 1 文ではなく複数の段落を訳文として返すことができます。
- **受け入れヘッダーのサポート**: すべての操作で、受け入れヘッダーを使用して応答形式 (text/plain または application/json) を定義できるようになりました。
- **Language Identification のサポート**: この API に言語識別メソッドが追加されました。これにより、入力テキストの言語を識別し、API で検出できるサポート対象言語をすべてリストすることができます。


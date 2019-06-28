---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-14"

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

## 新しい API 認証プロセス
{: #iam-auth-process }

{{site.data.keyword.languagetranslatorshort}} サービスは、次のロケーションでホストされるサービス・インスタンスの API 認証プロセスを刷新しました。

- ダラス (2018 年 6 月 15 日)
- フランクフルト (2018 年 6 月 15 日)
- ロンドン
- シドニー (2018 年 6 月 12 日)
- 東京
- ワシントン DC (2018 年 6 月 12 日)

{{site.data.keyword.cloud_notm}} は、トークン・ベースの ID およびアクセス管理 (IAM) 認証へのマイグレーションを進めています。 一部のサービス・インスタンスでは、API に対する認証で IAM を使用します。

- 前に示したロケーションで作成された_新しい_サービス・インスタンスの場合は、認証に IAM を使用します。ベアラー・トークンを渡すか、または API キーを渡すことができます。 トークンを使用すれば、認証済み要求がサポートされるので、呼び出すたびにサービス資格情報を埋め込む必要がありません。 API キーは基本認証を使用します。

    Watson SDK を使用する場合は、API キーを渡して、SDK にトークンのライフサイクルを管理させることができます。 詳細情報と例については、API リファレンスの[認証![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/apidocs/language-translator#authentication){: new_window} を参照してください。
- 記載した日付より前に作成した_既存の_サービス・インスタンスでは、引き続きサービス・インスタンスのユーザー名とパスワードを渡して認証できます。 最終的には、これらのサービス・インスタンスは IAM 認証にマイグレーションする必要があります。 マイグレーションのプロセスと日付に関する新たな情報が提供される予定です。 マイグレーションの詳細については、[リソース・グループへの Cloud Foundry サービス・インスタンスのマイグレーション](/docs/resources?topic=resources-migrate#migrate)を参照してください。

どの認証を使用するかを調べるには、[{{site.data.keyword.cloud_notm}} リソース・ページ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/resources){: new_window} でサービス・インスタンスをクリックしてサービス資格情報を参照します。

## サービス API のバージョン管理
{: shortdesc}

{{site.data.keyword.languagetranslatorshort}} v3 の API 要求では、`version=YYYY-MM-DD` という形式で日付を設定した version パラメーターが必要です。後方互換性のない方法で API を変更する場合、API の新規マイナー・バージョンをリリースします。

API 要求のたびに version パラメーターを送信してください。 サービスでは、指定された日付の API バージョン、またはその日付より前の最新のバージョンが使用されます。 現在日付をデフォルトに設定しないでください。 代わりに、アプリと互換性のあるバージョンに一致する日付を指定して、アプリがより新しいバージョン用に準備ができるまで日付を変更しないでください。

現行のバージョンは `2018-05-01` です。

## 2019 年 6 月 14 日
{: #14-june-2019}

英語とギリシャ語の新しい[翻訳モデル](/docs/services/language-translator?topic=language-translator-translation-models)が使用可能になりました。
- 英語からギリシャ語 (en-el)
- ギリシャ語から英語 (el-en)

## 2019 年 6 月 13 日
{: #13-june-2019}

英語とヘブライ語の新しい[翻訳モデル](/docs/services/language-translator?topic=language-translator-translation-models)が使用可能になりました。
- 英語からヘブライ語 (en-he)
- ヘブライ語から英語 (he-en)

## 2019 年 3 月 21 日
{: #21-march-2019}

2019 年 3 月 21 日から、ご自分の {{site.data.keyword.cloud_notm}} アカウントに割り当てられた役割に関連付けられたサービス資格情報のみが表示されるようになりました。例えば、`reader` 役割を割り当てた場合、`writer` 以上のレベルのサービス資格情報は表示されません。

この変更は、既存のサービス・キー資格情報を使用しているユーザーやアプリケーションの API アクセスに影響を与えません。影響を受けるのは、{{site.data.keyword.cloud_notm}} 内の資格情報の表示のみです。

サービス鍵とユーザー役割について詳しくは、[IAM のサービス API 鍵](/docs/services/watson?topic=watson-api-key-bp#api-key-bp)を参照してください。

## 2018 年 12 月 14 日
{: #14-december-2018}

- {{site.data.keyword.cloud_notm}} のロンドン・ロケーションで {{site.data.keyword.languagetranslatorshort}} サービス・インスタンスを作成できるようになりました。

## 2018 年 11 月 16 日
{: #16-november-2018}

- [文書の翻訳 (ベータ)](/docs/services/language-translator?topic=language-translator-translating-documents) が、新規 API エンドポイントを通じて利用可能になりました。Microsoft Office 文書、PDF、または他のサポートされるファイル形式の文書を送信すると、{{site.data.keyword.languagetranslatorshort}} によって、元の形式を維持した翻訳済みコピーが提供されます。
  - [サポートされるファイル形式](/docs/services/language-translator?topic=language-translator-translating-documents#supported-file-types)は、`.doc`、`.ppt`、`.pdf` などです。

- ハンガリー語の新しい[翻訳モデル](/docs/services/language-translator?topic=language-translator-translation-models)が使用可能になりました。
  - ハンガリー語から英語 (hu-en)
  - 英語からハンガリー語 (en-hu)

## 2018 年 11 月 8 日
{: #8-november-2018}

- {{site.data.keyword.cloud_notm}} の東京ロケーションで {{site.data.keyword.languagetranslatorshort}} サービス・インスタンスを作成できるようになりました。

## 2018 年 8 月 9 日
{: #9-august-2018}

ノルウェー語ブークモールの新しい[翻訳モデル](/docs/services/language-translator?topic=language-translator-translation-models)が使用可能になりました。
  - ノルウェー語ブークモールから英語 (nb-en)
  - 英語からノルウェー語ブークモール (en-nb)

## 2018 年 6 月 27 日
{: #27-june-2018}

以下の 6 言語をフィーチャーした新しい[翻訳モデル](/docs/services/language-translator?topic=language-translator-translation-models)が使用可能になりました。
  - カタロニア語
    - カタロニア語からスペイン語 (ca-es)
    - スペイン語からカタロニア語 (es-ca)
  - チェコ語
    - チェコ語から英語 (cs-en)
    - 英語からチェコ語 (en-cs)
  - デンマーク語
    - デンマーク語から英語 (da-en)
    - 英語からデンマーク語 (en-da)
  - フィンランド語
    - フィンランド語から英語 (fi-en)
    - 英語からフィンランド語 (en-fi)
  - ヒンディ語
    - ヒンディ語から英語 (hi-en)
    - 英語からヒンディ語 (en-hi)
  - スウェーデン語
    - スウェーデン語から英語 (sv-en)
    - 英語からスウェーデン語 (en-sv)
  

## 2018 年 6 月 15 日
{: #15-june-2018}

2018 年 6 月 15 日より、ドイツと米国南部地域で作成される新しいサービス・インスタンスは [ID およびアクセス管理 (IAM) 認証](#iam-auth-process)を使用します。

ドイツおよび米国南部で作成した新規サービス・インスタンスは、Language Translator v2 との互換性がなくなります。Language Translator v2 を現在使用していて、アプリケーションで新規サービス・インスタンスを使用する予定の場合は、[v3 API にマイグレーション](/docs/services/language-translator?topic=language-translator-migrating)する必要があります。

## 2018 年 6 月 12 日
{: #12-june-2018}

{{site.data.keyword.languagetranslatorshort}} v3 が使用可能になりました。v2 Language Translator API は、2018 年 7 月 31 日以降は使用できなくなります。最新のサービス機能強化を利用するには、v3 API にマイグレーションしてください。詳しくは、[Language Translator v3 へのマイグレーション](/docs/services/language-translator?topic=language-translator-migrating)のページを参照してください。

### v3 の新機能
{: #whats-new}

-  {{site.data.keyword.languagetranslatorshort}} API v3 には、大幅に改善された翻訳結果を提供する**ニューラル機械翻訳** (NMT) モデルが付属しています。すべての NMT モデルをカスタマイズできるようになりました。
-  強制グロッサリーのカスタマイズには、基本モデルとしてカスタム・モデルを使用します。
-  API v3 は、廃止された API v2 の、簡素化された全 JSON サブセットです。
-  API バージョン日付を導入し、開発者は今後の API 変更を自身のペースで自由に採用できます。

### 重要な変更点
{: #breaking-changes}

- すべての API エンドポイントのバージョン日付 (必須): API v3 要求では、`version=YYYY-MM-DD` という形式のバージョン日付照会パラメーターが必要です。最新の API バージョンは `version=2018-05-01` です。
- 簡素化された API:
  - v3 では、**「翻訳」**メソッドおよび**「識別 (Identify)」**メソッドに、プレーン・テキスト応答を返すオプションがありません。これらのメソッドは JSON 応答のみを返します。
  - `GET /translate` メソッドおよび `GET /identify` メソッドは v3 ではサポートされていません。代わりに `POST /translate` メソッドおよび `POST /identify` メソッドを使用してください。 
- 単一言語コーパスのカスタマイズは、v3 ではサポートされていません。
- 並列コーパスおよび強制グロッサリーの両方でカスタム・モデルを作成するには、2 つの API 呼び出しが必要になりました。最初に、並列コーパスでモデルをカスタマイズします。カスタム・モデルのトレーニングが完了した後、それを強制グロッサリーで再度カスタマイズします。この変更点により、強制グロッサリーのカスタマイズのベースとして、並列コーパスでトレーニングしたカスタム・モデルを使用できます。
- 特許および会話のための特殊なドメイン・モデルは、v3 API では使用できません。特許ドメインと会話ドメインで NMT モデルが提供する翻訳品質は、以前の特殊モデルと比較すると概して改善されています。
- エラー・オブジェクト・キーの名前が、他の Watson API と整合するように変更されました。`error_code` は `code` に、`error_message` は `error` に名前変更されました。

### IAM 認証

2018 年 6 月 12 日より、シドニー地域および米国東部地域で作成される新しいサービス・インスタンスは [ID およびアクセス管理 (IAM) 認証](#iam-auth-process)を使用します。

## 2018 年 1 月 12 日
{: #12-january-2018}

新しいニューラル機械翻訳 (New Neural Machine Translation: NMT) モデルのプレビュー版を使用できます。 以下の言語ペアで NMT モデルを試すことができます。 

- 英語と次の言語 (双方向): アラビア語、中国語、オランダ語、フランス語、ドイツ語、イタリア語、日本語、韓国語、ポーランド語、ポルトガル語 (ブラジル)、ロシア語、スペイン語、トルコ語
- フランス語と次の言語 (双方向): ドイツ語、スペイン語
- ドイツ語と次の言語 (双方向): イタリア語

*NMT モデルとこのモデルの使用構文は、プレビュー期間中に変更される可能性があります。 現時点では、NMT モデルはコーパスのカスタマイズをサポートしていません。 強制グロッサリーのカスタマイズのみをサポートしています。*

NMT プレビュー・モデルを使用して翻訳するには、ヘッダー `X-Watson-Technology-Preview:2017-07-01` と、使用するモデルのソース言語とターゲット言語の文字コードを指定します。 次の例は、NMT プレビュー・モデルを使用して英語をスペイン語に翻訳する方法を示しています。

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}

NMT プレビューを使用して {{site.data.keyword.languagetranslatorshort}} をセットアップする方法を説明する [YouTube の動画ウォークスルー ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://youtu.be/L6ZC0QaUZ2k) を見ることができます。


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

2016 年 1 月 15 日の時点で、標準プランに含まれるカスタマイズ機能はすべて廃止されました。 カスタマイズやカスタマイズ・モデルに無関係の API 呼び出しでは標準プランは有効なままですので、カスタマイズ機能を使用しないアプリケーションを変更する必要はありません。 以前のサービス・インスタンスを使用する {{site.data.keyword.cloud}} アプリケーションで {{site.data.keyword.languagetranslatorshort}} サービスの GA カスタマイズ機能 (トレーニング可能なプラン) を使用するには、以下の手順に従ってください。

1.  Watson {{site.data.keyword.languagetranslatorshort}} インスタンスを新規作成し、GA の「トレーニング可能」なプランを指定します。
2.  この新しい「トレーニング可能」なサービス・インスタンスを {{site.data.keyword.cloud_notm}} 内のアプリにバインドします。
3.  カスタマイズ・モデルを最初に作成したときに使用したデータを集めます。 詳しくは、[トレーニング・データの構造](/docs/services/language-translator?topic=language-translator-customizing#structure)を参照してください。
4.  トレーニング・データをアップロードして、「トレーニング可能な」インスタンスに新しいカスタマイズ・モデルを作成します。 詳しくは、[カスタム翻訳モデルをトレーニングする](/docs/services/language-translator?topic=language-translator-customizing#training)を参照してください。
5.  アプリ内で、この新しいカスタマイズ・モデルを「ModelID」フィールドに指定します。
6.  {{site.data.keyword.cloud_notm}} 内のアプリから以前のサービスをアンバインドし、削除します。

## 2015 年 11 月 6 日
{: #6-november-2015}

{{site.data.keyword.languagetranslatorshort}} ツールのベータ版がリリースされました。 このツールは、より正確な機械翻訳を実現するためにモデルの管理とトレーニングを行うグラフィカル・ユーザー・インターフェースを備えた Web アプリケーションです。 プロジェクトの作成、トレーニング・データのアップロード、カスタム・モデルのトレーニング、テキストの翻訳を行えます。

## 2014 年 12 月 1 日
{: #1-december-2014}

ベータ版 Machine Translator API とベータ版 Language Identification API がアップグレードされて、{{site.data.keyword.languagetranslatorshort}} API にまとめられました。 新しいサービスをすぐに使い始めるには、以下の変更点を理解したうえで、コードを更新して変更点を反映させてください。

- **新しい model\_id パラメーター**: ベータ版 API では、翻訳に使用するモデルを選択するために、`sid` パラメーターを定義していました。 このバージョンでは、`sid` パラメーターの名前が `model_id` パラメーターに変更されました。 使用できる `model_id` 値を検索するには、`GET/language  translator/api/v2/models` 操作を使用します。 この操作により、すべてのモデルとそれらの対応する `model_id` 値のリストが返されます。
- **言語ペアのサポート**: `model_id` を選択する代わりに、ソース言語とターゲット言語を指定できるようになりました。指定すると、汎用ニュース・ドメインでトレーニングされたモデルが、デフォルトのモデルとして設定されます。
- **JSON 要求本文のサポート**: POST で翻訳を要求するときに、JSON 送信として要求できるようになりました。 JSON 形式を使用することで、テキスト 1 文ではなく複数の段落をフォーム送信形式で送信して翻訳できます。
- **JSON 応答本文のサポート**: 翻訳要求に対する応答で、プレーン・テキスト形式だけでなく、サポート JSON 形式もサポートされます。 JSON 形式によって、テキスト 1 文ではなく複数の段落を訳文として返すことができます。
- **受け入れヘッダーのサポート**: すべての操作で、受け入れヘッダーを使用して応答形式 (text/plain または application/json) を定義できるようになりました。
- **Language Identification のサポート**: この API に言語識別メソッドが追加されました。 これにより、入力テキストの言語を識別し、API で検出できるサポート対象言語をすべてリストすることができます。

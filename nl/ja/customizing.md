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

# モデルのカスタマイズ
{: #customizing}

お客様サポートで使用する翻訳プログラムを作成していて、会話の中で会社固有の用語を特定の方法で扱わなければならない。エンジニアのために外国語の特許データを検索する仕組みを作っていて、通常は、特定の技術に関する特許を出願している。そのような場合は、独自のデータを使用して、{{site.data.keyword.languagetranslatorshort}} API でカスタム辞書とカスタム翻訳モデルを作成してください。
{: shortdesc}

{{site.data.keyword.languagetranslatorshort}} モデルは、以下の方法でカスタマイズできます。

- 用語またはフレーズのソース言語とターゲット言語のペアをサービスに学習させます。*強制用語集* を指定します。この用語集には、必須用語として翻訳サービスに扱わせる絶対的で確実な用語またはフレーズのペアを含めます。あるいは、*並列コーパス* を指定します。このコーパスには、代替訳候補として翻訳サービスに考慮させる用語またはフレーズのペアを含めます。
- 言語サンプルとして機能するターゲット言語による大量のテキスト本文 (*単一言語コーパス*) をアップロードします。サービスは、これを評価して使用することで翻訳品質を全体的に向上させることができます。 

カスタマイズできるモデルのリストを参照するには、`GET /v2/models` メソッドを使用し、言語モデルごとに `customizable=true` 応答パラメーターが応答に含まれているか調べてください。

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

カスタマイズできるモデルごとに、サービス・インスタンスあたり最大 10 個のカスタマイズを保管できます。

## トレーニング・データの構造
{: #structure}

{{site.data.keyword.languagetranslatorshort}} サービスをトレーニングするために用語集または用語コーパスを指定するには、Translation Memory Exchange (TMX) [バージョン 1.4 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ttt.org/oscarstandards/tmx/tmx14.dtd){: new_window} 仕様に準拠した UTF-8 エンコードの有効な文書を作成してください。TMX は、機械翻訳ツールのために作られた XML 仕様です。以下のサンプルは、用語と訳語のペアを 2 つ含む TMX 形式の用語集ファイルです。

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

以下のように、用語と訳語のペアごとに `<tu>` タグで囲む必要があります。

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

`<tuv>` タグの `xml:lang` 属性は用語の言語を示し、`<seg>` タグには用語または訳語が含まれます。

{{site.data.keyword.languagetranslatorshort}} サービスは、`<tu>`、`<tuv>`、`<seg>` エレメントだけを使用します。このサンプルの中のその他のエレメントは、有効な TMX ファイルにするために必要なエレメントや通知用のエレメントです。ただし、このサービスでは使用されません。

上記のサンプルは、「patent」などの特定の技術用語の訳語を確実に標準化する方法と、「International Business Machines」などの社名の訳語をカスタマイズする方法を示しています。標準モデルでは、「International Business Machines」が「Machines Commerciales Internationales」と翻訳される可能性がありますが、これは社名なので実際には翻訳してはいけません。

## サンプルをテンプレートとして使用する

上記のサンプルを独自の用語集またはコーパスのテンプレートとして使用するには、以下の手順に従ってください。

1.  サンプルをコピーしてテキスト・エディターに貼り付けます。

1.  `<header>` タグの `srclang` 属性を、用語集または並列コーパスで使用するソース言語の[言語コード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} に変更します。

1.  用語または訳語ごとに、`<tuv>` タグの `xml:lang` 属性を正しい[言語コード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} に変更します。

    {{site.data.keyword.languagetranslatorshort}} サービスでは、アラビア語 (エジプト) 以外の言語に ISO 639-1 言語コードを使用し、アラビア語 (エジプト) に ISO 639-3 コードを使用します。

1.  拡張子 `.tmx` と UTF-8 エンコードを使用して文書を保存します。

### TMX ファイルを UTF-8 エンコードに変更する

TMX ファイルの作成や生成に使用できるツールは多数あります。多くの場合、デフォルトでは UTF-16 エンコードの TMX ファイルが生成されます。{{site.data.keyword.languagetranslatorshort}} サービスは UTF-8 エンコードの TMX ファイルしか受け入れません。TMX ファイルのエンコードを変更するには、以下の手順に従ってください。

1.  テキスト・エディターで TMX ファイルを開きます。

1.  XML ヘッダー (ある場合) を `<?xml ... encoding="utf-16"?>` から `<?xml ... encoding="utf-8"?>` に変更します。

1.  新しい名前と UTF-8 エンコード出力を指定してファイルを保存します。

Mac ユーザーは、手順 2 で文書の XML ヘッダーを更新した後に端末で以下のコマンドを実行して、ファイルのエンコードを変更することもできます。

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}

## カスタム翻訳モデルをトレーニングする
{: #training}

`POST /v2/models` メソッドを使用すると、TMX ファイルをアップロードして翻訳モデルをトレーニングできます。カスタム・モデルのトレーニングでは、以下のファイル・オプションを 1 つ以上指定します。

- `forced_glossary`: システムで必須用語として見なす用語のソース言語とターゲット言語のペアを含む UTF-8 エンコードの TMX ファイル。このファイルは、元のドメイン・データを完全に上書きします。

    強制用語集のファイル・サイズは 10 MB に制限されています。現在、アップロードできる強制用語集ファイルは、翻訳モデルごとに 1 つだけです。
    
- `parallel_corpus`: Watson でサンプルとして機能するフレーズのソース言語とターゲット言語のペアを含む UTF-8 エンコードの TMX ファイル。並列コーパスは、元のドメイン・データを上書きしないので、強制用語集とは違います。

    カスタム・モデルのトレーニングを成功させるには、並列コーパスの文書に用語と訳語のペアを 5,000 以上含める必要があります。
    
- `monolingual_corpus`: 翻訳内容に関連する、ターゲット言語によるテキスト本文を含む UTF-8 エンコードのプレーン・テキスト・ファイル。単一言語コーパスを指定すると、直訳が自然で滑らかな翻訳に改善されます。

    カスタム・モデルのトレーニングを成功させるには、単一言語コーパスの文書に用語と訳語のペアを 1,000 以上含める必要があります。

アップロードしたすべての用語集とコーパスのファイルの合計ファイル・サイズは、250 MB に制限されています。アップロードしたファイルのサイズに応じて、トレーニングに必要な時間は異なります。用語集には数分しかかかりませんが、大規模なコーパスには数時間かかることもあります。

以下の curl の例では、`forced_glossary` ファイル・オプションを使用します。
1. [トレーニング・データの構造](#structure)のセクションから TMX ファイルのサンプルをダウンロードします。
1. 基本モデルとしてフランス語のニュース・ドメイン (en-fr) を使用します。TMX ファイル内の指定内容によって、元のドメイン・データが完全に上書きされます。

    {{site.data.keyword.languagetranslatorshort}} サービスでサポートされるすべてのモデル・ドメインを検索するには、以下のように `GET v2/models` メソッドを使用します。

```curl
curl -u "{username}":"{password}" -X POST -F base_model_id=en-fr -F name="test_glossary" -F forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

`POST /v2/models` メソッドの応答として、`200` コードと新しい `model_id` が返されます。この新しくカスタマイズしたモデルでテキストを翻訳するときには、その `model_id` を使用します。

## トレーニングをモニタリングする

TMX トレーニング・ファイルのサイズは、`POST /v2/models` 要求のトレーニング時間に影響します。トレーニングの進行状況や、トレーニングが正常に完了したかどうかをモニターするには、`GET /v2/models/<model_id>` メソッドを使用して、応答内の `status` パラメーターの値を参照します。

以下の例のコマンドを実行すると、モデルに関する情報を表示し、[翻訳モデルをトレーニングする](#training)のセクションで開始したトレーニングの状況を確認できます。このコマンドは、本文が空の要求を使用します。

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}

`STATUS` 応答パラメーターに、トレーニング・プロセスのモデルの状態が以下のように表されます。

- `uploading`
- `uploaded`
- `dispatching`
- `queued@<#>`
- `training`
- `trained`
- `publishing`
- `available`

モデルの状況が `available` の場合は、モデルをサービス・インスタンスで使用できます。モデルが削除されたり、トレーニング・プロセス中にエラーが発生したりした場合は、以下のいずれかのエラーが表示されます。

- `deleted`
- `error`

## カスタム翻訳モデルを使用する

トレーニングしたカスタム翻訳モデルを `POST /v2/translate` メソッドまたは `GET /v2/translate` メソッドで使用するときには、その翻訳モデルの model\_id を指定します。

以下の例では、[カスタム翻訳モデルをトレーニングする](#training)のセクションでカスタマイズした、英語からフランス語への翻訳モデルを呼び出しています。

```curl
curl -u "{username}":"{password}" --header "Content-Type: application/json" -X POST --data "{\"model_id\": \"3e7dfdbe-f757-4150-afee-458e71eb93fb\",\"text\": \"Hello, my name is Watson, and I work for International Business Machines. How can I help you today?\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate 
```
{: codeblock}

{{site.data.keyword.languagetranslatorshort}} サービスは、IBM で開発した規格に加えて BLEU (bilingual evaluation understudy) 規格を使用して、翻訳の品質を評価します。結果は、言語のペア、使用されている専門語、データのドメインに応じて異なります。

## カスタム翻訳モデルを削除する

古くなった翻訳モデルは削除できます。カスタム翻訳モデルを削除するには、`DELETE /v2/models/<model_id>` メソッドを使用します。カスタムかデフォルトかにかかわらず、すべての翻訳モデルのモデル ID を取得するには、`GET /v2/models` メソッドを使用します。

以下のコマンドは、上記の例で作成した翻訳モデルを削除します。

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}


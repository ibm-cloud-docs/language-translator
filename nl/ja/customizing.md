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

# モデルのカスタマイズ
{: #customizing}

{{site.data.keyword.languagetranslatorshort}} に備わっているほとんどの翻訳モデルは、カスタムの用語や句、または翻訳データから取得した一般スタイルを学習させるように拡張することができます。独自のカスタム翻訳モデルを作成するには、以下の指示に従ってください。
{: shortdesc}

## 始めに
{: #before-you-begin}

1. ご使用の {{site.data.keyword.languagetranslatorshort}} サービス・インスタンスが拡張またはプレミアムの価格プランに存在することを確認します。ライト・プランおよび標準プランではカスタマイズがサポートされていません。
1. ご使用の言語ペアのカスタマイズ可能な基本モデルを見つけます。カスタム・モデルをトレーニングするには、基本モデルのモデル ID が必要です。
    - [翻訳モデル](/docs/services/language-translator?topic=language-translator-translation-models)・ページにリストされているモデルを検索します。**「カスタマイズ可能」**列で値**「true」**を探し、モデルの**「ソース」**言語および**「ターゲット」**言語が目的の言語ペアと一致することを確認します。
    - あるいは、[モデルのリスト (List models)![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/apidocs/language-translator#list-models) API メソッドを使用してモデルをプログラマチックに検索することもできます。`source` および `target` パラメーターを使用して、言語を基準に結果をフィルター操作できます。

## ステップ 1: トレーニング・データを作成する
{: #create-your-training-data}

このサービスでは、トレーニング・データを [Translation Memory Exchange (TMX) ファイル形式](#creating-tmx-files)で提供する必要があります。サービス・インスタンスでは、言語ペアごとに最大 10 個のカスタマイズを保管できます。このサービスは 2 種類のカスタマイズ要求をサポートします。強制グロッサリー、または並列文を含むコーパスのいずれかを使用して、モデルをカスタマイズできます。

- [強制グロッサリー](#forced-glossary-customization)は、特定の用語や句を特定の方法で翻訳するように強制する場合に使用します。
- [パラレル・コーパス](#parallel-corpus-customization)は、サンプル内の一般的な翻訳パターンからカスタム・モデルを学習させる場合に使用します。モデルがパラレル・コーパスから学習した内容は、モデルでまだ学習していない入力テキストの翻訳結果を向上させるのに役立つ可能性があります。

[Translation Memory Exchange (TMX) ファイル](#creating-tmx-files)を作成したら、モデルをトレーニングする準備ができたことになります。

## ステップ 2: モデルをトレーニングする
{: #train-your-model}

[モデルの作成 (Create model)![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/apidocs/language-translator#create-model) メソッドを使用して、モデルをトレーニングすることができます。要求では、カスタマイズ可能な基本モデルのモデル ID を指定し、`forced_glossary` または `parallel_corpus` パラメーターの中でトレーニング・データを指定します。

### 要求例
{: #train-model-example-request}

以下の要求例では、強制グロッサリー・ファイル _glossary.tmx_ を使用して `en-es` 基本モデルをカスタマイズします。サンプルの強制グロッサリー TMX ファイルについては、「[強制グロッサリーのカスタマイズ](#forced-glossary)」セクションを参照してください。

```bash
curl --user apikey:{apikey} -X POST --form forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

API 応答には、モデル ID など、カスタム・モデルに関する詳細が含まれます。モデル ID を使用してモデルの状況を確認し、モデルの状況が「使用可能 (available)」になったら文を翻訳します。

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

## ステップ 3: モデルの状況を確認する
{: #check-model-status}

モデルのトレーニングには、トレーニング・データの量に応じて、数分 (強制グロッサリーの場合) から数時間 (大規模なパラレル・コーパスの場合) かかります。目的のモデルが使用可能かどうかを確認するには、[モデルの取得 (Get model) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/apidocs/language-translator#get-model-details) メソッドを使用して、ステップ 2 のサービス応答で受信したモデル ID を指定します。または、[モデルのリスト (List models) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/apidocs/language-translator#list-models) メソッドを使用してすべてのモデルの状況を確認できます。

`status` 応答属性に、トレーニング・プロセスのモデルの状態が以下のように表されます。

- `uploading`
- `uploaded`
- `dispatching`
- `queued`
- `training`
- `trained`
- `publishing`
- `available`

モデルの状況が `available` の場合は、モデルをサービス・インスタンスで使用できます。 モデルが削除されたり、トレーニング・プロセス中にエラーが発生したりした場合は、以下のいずれかの状況が表示されます。

- `deleted`
- `error`

### 要求例
{: #check-model-example-request}

次の例では、モデル ID `96221b69-8e46-42e4-a3c1-808e17c787ca` で識別されるモデルの情報を取得します。

```bash
curl --user apikey:{apikey_value} "https://gateway.watsonplatform.net/language-translator/api/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## ステップ 4: カスタム・モデルを使用してテキストを翻訳する
{: #translate-text}

カスタム・モデルを使用するには、翻訳するテキストとカスタム・モデルのモデル ID を[翻訳 (Translate) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/apidocs/language-translator#translate) メソッドで指定します。

### 要求例
{: #translate-text-example-request}

次の例では、モデル ID `96221b69-8e46-42e4-a3c1-808e17c787ca` で識別されるカスタム・モデルを使用してテキストを翻訳します。

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data '{"text":"Hello","model_id":"96221b69-8e46-42e4-a3c1-808e17c787ca"}' https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}


## 強制グロッサリーのカスタマイズ
{: #forced-glossary-customization}

**強制グロッサリー**を使用して、特定の用語と句の必須翻訳を設定します。翻訳の動作を具体的に制御する必要がある場合は、強制グロッサリーを使用してください。

- トレーニング・データ・フォーマット: [TMX](#creating-tmx-files) (UTF-8 エンコード)
- 最大ファイル・サイズ: 10 MB
- 基本モデル、またはパラレル・コーパスでカスタマイズされたモデルに強制グロッサリーを適用できる
- モデルごとに強制グロッサリーを 1 つに制限する

強制グロッサリーの例では大文字と小文字が区別されるため、アプリケーションが検出するコンテンツの大/小文字の区別が必ずトレーニング・データに反映されるようにしてください。
{: tip}

### 強制グロッサリーの例
{: #forced-glossary-example}

次の例は、2 つの翻訳ペアを持つ TMX ファイルを示しています。最初のペアは、翻訳中に「international business machines」を英語のままで保持することを強制します。非公式のやり取りで誤って大/小文字になった会社名を保持したい場合には、このような強制翻訳が役立つことがあります。2 番目のペアは、「patent」を翻訳する際に常に「brevet」を使用するようモデルに強制します。

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



## パラレル・コーパスのカスタマイズ
{: #parallel-corpus-customization}

**パラレル・コーパス**を使用すると、基本モデルが学習する基礎となる追加の翻訳を提供できます。これは、基本モデルを特定のドメインに適応させるのに役立ちます。結果として生成されるカスタム・モデルがテキストをどのように翻訳するかは、パラレル・コーパスと基本モデルがモデルでどのように統合的に理解されるかに依存します。

- トレーニング・データ・フォーマット: [TMX](#creating-tmx-files) (UTF-8 エンコード)
- 翻訳ペアの最大長: 80 ソース・ワード
- 翻訳ペアの最小数: 5,000
- 最大ファイル・サイズ: 250 MB
- ファイルの累積サイズが 250 MB を超えない限り、`parallel_corpus` マルチパート・フォーム・パラメーターを繰り返すことで、複数のパラレル・コーパス・ファイルを送信できます。

### パラレル・コーパスの例
{: #parallel-corpus-example}

以下に、OPUS オープン・パラレル・コーパス Web サイトで入手可能な [MultiUN コレクション![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://opus.nlpl.eu/MultiUN.php) からダウンロードした、英語とフランス語のパラレル・コーパスの一部を示しています。TMX ファイル全体の圧縮バージョンは、[ここ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz) からダウンロードできます。


```xml
<?xml version="1.0" encoding="UTF-8" ?>
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

パラレル・コーパスでカスタマイズした場合の改善内容は、一般的に、強制グロッサリー・カスタマイズで得られる強制的な結果よりも予測困難です。例えば、この例のパラレル・コーパスの次の翻訳単位を見てみましょう (第 172～175 行)。

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

「55/102. Globalization and its impact on the full enjoyment of all human rights」を基本モデル `en-fr` で翻訳すると、サービスの応答では次のように翻訳されます。

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

この例のコーパスでトレーニングされたカスタム・モデルを使って同じ入力文を翻訳した場合、サービスの応答ではトレーニング・データで提供されるサンプル翻訳とは異なる翻訳になります。

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- カスタム・モデルは、「the full enjoyment」を「la pleine jouissance」ではなく「le plein exercice」と翻訳します。基本モデルの動作でこうした逸脱が起きてしまう原因として、コーパスに「enjoyment」が「exercice」に翻訳される例が多数存在する可能性があります。
- カスタム・モデルは、翻訳単位「des droits de l'homme」からの結果を複製せずに、「of all human rights」を「de tous les droits de l'homme」に翻訳します。この動作は、トレーニングされたモデルでの基本モデルの総合的な理解と、「of all human rights」に関連するすべての翻訳サンプルをパラレル・コーパスから反映したことによるものです。

場合によっては、パラレル・コーパスを使ってトレーニングされたカスタム・モデルが、ユーザーが提供した特定の例を無視しているように見えることもあります。この場合、トレーニング・データの中でそのような翻訳動作に影響を与えている可能性がある他の文を探します。または、翻訳を具体的に制御する必要がある場合には強制グロッサリーの使用を検討してください。


## TMX ファイルの作成
{: #creating-tmx-files}

{{site.data.keyword.languagetranslatorshort}} サービスをトレーニングするために用語集または用語コーパスを指定するには、Translation Memory Exchange (TMX) [バージョン 1.4 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ttt.org/oscarStandards/tmx/){: new_window} 仕様に準拠した UTF-8 エンコードの有効な文書を作成してください。 TMX は、機械翻訳ツールのために作られた XML 仕様です。 以下のサンプルは、翻訳ペア (`<tu>` 要素) を 2 つ含む TMX 形式の用語集ファイルです。

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

以下のように、用語と訳語のペアごとに `<tu>` タグで囲む必要があります。

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

`<tuv>` タグの `xml:lang` 属性は用語の言語を示し、`<seg>` タグには用語または訳語が含まれます。

{{site.data.keyword.languagetranslatorshort}} サービスは、`<tu>`、`<tuv>`、`<seg>` エレメントだけを使用します。 このサンプルの中のその他のエレメントは、有効な TMX ファイルにするために必要なエレメントや通知用のエレメントです。ただし、このサービスでは使用されません。



### サンプルをテンプレートとして使用する
{: #using-the-example-template}

上記のサンプルを独自の用語集またはコーパスのテンプレートとして使用するには、以下の手順に従ってください。

1. サンプルをコピーしてテキスト・エディターに貼り付けます。

2. `<header>` タグの `srclang` 属性を、用語集または並列コーパスで使用するソース言語の[言語コード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} に変更します。

3. 用語または訳語ごとに、`<tuv>` タグの `xml:lang` 属性を正しい[言語コード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} に変更します。

4. 拡張子 `.tmx` と UTF-8 エンコードを使用して文書を保存します。

### TMX ファイルを UTF-8 エンコードに変更する
{: #changing-tmx-file-to-utf-8}

TMX ファイルの作成や生成に使用できるツールは多数あります。 多くの場合、デフォルトでは UTF-16 エンコードの TMX ファイルが生成されます。 {{site.data.keyword.languagetranslatorshort}} サービスは UTF-8 エンコードの TMX ファイルしか受け入れません。 TMX ファイルのエンコードを変更するには、以下の手順に従ってください。

1. テキスト・エディターで TMX ファイルを開きます。

1. XML ヘッダー (ある場合) を `<?xml ... encoding="utf-16"?>` から `<?xml ... encoding="utf-8"?>` に変更します。

1. 新しい名前と UTF-8 エンコード出力を指定してファイルを保存します。

Mac ユーザーは、手順 2 で文書の XML ヘッダーを更新した後に端末で以下のコマンドを実行して、ファイルのエンコードを変更することもできます。

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}


## カスタム翻訳モデルを削除する
{: #deleting-a-custom-model}

カスタム翻訳モデルを削除するには、[モデルの削除 (Delete model) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/apidocs/language-translator#delete-model) メソッドを使用します。

以下のコマンドは、モデル ID `3e7dfdbe-f757-4150-afee-458e71eb93fb` の翻訳モデルを削除します。

```curl
curl --user apikey:{apikey_value} --request DELETE "https://gateway.watsonplatform.net/language-translator/api/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: codeblock}

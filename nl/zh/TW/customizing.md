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

# 自訂您的模型
{: #customizing}

您可以擴充 {{site.data.keyword.languagetranslatorshort}} 中大部分提供的翻譯模型，以學習自訂術語和詞組，或衍生自翻譯資料的一般樣式。請追蹤下列指示，以建立自己的翻譯模型。
{: shortdesc}

## 開始之前
{: #before-you-begin}

1. 確定您的 {{site.data.keyword.languagetranslatorshort}} 服務實例是在「進階」或「超值」定價方案上。「精簡」和「標準」方案不支援自訂作業。
1. 為您的語言配對尋找可自訂的基礎模型。您將需要基礎模型的模型 ID，才能訓練自訂模型。
    - 搜尋[翻譯模型](/docs/services/language-translator?topic=language-translator-translation-models)頁面上列出的模型。在**可自訂**直欄中尋找 "**true**" 值，並確定模型的**來源**和**目標**語言符合您的語言配對。
    - 或者，您也可以使用[列出模型 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/apidocs/language-translator#list-models) API 方法，以程式設計方式搜尋模型。您可以使用 `source` 和 `target` 參數，依語言過濾結果。

## 步驟 1：建立您的訓練資料
{: #create-your-training-data}

服務要求以 [Translation Memory Exchange (TMX) 檔案格式](#creating-tmx-files)提供訓練資料。您最多可以為服務實例中的每個語言配對儲存 10 個自訂項目。服務支援兩種類型的自訂要求。您可以使用強制名詞解釋或包含平行句子的語料庫來自訂模型。

- 使用[強制名詞解釋](#forced-glossary-customization)，強制以特定方式翻譯特定術語和詞組。
- 當您想要自訂模型從範例中的一般翻譯型樣進行學習時，請使用[平行語料庫](#parallel-corpus-customization)。您的模型從平行語料庫中學到的內容，可以改善模型尚未訓練之輸入文字的翻譯結果。

建立 [Translation Memory Exchange (TMX) 檔案](#creating-tmx-files)之後，表示您已準備好要訓練您的模型。

## 步驟 2：訓練您的模型
{: #train-your-model}

使用[建立模型 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/apidocs/language-translator#create-model) 方法，來訓練您的模型。在您的要求中，指定可自訂基礎模型的模型 ID，以及 `forced_glossary` 或 `parallel_corpus` 參數中的訓練資料。

### 範例要求
{: #train-model-example-request}

下列範例會使用強制名詞解釋檔案 (_glossary.tmx_) 來自訂 `en-es` 基礎模型。請參閱[強制名詞解釋自訂作業](#forced-glossary)一節，以取得強制名詞解釋 TMX 檔案範例。

```bash
curl --user apikey:{apikey} -X POST --form forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

API 回應將包含自訂模型的詳細資料，包括其模型 ID。請使用模型 ID 來檢查模型的狀態，一旦模型的狀態變成「可用」，就會翻譯句子。

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

## 步驟 3：檢查模型的狀態
{: #check-model-status}

模型訓練可能需要幾分鐘（針對強制名詞解釋）到幾小時（針對大型平行語料庫），取決於涉及多少訓練資料。若要查看您的模型是否可用，請使用[取得模型 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/apidocs/language-translator#get-model-details) 方法，並指定您在步驟 2 的服務回應中接收到的模型 ID。此外，您可以使用[列出模型 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/apidocs/language-translator#list-models) 方法，來檢查所有模型的狀態。

`status` 回應屬性說明模型在訓練過程中的狀態：

- `uploading`
- `uploaded`
- `dispatching`
- `queued`
- `training`
- `trained`
- `publishing`
- `available`

當模型狀態為 `available` 時，表示您的模型已準備好與您的服務實例搭配使用。如果您的模型已被刪除，或如果它在訓練過程中發生錯誤，則您可能會看到下列其中一個狀態：

- `deleted`
- `error`

### 範例要求
{: #check-model-example-request}

下列範例會取得模型 ID `96221b69-8e46-42e4-a3c1-808e17c787ca` 所識別之模型的資訊。

```bash
curl --user apikey:{apikey_value} "https://gateway.watsonplatform.net/language-translator/api/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## 步驟 4：使用您的自訂模型翻譯文字
{: #translate-text}

若要使用您的自訂模型，請在[翻譯 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/apidocs/language-translator#translate) 方法中指定您要翻譯的文字，以及自訂模型的模型 ID。

### 範例要求
{: #translate-text-example-request}

下列範例會使用模型 ID `96221b69-8e46-42e4-a3c1-808e17c787ca` 所識別的自訂模型來翻譯文字。

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data '{"text":"Hello","model_id":"96221b69-8e46-42e4-a3c1-808e17c787ca"}' https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}


## 強制名詞解釋自訂作業
{: #forced-glossary-customization}

使用**強制名詞解釋**來設定特定術語和詞組的必要翻譯。如果您想要對翻譯行為進行特定控制，請使用強制名詞解釋。

- 訓練資料格式：[TMX](#creating-tmx-files)（UTF-8 編碼）
- 檔案大小上限：10 MB
- 您可以將強制名詞解釋套用至基礎模型，或套用至已使用平行語料庫自訂的模型
- 限制每個模型一個強制名詞解釋

強制名詞解釋範例會區分大寫，因此請確定您的訓練資料會反映您的應用程式將發現之內容的大寫。
{: tip}

### 強制名詞解釋範例
{: #forced-glossary-example}

下列範例顯示一個 TMX 檔案與兩個翻譯配對。第一個配對強制 "international business machines" 在翻譯期間保留為英文。如果您想要在非正式通訊中保留未適當大寫的公司名稱，這種類型的強制翻譯可能會非常實用。第二個配對強制模型在翻譯 "patent" 時一律使用 "brevet"。

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



## 平行語料庫自訂作業
{: #parallel-corpus-customization}

使用**平行語料庫**來提供其他翻譯，供基礎模型從中學習。這有助於讓基礎模型適應特定領域。產生的自訂模型如何翻譯文字，取決於模型對平行語料庫和基礎模型的綜合理解。

- 訓練資料格式：[TMX](#creating-tmx-files)（UTF-8 編碼）
- 翻譯配對的長度上限：80 個來源字組
- 翻譯配對的數目下限：5,000
- 檔案大小上限：250 MB
- 只要檔案的累積大小不超出 250 MB，您就可以藉由重複 `parallel_corpus` 多組件表單參數，來提交多個平行語料庫檔案。

### 平行語料庫範例
{: #parallel-corpus-example}

下列是從英文到法文的平行語料庫的一小段，而此語料庫是從 OPUS 開放平行語料庫網站上提供的 [MultiUN 集合 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://opus.nlpl.eu/MultiUN.php) 所下載的。您可以在[這裡 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz) 下載整個 TMX 檔案的壓縮版。


```xml
<?xml version="1.0" encoding="UTF-8"?>
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

來自平行語料庫自訂作業的一般改進，比您從強制名詞解釋自訂作業取得的必要結果更難以預測。例如，考量下列來自範例平行語料庫的翻譯單位（第 172-175 行）。

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

如果您使用基礎 `en-fr` 模型，翻譯 "55/102. Globalization and its impact on the full enjoyment of all human rights"，則服務會以下列翻譯回應。

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

當相同的輸入句子由使用範例語料庫訓練的自訂模型翻譯時，服務會以不同翻譯回應，而此翻譯與訓練資料中提供的範例翻譯不相同。

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- 自訂模型會將 "the full enjoyment" 翻譯為 "le plein exercice"，而非 "la pleine jouissance"。與基礎模型行為產生這種偏差的可能說明是語料庫中有許多將 "enjoyment" 翻譯為 "exercice" 的範例。
- 自訂模型會將 "of all human rights" 翻譯為 "de tous les droits de l'homme"，而非從翻譯單位 "des droits de l'homme" 重新產生結果。這種行為反映了訓練模型可以連貫性瞭解基礎模型，以及與平行語料庫中 "of all human rights" 相關的所有翻譯範例。

在某些情況下，使用平行語料庫訓練的自定義模型似乎會忽略您提供的特定範例。在這些情況下，嘗試搜尋您的訓練資料，找出可能影響翻譯行為的其他句子，或考量使用強制名詞解釋，如果您想要控制特定翻譯的話。


## 建立 TMX 檔案
{: #creating-tmx-files}

若要提供術語的名詞解釋或語料庫，以訓練 {{site.data.keyword.languagetranslatorshort}} 服務，請建立有效的 UTF-8 編碼文件，其必須符合 Translation Memory Exchange (TMX) [1.4 版 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ttt.org/oscarStandards/tmx/){: new_window}規格。TMX 是針對機器翻譯工具設計的 XML 規格。下列範例是 TMX 格式的名詞解釋檔案，其中具有兩個翻譯單位（`<tu>` 元素）：

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

每一個術語與翻譯配對必須以 `<tu>` 標籤括住：

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

`<tuv>` 標籤中的 `xml:lang` 屬性可以識別表示術語所用的語言，而 `<seg>` 標籤則包含術語或翻譯。

{{site.data.keyword.languagetranslatorshort}} 服務只會使用 `<tu>`、`<tuv>` 及 `<seg>` 元素。範例中的所有其他元素是製作有效檔案所需的元素，或是參考元素，但不為服務所用。



### 使用範例作為範本
{: #using-the-example-template}

若要使用所提供的範例作為您專屬名詞解釋或語料庫的範本，請完成下列步驟：

1. 複製範例並貼入文字編輯器中。

2. 將 `<header>` 標籤的 `srclang` 屬性變更為名詞解釋或平行語料庫所使用之來源語言的[語言碼 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}。

3. 將 `<tuv>` 標籤的 `xml:lang` 屬性變更為每一個術語或翻譯的正確 [語言碼 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}。

4. 使用副檔名 `.tmx` 及 UTF-8 編碼來儲存文件。

### 將 TMX 檔案變更為 UTF-8 編碼
{: #changing-tmx-file-to-utf-8}

您可以使用數種工具來建立或產生 TMX 檔案。通常，所產生的 TMX 檔案預設為 UTF-16 編碼。{{site.data.keyword.languagetranslatorshort}} 服務只接受 UTF-8 編碼的 TMX 檔案。若要變更 TMX 檔案的編碼，請完成下列步驟：

1. 在文字編輯器中開啟 TMX 檔案。

1. 將 XML 標頭（若有的話）從 `<?xml ... encoding="utf-16"?>` 變更為 `<?xml ... encoding="utf-8"?>`。

1. 使用新名稱及 UTF-8 編碼輸出來儲存檔案。

Mac 使用者也可以如步驟 2 所述更新文件的 XML 標頭，然後在「終端機」中執行下列指令來變更檔案編碼：

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}


## 刪除自訂翻譯模型
{: #deleting-a-custom-model}

若要刪除自訂翻譯模型，請使用[刪除模型 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/apidocs/language-translator#delete-model) 方法。

下列指令會刪除模型 ID 為 `3e7dfdbe-f757-4150-afee-458e71eb93fb` 的翻譯模型。

```curl
curl --user apikey:{apikey_value} --request DELETE "https://gateway.watsonplatform.net/language-translator/api/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: codeblock}

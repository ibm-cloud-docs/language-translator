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

# 自訂您的模型
{: #customizing}

您是否正在建立供客戶支援中心使用的翻譯器，並且在交談中具有您想要以特定方式處理的公司專用術語？您是否正在建立一種方式，讓貴公司在某個國家的工程師能以另一種語言查閱專利資料，並且您通常會針對特定技術提交專利？請在 {{site.data.keyword.languagetranslatorshort}} API 中使用您自己的資料，來建立自訂字典及自訂翻譯模型。
{: shortdesc}

您可以使用下列方式自訂 {{site.data.keyword.languagetranslatorshort}} 模型：

- 教導服務如何配對來源語言與目標語言中的術語與詞組。請提供*強制名詞解釋*，其中包含術語或詞組的配對，而您想要翻譯服務將這些術語或詞組視為必要的絕對限定術語。或者，提供*平行語料庫*，其中包含術語或詞組的配對，而您想要將這些術語或詞組充當翻譯服務考量的替代翻譯建議。
- 上傳大量以目標語言書寫的文字主體（稱為*單語語料庫*），充當服務可以評估並用來提高整體翻譯品質的語言樣本。

若要查看您可以自訂的模型清單，請使用 `GET /v2/models` 方法，在每一個語言模型的回應中尋找回應參數 `customizable=true`。

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

每一個可自訂模型最多可以為每個服務實例儲存 10 個自訂項目。

## 訓練資料的結構
{: #structure}

若要提供術語的名詞解釋或語料庫，以訓練 {{site.data.keyword.languagetranslatorshort}} 服務，請建立有效的 UTF-8 編碼文件，其必須符合 Translation Memory Exchange (TMX) [1.4 版 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www.ttt.org/oscarstandards/tmx/tmx14.dtd){: new_window}規格。TMX 是針對機器翻譯工具設計的 XML 規格。下列範例是 TMX 格式的名詞解釋檔案，其中具有兩個術語與翻譯配對：

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

每一個術語與翻譯配對必須以 `<tu>` 標籤括住：

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

`<tuv>` 標籤中的 `xml:lang` 屬性可以識別表示術語所用的語言，而 `<seg>` 標籤則包含術語或翻譯。

{{site.data.keyword.languagetranslatorshort}} 服務只會使用 `<tu>`、`<tuv>` 及 `<seg>` 元素。範例中的所有其他元素是製作有效檔案所需的元素，或是參考元素，但不為服務所用。

前一個範例顯示如何明確地標準化技術術語（如 'patent'）的翻譯，以及如何自訂公司名稱（如 'International Business Machines'）的翻譯。在標準模型中，'International Business Machines' 可能翻譯為 'Machines Commerciales Internationales'，但實際上不應該翻譯，因為它是公司名稱。

## 使用範例作為範本

若要使用所提供的範例作為您專屬名詞解釋或語料庫的範本，請完成下列步驟：

1.  複製範例並貼入文字編輯器中。

1.  將 `<header>` 標籤的 `srclang` 屬性變更為名詞解釋或平行語料庫所使用之來源語言的[語言碼 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}。

1.  將 `<tuv>` 標籤的 `xml:lang` 屬性變更為每一個術語或翻譯的正確 [語言碼 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://www-01.sil.org/iso639-3/codes.asp){: new_window}。

    {{site.data.keyword.languagetranslatorshort}} 服務可對所有語言使用 ISO 639-1 語言碼，但埃及阿拉伯文除外，其使用 ISO 639-3 語言碼。

1.  使用副檔名 `.tmx` 及 UTF-8 編碼來儲存文件。

### 將 TMX 檔案變更為 UTF-8 編碼

您可以使用數種工具來建立或產生 TMX 檔案。通常，所產生的 TMX 檔案預設為 UTF-16 編碼。{{site.data.keyword.languagetranslatorshort}} 服務只接受 UTF-8 編碼的 TMX 檔案。若要變更 TMX 檔案的編碼，請完成下列步驟：

1.  在文字編輯器中開啟 TMX 檔案。

1.  將 XML 標頭（若有的話）從 `<?xml ... encoding="utf-16"?>` 變更為 `<?xml ... encoding="utf-8"?>`。

1.  使用新名稱及 UTF-8 編碼輸出來儲存檔案。

Mac 使用者也可以如步驟 2 所述更新文件的 XML 標頭，然後在「終端機」中執行下列指令來變更檔案編碼：

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}

## 訓練自訂翻譯模型
{: #training}

使用 `POST /v2/models` 方法來上傳您的 TMX 檔案，並訓練您的翻譯模型。請至少指定下列其中一個檔案選項來訓練您的自訂模型：

- `forced_glossary`：UTF-8 編碼的 TMX 檔案，其中包含來源語言及目標語言中系統看成絕對之相符術語的配對。此檔案將完全改寫原始領域資料。

    強制名詞解釋的檔案大小不得超過 10 MB。目前您只能為每個翻譯模型上傳一個強制名詞解釋檔案。
    
- `parallel_corpus`：UTF-8 編碼的 TMX 檔案，其中包含來源語言及目標語言中充當 Watson 之範例的相符詞組。平行語料庫不同於強制名詞解釋，因為它們不會改寫原始領域資料。

    若要順利訓練自訂模型，平行語料庫文件必須至少包含 5,000 個術語及翻譯配對。
    
- `monolingual_corpus`：UTF-8 編碼的純文字檔案，其中包含目標語言中與您翻譯之內容相關的文字主體。提供單語語料庫可藉由讓翻譯更加流暢及自然而改善直譯。

    若要順利訓練自訂模型，單語語料庫文件必須至少包含 1,000 個句子。

所有上傳的名詞解釋及語料庫檔案，其檔案大小累加後不得超過 250MB。根據上傳檔案的大小，訓練時間可以從數分鐘（若為名詞解釋）到數小時（若為大型語料庫）。

下列 curl 範例使用 `forced_glossary` 檔案選項。
1. 從[訓練資料的結構](#structure)區段中下載 TMX 檔案樣本
1. 使用法文新聞領域 (en-fr) 作為基本模型。在 TMX 檔案中指定的任何內容都會完全改寫原始領域資料。

    若要查閱 {{site.data.keyword.languagetranslatorshort}} 服務支援的所有模型領域，請使用 `GET v2/models` 方法：

```curl
curl -u "{username}":"{password}" -X POST -F base_model_id=en-fr -F name="test_glossary" -F forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

`POST /v2/models` 方法會以 `200` 程式碼及新的 `model_id` 作為回應。當使用這個新自訂的模型翻譯文字時，請使用 `model_id`。

## 監視訓練

TMX 訓練檔案的大小會影響 `POST /v2/models` 要求的訓練時間。若要監視訓練進度，以及訓練是否順利完成，請使用 `GET /v2/models/<model_id>` 方法，並在回應中查看 `status` 參數的值。

此範例指令會提供模型的相關資訊，並檢查已在[訓練翻譯模型](#training)區段中開始之訓練的狀態。此指令會使用空白內文要求。

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}

`STATUS` 回應參數說明模型在訓練過程中的狀態：

- `uploading`
- `uploaded`
- `dispatching`
- `queued@<#>`
- `training`
- `trained`
- `publishing`
- `available`

當模型狀態為 `available` 時，表示您的模型已準備好與您的服務實例搭配使用。如果您的模型遭到刪除，或如果它在訓練過程中發生錯誤，則您可能看到下列其中一個錯誤：

- `deleted`
- `error`

## 使用自訂翻譯模型

在訓練自訂翻譯模型之後，請指定該翻譯模型的 model\_id，以與 `POST /v2/translate` 或 `GET /v2/translate` 方法搭配使用。

下列範例會呼叫已在[訓練自訂翻譯模型](#training)區段中自訂的英文或法文模型。

```curl
curl -u "{username}":"{password}" --header "Content-Type: application/json" -X POST --data "{\"model_id\": \"3e7dfdbe-f757-4150-afee-458e71eb93fb\",\"text\": \"Hello, my name is Watson, and I work for International Business Machines. How can I help you today?\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate 
```
{: codeblock}

{{site.data.keyword.languagetranslatorshort}} 服務會使用 BLEU (Bilingual Evaluation Understudy) 標準，以及 IBM 開發的標準來評估翻譯的品質。結果可能會有所不同，視語言配對、所用的方言或您的資料領域而定。

## 刪除自訂翻譯模型

當翻譯模型過期時，您可能想要刪除它。若要刪除自訂翻譯模型，請使用 `DELETE /v2/models/<model_id>` 方法。若要擷取所有翻譯模型（無論是自訂還是預設）的模型 ID，請使用 `GET /v2/models` 方法。

下列指令會刪除已在這些範例中建立的翻譯模型。

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}


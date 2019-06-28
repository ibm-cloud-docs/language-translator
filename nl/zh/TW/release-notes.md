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

# 版本注意事項

下列新增特性及服務的變更可供使用。
{: shortdesc}

## 新的 API 鑑別處理程序
{: #iam-auth-process }

對於在下列位置進行管理的服務實例，{{site.data.keyword.languagetranslatorshort}} 服務具有新的 API 鑑別處理程序：

- 達拉斯（自 2018 年 6 月 15 日開始）
- 法蘭克福（自 2018 年 6 月 15 日開始）
- 倫敦
- 雪梨（自 2018 年 6 月 12 日開始）
- 東京
- 華盛頓特區（自 2018 年 6 月 12 日開始）

{{site.data.keyword.cloud_notm}} 正在移轉至記號型 Identity and Access Management (IAM) 鑑別。對於某些服務實例，您可以使用 IAM 向 API 進行鑑別。

- 對於在先前指出之位置中建立的_新_ 服務實例，您可以使用 IAM 進行鑑別。您可以傳遞載送記號或 API 金鑰。記號支援已經過鑑別的要求，而不需要在每個呼叫中內嵌服務認證。API 金鑰使用基本鑑別。

    當您使用任何 Watson SDK 時，您可以傳遞 API 金鑰，並讓 SDK 管理記號的生命週期。如需相關資訊和範例，請參閱 API 參考資料中的[鑑別 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/apidocs/language-translator#authentication){: new_window}。
- 對於在指出日期之前建立的_現有_ 服務實例，您可以提供服務實例的使用者名稱及密碼來繼續進行鑑別。但最終需要將這些服務實例移轉至 IAM 鑑別。將提供有關移轉處理程序和日期的更新項目。如需移轉的相關資訊，請參閱[將 Cloud Foundry 服務實例移轉至資源群組](/docs/resources?topic=resources-migrate#migrate)。

若要找出要使用的鑑別，請按一下 [{{site.data.keyword.cloud_notm}} 資源頁面 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://cloud.ibm.com/resources){: new_window} 上的服務實例，來檢視服務認證。

## 服務 API 版本化
{: shortdesc}

{{site.data.keyword.languagetranslatorshort}} 第 3 版中的 API 要求需要版本參數，取得格式為 `version=YYYY-MM-DD` 的日期。每當我們以舊版不相容方式變更 API 時，就會發行新的 API 次要版本。

請在每個 API 要求中傳送版本參數。服務會使用所指定日期的 API 版本，或該日期之前的最新版本。請勿預設為現行日期。請改為指定符合與您的應用程式相容的版本的日期，並且在您的應用程式備妥可接受較新的版本之前，不要變更該日期。

現行版本為 `2018-05-01`。

## 2019 年 6 月 14 日
{: #14-june-2019}

現在提供英文和希臘文的新[翻譯模型](/docs/services/language-translator?topic=language-translator-translation-models)。
- 英文至希臘文 (en-el)
- 希臘文至英文 (el-en)

## 2019 年 6 月 13 日
{: #13-june-2019}

現在提供英文和希伯來文的新[翻譯模型](/docs/services/language-translator?topic=language-translator-translation-models)。
- 英文至希伯來文 (en-he)
- 希伯來文至英文 (he-en)

## 2019 年 3 月 21 日
{: #21-march-2019}

從 2019 年 3 月 21 日開始，您只會看到與指派給 {{site.data.keyword.cloud_notm}} 帳戶之角色相關聯的服務認證資訊。例如，如果您已獲指派 `reader` 角色，將看不到任何 `writer` 或更高層次的服務認證。

此變更不會影響具有現有服務金鑰認證之使用者或應用程式的 API 存取。只會影響 {{site.data.keyword.cloud_notm}} 內的認證檢視。

如需服務金鑰和使用者角色的相關資訊，請參閱 [IAM 服務 API 金鑰](/docs/services/watson?topic=watson-api-key-bp#api-key-bp)。

## 2018 年 12 月 14 日
{: #14-december-2018}

- 您現在可以在 {{site.data.keyword.cloud_notm}} 倫敦位置建立 {{site.data.keyword.languagetranslatorshort}} 服務實例。

## 2018 年 11 月 16 日
{: #16-november-2018}

- [翻譯文件（測試版）](/docs/services/language-translator?topic=language-translator-translating-documents) 現在可以透過新的 API 端點使用。請提交 Microsoft Office 文件、PDF 或其他具有受支援檔案格式的文件，而且 {{site.data.keyword.languagetranslatorshort}} 將提供保留原始格式化的已翻譯副本。
  - [受支援檔案格式](/docs/services/language-translator?topic=language-translator-translating-documents#supported-file-types)包括 `.doc`、`.ppt`、`.pdf` 及其他。

- 現在提供匈牙利文的新[翻譯模型](/docs/services/language-translator?topic=language-translator-translation-models)：
  - 匈牙利文至英文 (hu-en)
  - 英文至匈牙利文 (en-hu)

## 2018 年 11 月 8 日
{: #8-november-2018}

- 您現在可以在 {{site.data.keyword.cloud_notm}} 東京位置建立 {{site.data.keyword.languagetranslatorshort}} 服務實例。

## 2018 年 8 月 9 日
{: #9-august-2018}

現在提供巴克摩挪威文的新[翻譯模型](/docs/services/language-translator?topic=language-translator-translation-models)：
  - 巴克摩挪威文至英文 (nb-en)
  - 英文至巴克摩挪威文 (en-nb)

## 2018 年 6 月 27 日
{: #27-june-2018}

現在提供以六種新語言為特色的新[翻譯模型](/docs/services/language-translator?topic=language-translator-translation-models)：
  - 加泰蘭文
    - 加泰蘭文至西班牙文 (ca-es)
    - 西班牙文至加泰蘭文 (es-ca)
  -      捷克文
    
    - 捷克文至英文 (cs-en)
    - 英文至捷克文 (en-cs)
  -      丹麥文
    
    - 丹麥文至英文 (da-en)
    - 英文至丹麥文 (en-da)
  -      芬蘭文
    
    - 芬蘭文至英文 (fi-en)
    - 英文至芬蘭文 (en-fi)
  -      北印度文
    
    - 北印度文至英文 (hi-en)
    - 英文至北印度文 (en-hi)
  -      瑞典文
    
    - 瑞典文至英文 (sv-en)
    - 英文至瑞典文 (en-sv)
  

## 2018 年 6 月 15 日
{: #15-june-2018}

自 2018 年 6 月 15 日開始，在德國及美國南部地區建立的新服務實例會使用 [Identityand Access Management (IAM) 鑑別](#iam-auth-process)。

您在德國及美國南部建立的新服務實例與 Language Translator 第 2 版不相容。如果您使用 Language Translator 第 2 版，並打算在您的應用程式中使用新的服務實例，將需要[移轉至第 3 版 API](/docs/services/language-translator?topic=language-translator-migrating)。

## 2018 年 6 月 12 日
{: #12-june-2018}

現在提供 {{site.data.keyword.languagetranslatorshort}} 第 3 版。在 2018 年 7 月 31 日之後，將不再提供第 2 版 Language Translator API。若要充分運用最新的服務加強功能，請移轉至第 3 版 API。如需相關資訊，請檢視[移轉至 Language Translator 第 3 版](/docs/services/language-translator?topic=language-translator-migrating)頁面。

### 第 3 版的新增功能
{: #whats-new}

-  {{site.data.keyword.languagetranslatorshort}} API 第 3 版隨附**神經機器翻譯** (NMT) 模型，此模型提供大幅改善的翻譯結果。所有 NMT 模型現在都可以用於自訂作業。
-  使用自訂模型作為強制名詞解釋自訂作業的基礎模型。
-  API 第 3 版是已淘汰之 API 第 2 版的簡化全 JSON 子集。
-  引進 API 版本日期，讓開發人員可以按照自己的速度自由採用未來的 API 變更。

### 重大變更
{: #breaking-changes}

- 所有 API 端點的必要版本日期：API 第 3 版要求需要格式為 `version=YYYY-MM-DD` 的版本日期查詢參數。最新 API 版本為 `version=2018-05-01`。
- 簡化的 API：
  - **翻譯**和**識別**方法不會在第 3 版中提供傳回純文字回應的選項。這些方法只會傳回 JSON 回應。
  - 第 3 版中不支援 `GET /translate` 和 `GET /identify` 方法。請改用 `POST /translate` 和 `POST /identify` 方法。 
- 第 3 版中不支援單語語料庫自訂作業。
- 同時使用平行語料庫和強制名詞解釋建立自訂模型，現在需要以兩個 API 呼叫來完成。首先，使用平行語料庫自訂模型。在自訂模型完成訓練之後，再使用強制名詞解釋來自訂它。此變更可讓您使用一個利用平行語料庫訓練的自訂模型，作為強制名詞解釋自訂作業的基礎。
- 第 3 版 API 中不提供特殊化的專利和會話領域模型。與更舊的特殊化模型相比，NMT 模型在專利和會話領域中提供的翻譯品質通常會得到改善。
- 錯誤物件索引鍵已重新命名，以讓它們與其他 Watson API 一致。`error_code` 已重新命名為 `code`，而 `error_message` 已重新命名為 `error`。

### IAM 鑑別

自 2018 年 6 月 12 日開始，在雪梨和美國東部地區建立的新服務實例會使用 [Identityand Access Management (IAM) 鑑別](#iam-auth-process)。

## 2018 年 1 月 12 日
{: #12-january-2018}

新的「神經機器翻譯 (NMT)」模型可供預覽。您可對下列語言配對嘗試 NMT 模型。 

- 英文與後述語言的相互翻譯：阿拉伯文、中文、荷蘭文、法文、德文、義大利文、日文、韓文、波蘭文、葡萄牙文（巴西）、俄文、西班牙文，以及土耳其文
- 法文與後述語言的相互翻譯：德文、西班牙文
- 德文與後述語言的相互翻譯：義大利文

*NMT 模型及使用它們的語法在預覽期間可能會有所變更。目前，NMT 模型不支援語料庫的自訂。僅支援強制名詞解釋的自訂。*

若要使用 NMT 預覽來翻譯，請指定標頭 `X-Watson-Technology-Preview:2017-07-01`，以及您想要使用的模型之來源與目標語言的字元碼。下列範例顯示如何使用 NMT 模型，將英文翻譯為西班牙文。

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}

您可以在 YouTube 觀看[視訊逐步演練 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://youtu.be/L6ZC0QaUZ2k)，其中說明如何使用 NMT 預覽來設定 {{site.data.keyword.languagetranslatorshort}}。


## 2016 年 12 月 15 日
{: #15-december-2016}

已新增其他的新聞翻譯模型：英文與日文的相互翻譯

## 2016 年 11 月 15 日
{: #15-november-2016}

不再提供或支援先前可供 {{site.data.keyword.languagetranslatorshort}} 服務使用的工具。 

請與業務代表或客戶支援中心聯絡，以取得如何使用 {{site.data.keyword.languagetranslatorshort}} API 來達成 {{site.data.keyword.languagetranslatorshort}} 工具所支援之作業的相關資訊。

## 2016 年 9 月 1 日
{: #1-september-2016}

IBM Watson&trade; Language Translation 服務已改名為 {{site.data.keyword.languagetranslatorshort}} 服務。

## 2016 年 3 月 22 日
{: #22-march-2016}

已新增其他語言的支援：英文與義大利文的相互翻譯，以及西班牙文與法文的相互翻譯。

## 2015 年 12 月 3 日
{: #3-december-2015}

從 2016 年 1 月 15 日開始，「標準方案」內的所有自訂作業功能均已停止使用。未使用自訂作業功能的應用程式不需要變更，因為「標準方案」對於與自訂作業或自訂模型不相關的所有 API 仍然有效。若要使用 {{site.data.keyword.languagetranslatorshort}} 服務的 GA 自訂作業功能（「可訓練」方案），與使用舊版服務實例的 {{site.data.keyword.cloud}} 應用程式搭配，請完成下列步驟：

1.  建立新的 Watson {{site.data.keyword.languagetranslatorshort}} 實例，並指定 GA「可訓練」方案。
2.  將新的「可訓練」服務實例連結至 {{site.data.keyword.cloud_notm}} 中的應用程式。
3.  收集用來起始建立自訂模型的資料。如需相關資訊，請參閱[訓練資料的結構](/docs/services/language-translator?topic=language-translator-customizing#structure)。
4.  上傳訓練資料，以在「可訓練」實例上建立新的自訂模型。如需相關資訊，請參閱[訓練自訂翻譯模型](/docs/services/language-translator?topic=language-translator-customizing#training)。
5.  在應用程式中，將「模型 ID」指向新的自訂模型。
6.  從 {{site.data.keyword.cloud_notm}} 中的應用程式取消連結舊版服務，然後將其刪除。

## 2015 年 11 月 6 日
{: #6-november-2015}

{{site.data.keyword.languagetranslatorshort}} 工具測試版已釋出。此工具是一種 Web 應用程式，其會提供圖形使用者介面，來管理並訓練模型，以取得更加精確的機器翻譯。您可以建立專案、上傳訓練資料、訓練自訂模型，以及翻譯文字。

## 2014 年 12 月 1 日
{: #1-december-2014}

測試版 Machine Translator及測試版 Language Identification API 已升級，並結合至 {{site.data.keyword.languagetranslatorshort}} API。若要立即開始使用新服務，請瞭解並更新您的程式碼，以反映這些變更：

- **New model\_id 參數**：在測試版 API 中，您已定義 `sid` 參數來選取要用於翻譯的模型。在此版本中，`sid` 參數重新命名為 `model_id` 參數。若要擷取 `model_id` 容許的值，請使用 `GET/language  translator/api/v2/models` 作業。這會傳回一個清單，列出所有模型及其對應 `model_id` 值。
- **語言配對支援**：不是選取 `model_id`，而是您現在可以指定來源及目標語言，而且模型將預設為在一般新聞領域上訓練的模型。
- **JSON 要求內文支援**：現在，提出 POST 翻譯要求時，您可用 JSON 提交形式提出要求。JSON 格式可讓您提交多個段落進行翻譯，而不只是表單提交格式中的單一文字片段。
- **JSON 回應內文支援**：翻譯要求會傳回支援的 JSON 格式，以及純文字格式。JSON 格式可支援在多個段落而不是單一文字片段中傳回已翻譯的文字。
- **Accept 標頭支援**：accept 標頭現在可以用來定義所有作業中的回應格式（text/plain 或 application/json）。
- **語言識別支援**：語言識別方法已新增至此 API。這可讓您識別輸入文字的語言，以及列出 API 可以偵測的所有支援語言。

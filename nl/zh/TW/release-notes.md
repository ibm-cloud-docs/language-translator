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

# 版本注意事項

下列新增特性及服務的變更可供使用。
{: shortdesc}

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
1.  將新的「可訓練」服務實例連結至 {{site.data.keyword.cloud_notm}} 中的應用程式。
1.  收集用來起始建立自訂模型的資料。如需相關資訊，請參閱[訓練資料的結構](/docs/services/language-translator/customizing.html#structure)。
1.  上傳訓練資料，以在「可訓練」實例上建立新的自訂模型。如需相關資訊，請參閱[訓練自訂翻譯模型](/docs/services/language-translator/customizing.html#training)。
1.  在應用程式中，將「模型 ID」指向新的自訂模型。
1.  從 {{site.data.keyword.cloud_notm}} 中的應用程式取消連結舊版服務，然後將其刪除。

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


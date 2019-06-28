---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-04"

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

# 資訊安全
{: #information-security}

IBM 致力於為我們的客戶和夥伴提供創新的資料隱私權、安全及控管解決方案。
{: shortdesc}

**注意事項：**客戶須負責確定本身遵循各種法令規章，包括「歐盟一般資料保護規範」。有關任何可能影響「客戶」業務之相關法令規章之確認與解釋，以及任何「客戶」為遵循該等法令規章所需採取之行動，「客戶」應自行負責向法律顧問取得諮詢意見。

本文所述的產品、服務及其他功能並不適合所有「客戶」情況，其可用性可能受限。IBM 不提供法律、會計或審核意見，亦不聲明或保證其服務或產品可確保「客戶」遵循任何法令規章。

如果您需要針對建立的 {{site.data.keyword.cloud}} {{site.data.keyword.watson}} 資源要求 GDPR 支援：

-   在歐盟 (EU)，請參閱[要求在歐盟建立之 IBM Cloud Watson 資源的支援](/docs/services/watson/getting-started-gdpr-sar.html#request-EU)。
-   在歐盟以外地區，請參閱[要求歐盟以外資源的支援](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU)。

## 歐盟一般資料保護法規 (GDPR)
{: #gdpr}

IBM 致力於為我們的客戶和夥伴提供創新的資料隱私權、安全及控管解決方案，以協助他們邁向 GDPR 合規性。

進一步瞭解 IBM 對 GDPR 準備的行程，以及我們的 GDPR 功能及產品與服務，以支援您遵循法規 [這裡 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](../../icons/launch-glyph.svg "外部鏈結圖")](http://www.ibm.com/gdpr){: new_window}.

## 標示及刪除 Language Translator 中的資料
{: #gdpr-in-service}

{{site.data.keyword.languagetranslatorshort}} 服務會暫時快取翻譯要求中的翻譯資料，並儲存用來建立自訂模型的訓練資料。

### 翻譯資料和文件
{: #translation-data-and-documents}

當您將文件傳送至**翻譯**方法中的 {{site.data.keyword.languagetranslatorshort}} 時，服務會快取來源文字和翻譯結果，以在後續的**翻譯**要求中接收到相同文字時改善效能。一旦 15 天未使用快取的翻譯文字，就會將其刪除。

透過**翻譯文件**方法提交給服務進行翻譯的文件會儲存在內部以提供已翻譯的檔案，並會藉由參照原始上傳的文件來支援其他**翻譯文件**要求。一旦後續的**翻譯文件**要求 15 天未使用原始文件和任何關聯的已翻譯文件，就會將其刪除。**刪除文件**方法可以用來在刪除截止時間之前刪除文件。 

翻譯資料和文件採取進行中加密和靜態加密。

### 自訂模型訓練資料
{: #custom-model-training-data}

訓練自訂模型時，會儲存您用來建立模型的訓練資料，以提供您自訂模型。自訂模型和訓練資料採取進行中加密和靜態加密。已加密的訓練資料會持續保存在儲存空間中，直到使用**刪除模型**方法刪除模型為止。

只能在模型層次刪除自訂模型。無法刪除用來建立自訂模型的元件資料。如果您在建立自訂模型時使用個人資料，則必須針對每個客戶建立個別的自訂模型，並標示模型 `name` 來識別客戶，以在要求時將其刪除。 

---

copyright:
  years: 2019
lastupdated: "2019-03-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# 高可用性與災難回復
{: #ha-dr}

{{site.data.keyword.languagetranslatorfull}} 在多個 {{site.data.keyword.cloud_notm}} 位置（例如，達拉斯和華盛頓特區）內高度使用。不過，從影響整個位置的潛在災難回復需要規劃和準備。
{: shortdesc}

您要負責瞭解服務的配置、自訂作業和使用。同時負責備妥以在新位置重建服務實例，以及在任何位置還原資料。如需相關資訊，請參閱[如何確保運作零中斷？![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window}。

## 高可用性
{: #high-availability}

{{site.data.keyword.languagetranslatorshort}} 支援沒有單一失敗點的高可用性。服務可以使用 {{site.data.keyword.cloud_notm}} 所提供的多區域地區 (MZR) 特性，來自動並明確地達成高可用性。

{{site.data.keyword.cloud_notm}} 會啟用未在單一位置內共用單一失敗點的多個區域。它也會提供地區內各個區域之間的自動載入平衡。


## 災難回復
{: #disaster-recovery}

如果地區中發生災難性失效，請完成下列步驟。

- 建立新的 {{site.data.keyword.languagetranslatorshort}} 服務實例。
- 調整您的應用軟體來使用新的服務實例 URL 和認證。
- 建立新的自訂模型，來取代您失去的任何自訂模型。請使用您用來建立先前自訂模型的相同強制名詞解釋和平行語料庫。如需自訂模型的相關資訊，請參閱[自訂您的模型](/docs/services/language-translator?topic=language-translator-customizing#customizing)。
  - 若要準備快速回復，每當您建立模型時，就儲存訓練檔案的備份副本。您可以使用自訂模型的 `name` 和 `model_id` 欄位，以及訓練檔案的檔名，來記錄針對每個模型使用的檔案。 
- 調整您的應用軟體來使用新的自訂模型。


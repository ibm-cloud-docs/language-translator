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

# 機密保護
{: #information-security}

IBM は、お客様やパートナーに、データ・プライバシー、セキュリティー、およびガバナンスに関する革新的なソリューションを提供することに努めています。
{: shortdesc}

**注意:**
お客様自身が欧州連合の一般データ保護規則を含む各種法令を遵守するために必要な措置を講ずるのはお客様の責任です。 お客様のビジネスに影響を及ぼす可能性のある関連法令の特定およびそれらの解釈、ならびにかかる関連法令を遵守するためにお客様が講ずるべき必要措置に関する助言は、お客様の責任により適格な弁護士から得るものとします。

本書に記載の製品、サービス、および他の機能が、すべてのお客様の状況に適しているとは限らず、使用する際に制約を受ける場合があります。 IBM は、法律、会計または監査に関する助言を提供することはしませんし、IBM のサービスまたは製品が、お客様のあらゆる法令遵守の裏付けとなる表明または保証もいたしません。

以下の場所で作成された {{site.data.keyword.cloud}} {{site.data.keyword.watson}} リソースの GDPR サポートを要請する必要がある場合の手順

-   EU 内の場合、[EU で作成された IBM Cloud Watson リソースのサポートの要求 (Requesting support for IBM Cloud Watson resources created in the European Union)](/docs/services/watson/getting-started-gdpr-sar.html#request-EU) を参照してください。
-   EU 外のリソースについては、[EU 外にあるリソースについてのサポートの要求](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU)を参照してください。

## EU 一般データ保護規則 (GDPR)
{: #gdpr}

IBM は、お客様やパートナーに、データ・プライバシー、セキュリティー、およびガバナンスに関する革新的なソリューションを提供して、GDPR  に対する準拠が完了するまでの過程を支援することに努めています。

GDPR に対する準備を整えるための IBM 独自の過程と、準拠が完了するまでの過程をサポートする弊社の GDPR 機能とオファリングについて詳しくは、[ここ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.ibm.com/gdpr){: new_window} を参照してください。

## Language Translator でのデータのラベル付けと削除
{: #gdpr-in-service}

{{site.data.keyword.languagetranslatorshort}} サービスは翻訳要求から翻訳データを一時的にキャッシュし、カスタム・モデルの作成に使われるトレーニング・データを保管します。

### 翻訳データと文書
{: #translation-data-and-documents}

**「翻訳」**メソッドでテキストを {{site.data.keyword.languagetranslatorshort}} に送信するとき、サービスはソース・テキストと翻訳結果をキャッシュします。これにより、後続の**「翻訳」**要求で同じテキストを受信した場合のパフォーマンスが向上します。キャッシュされた翻訳テキストは、15 日間使用されなかった場合にのみ削除されます。

翻訳用に**「文書の翻訳 (Translate document)」**メソッドでサービスに送信された文書は、内部的に保管されます。これにより翻訳済みファイルが提供され、元のアップロード済み文書を参照することで追加の**「文書の翻訳 (Translate document)」**要求がサポートされます。元の文書および関連する翻訳済み文書は、後続の**「文書の翻訳 (Translate document)」**要求で 15 日間使用されなかった場合にのみ削除されます。削除の期限より前に文書を削除するには、**「文書の削除 (Delete document)」**メソッドを使用できます。 

翻訳データと文書は、転送中および保存時に暗号化されます。

### カスタム・モデルのトレーニング・データ
{: #custom-model-training-data}

カスタム・モデルをトレーニングすると、モデルの作成に使用するトレーニング・データが保管され、カスタム・モデルが提供されます。カスタム・モデルとトレーニング・データは、転送中および保存時に暗号化されます。暗号化されたトレーニング・データは、**「モデルの削除 (Delete model)」**メソッドでモデルが削除されるまでストレージに保持されます。

カスタム・モデルは、モデル・レベルでのみ削除できます。カスタム・モデルの作成に使われたコンポーネント・データを削除することはできません。カスタム・モデルの作成時に個人データを使用する場合は、お客様ごとに別々のカスタム・モデルを作成し、要求に応じて削除できるように、お客様を識別するモデル `name` のラベルを付ける必要があります。 

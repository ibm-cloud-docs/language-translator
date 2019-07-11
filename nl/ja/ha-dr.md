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

# 高可用性と災害復旧
{: #ha-dr}

{{site.data.keyword.languagetranslatorfull}} は、複数の {{site.data.keyword.cloud_notm}} ロケーション (例えばダラスとワシントン DC) 内で高可用性を実現します。ただし、ロケーション全体が影響を受けるような災害から復旧するためには、計画と準備が必要です。
{: shortdesc}

サービスの構成、カスタマイズ、使用法を把握しておく必要があります。 さらに、新しいロケーションでサービスのインスタンスを再作成してすべてのロケーションのデータを復元できるように、準備しておく必要もあります。詳しくは、[ゼロ・ダウン時間を確実に実現するにはどうすればよいですか? ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} を参照してください。

## 高可用性
{: #high-availability}

{{site.data.keyword.languagetranslatorshort}} は、単一障害点のない高可用性をサポートしています。このサービスは、{{site.data.keyword.cloud_notm}} に用意されている複数ゾーン地域 (MZR) 機能を使用して、高可用性を自動的かつ透過的に実現します。

{{site.data.keyword.cloud_notm}} では、1 つのロケーションの中で、単一障害点を共有しない複数のゾーンを利用できます。 1 つの地域の複数のゾーン間で自動的に負荷分散を行うこともできます。


## 災害復旧
{: #disaster-recovery}

ある地域で壊滅的な障害が発生した場合は、以下の手順に従ってください。

- 新規 {{site.data.keyword.languagetranslatorshort}} サービス・インスタンスを作成します。
- 新規サービス・インスタンスの URL と資格情報を使用するようにアプリケーション・ソフトウェアを調整します。
- 失われたものを置き換えるための新規カスタム・モデルを作成します。以前のカスタム・モデルを作成した際に使用したものと同じ強制グロッサリーおよび並列コーパスを使用します。カスタム・モデルについて詳しくは、[モデルのカスタマイズ](/docs/services/language-translator?topic=language-translator-customizing#customizing)を参照してください。
  - 迅速な復旧の準備をするために、モデルの作成時には常にトレーニング・ファイルのバックアップ・コピーを保管します。カスタム・モデルの `name` フィールドと `model_id` フィールドおよびトレーニング・ファイルのファイル名を使用して、各モデルに使用するファイルの記録を残すことができます。 
- 新規カスタム・モデルを使用するようにアプリケーション・ソフトウェアを調整します。


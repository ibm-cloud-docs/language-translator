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

# 高可用性和灾难恢复
{: #ha-dr}

{{site.data.keyword.languagetranslatorfull}} 在多个 {{site.data.keyword.cloud_notm}} 位置（例如，达拉斯和华盛顿）具有高可用性。但是，要从影响整个位置的潜在灾难中恢复，需要进行规划和准备。
{: shortdesc}

您负责了解服务的配置、定制和使用情况。您还负责准备好在新位置重新创建该服务的实例，并在任何位置复原数据。有关更多信息，请参阅[如何确保停机时间为零？![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window}。

## 高可用性
{: #high-availability}

{{site.data.keyword.languagetranslatorshort}} 支持高可用性，没有单点故障。该服务使用 {{site.data.keyword.cloud_notm}} 提供的多专区区域 (MZR) 功能，自动、透明地实现高可用性。

{{site.data.keyword.cloud_notm}} 支持单个位置中的多个专区不分担单点故障。它还在一个区域中的各个专区之间提供自动负载均衡。


## 灾难恢复
{: #disaster-recovery}

如果区域发生灾难性故障，请完成以下步骤。

- 创建新的 {{site.data.keyword.languagetranslatorshort}} 服务实例。
- 调整应用程序软件以使用新的服务实例 URL 和凭证。
- 创建新的定制模型以替换丢失的任何模型。使用创建先前定制模型所用的相同特殊词汇表和平行语料库。有关定制模型的更多信息，请参阅[定制模型](/docs/services/language-translator?topic=language-translator-customizing#customizing) 。
  - 要为快速恢复做好准备，请在每次创建模型时存储训练文件的备份副本。可以将定制模型的 `name` 和 `model_id` 字段与训练文件的文件名一起使用，以保留用于每个模型的文件的记录。 
- 调整应用程序软件以使用新的定制模型。


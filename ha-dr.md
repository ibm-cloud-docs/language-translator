---

copyright:
  years: 2019, 2023
lastupdated: "2023-05-03"

subcollection: language-translator

---

{{site.data.keyword.attribute-definition-list}}

# High availability and disaster recovery
{: #ha-dr}

IBM is announcing the deprecation of the {{site.data.keyword.languagetranslatorfull}} service for {{site.data.keyword.cloud}} in all regions. As of 10 June 2023, the {{site.data.keyword.languagetranslatorshort}} tile will be removed from the {{site.data.keyword.cloud_notm}} Platform for new customers; only existing customers will be able to access the product. As of 10 June 2024, the service will reach its End of Support date. As of 10 December 2024, the service will be withdrawn entirely and will no longer be available to any customers.
{: deprecated}

{{site.data.keyword.languagetranslatorfull}} is highly available within multiple {{site.data.keyword.cloud_notm}} locations (for example, Dallas and Washington, DC). However, recovering from potential disasters that affect an entire location requires planning and preparation.
{: shortdesc}

You are responsible for understanding your configuration, customization, and usage of the service. You are also responsible for being ready to re-create an instance of the service in a new location and to restore your data in any location. Fore more information, see [How IBM Cloud ensures high availability and disaster recovery](/docs/overview?topic=overview-zero-downtime){: external}.

## High availability
{: #high-availability}

{{site.data.keyword.languagetranslatorshort}} supports high availability with no single point of failure. The service achieves high availability automatically and transparently by using the multi-zone region (MZR) feature provided by {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} enables multiple zones that do not share a single point of failure within a single location. It also provides automatic load balancing across the zones within a region.


## Disaster recovery
{: #disaster-recovery}

In the event of a catastrophic failure in a region, complete the following steps.

-   Create a new {{site.data.keyword.languagetranslatorshort}} service instance.
-   Adjust your application software to use the new service instance URL and credentials.
-   Create new custom models to replace any that you lost. Use the same forced glossaries and parallel corpora that you used to create your previous custom models. See [Customizing your model](/docs/language-translator?topic=language-translator-customizing#customizing) for more information about custom models.
    -   To prepare for a quick recovery, store backup copies of your training files whenever you create a model. You can use the `name` and `model_id` fields of your custom models along with the filenames of your training files to keep a record of the files that you use for each model.
-   Adjust your application software to use the new custom models.

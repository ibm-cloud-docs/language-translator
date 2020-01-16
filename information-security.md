---

copyright:
  years: 2015, 2020
lastupdated: "2020-01-16"

subcollection: language-translator

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Information security
{: #information-security}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions.
{: shortdesc}

**Notice:**
Clients are responsible for ensuring their own compliance with various laws and regulations, including the European Union General Data Protection Regulation. Clients are solely responsible for obtaining advice of competent legal counsel as to the identification and interpretation of any relevant laws and regulations that may affect the clients’ business and any actions the clients may need to take to comply with such laws and regulations.

The products, services, and other capabilities described herein are not suitable for all client situations and may have restricted availability. IBM does not provide legal, accounting or auditing advice or represent or warrant that its services or products will ensure that clients are in compliance with any law or regulation.

If you need to request GDPR support for {{site.data.keyword.cloud}} {{site.data.keyword.watson}} resources that are created

-   In the European Union (EU), see [Requesting support for IBM Cloud Watson resources created in the European Union](/docs/services/watson/getting-started-gdpr-sar.html#request-EU).
-   Outside of the EU, see [Requesting support for resources outside the European Union](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU).

## European Union General Data Protection Regulation (GDPR)
{: #gdpr}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions to assist them on their journey to GDPR compliance.

Learn more about IBM's own GDPR readiness journey and our GDPR capabilities and offerings to support your compliance journey [here](http://www.ibm.com/gdpr){: external}.

## Health Insurance Portability and Accountability Act (HIPAA)
{: #hipaa}

US Health Insurance Portability and Accountability Act (HIPAA) support is available for Premium plans in the Washington, DC location created on or after 1 April 2019. See [Enabling EU and HIPAA supported settings](/docs/account?topic=account-eu-hipaa-supported#eu-hipaa-supported){: external} for more information.

## Labeling and deleting data in Language Translator
{: #gdpr-in-service}

The {{site.data.keyword.languagetranslatorshort}} service temporarily caches translation data from translation requests and stores training data that is used to create custom models.

### Translation data and documents
{: #translation-data-and-documents}

When you send text to {{site.data.keyword.languagetranslatorshort}} in the **Translate** method, the service caches the source text and the translation result to improve performance when it receives the same text in subsequent **Translate** requests. Cached translation text is deleted only after it is not used for a period of 15 days.

Documents that are submitted to the service for translation through the **Translate document** method are stored internally to provide the translated file, and to support additional **Translate document** requests by reference to the original uploaded document. The original document and any associated translated documents are deleted only after they are not used in subsequent **Translate document** requests for a period of 15 days. The **Delete document** method can be used to delete documents before the deletion deadline.

Translation data and documents are encrypted in flight and at rest.

### Custom model training data
{: #custom-model-training-data}

When you train a custom model, the training data that you use to create the model is stored to provide you with the custom model. Custom models and training data are encrypted in flight and at rest. The encrypted training data persists in storage until the model is deleted with the **Delete model** method.

Custom models can only be deleted at the model level. Component data used to create a custom model cannot be deleted. If you use personal data when creating a custom model, a separate custom model must be created for each customer and the model `name` labeled to identify the customer so it can be deleted if requested.

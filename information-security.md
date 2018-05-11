---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-11"

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

# Information security
{: #information-security}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions.
{: shortdesc}

**Notice:**
Clients are responsible for ensuring their own compliance with various laws and regulations, including the European Union General Data Protection Regulation. Clients are solely responsible for obtaining advice of competent legal counsel as to the identification and interpretation of any relevant laws and regulations that may affect the clients’ business and any actions the clients may need to take to comply with such laws and regulations.

The products, services, and other capabilities described herein are not suitable for all client situations and may have restricted availability. IBM does not provide legal, accounting or auditing advice or represent or warrant that its services or products will ensure that clients are in compliance with any law or regulation.

## European Union General Data Protection Regulation (GDPR)
{: #gdpr}

IBM is committed to providing our clients and partners with innovative data privacy, security and governance solutions to assist them on their journey to GDPR compliance.

Learn more about IBM's own GDPR readiness journey and our GDPR capabilities and offerings to support your compliance journey [here ![External link icon](../../icons/launch-glyph.svg "External link icon")](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/gdpr){: new_window}.

## Labeling and deleting data in Language Translator
{: #gdpr-in-service}

The {{site.data.keyword.languagetranslatorshort}} service temporarily caches translation data from translation requests and stores training data that is used to create custom models.

### Translation data

When you send text to {{site.data.keyword.languagetranslatorshort}} in the **Translate** method, the service caches the source text and the translation result to improve performance when it receives the same text in subsequent **Translate** requests. Cached translation text is deleted only after it is not used for a period of 15 days.

### Custom model training data

When you train a custom model, the training data that you use to create the model is stored to provide you with the custom model. The training data persists in storage until the model is deleted with the **Delete model** method.

Custom models can only be deleted at the model level. Component data used to create a custom model cannot be deleted. If you use personal data when creating a custom model, a separate custom model must be created for each customer and the model `name` labeled to identify the customer so it can be deleted if requested.

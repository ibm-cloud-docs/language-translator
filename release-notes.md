---

copyright:
  years: 2015, 2020
lastupdated: "2020-02-06"

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

# Release notes

The following new features and changes to the service are available.
{: shortdesc}

## New API authentication process
{: #iam-auth-process }

The {{site.data.keyword.languagetranslatorshort}} service has a new API authentication process for service instances that are hosted in the following locations:

- Dallas as of June 15, 2018
- Frankfurt as of June 15, 2018
- London
- Seoul
- Sydney as of June 12, 2018
- Tokyo
- Washington, DC as of June 12, 2018

{{site.data.keyword.cloud_notm}} is migrating to token-based Identity and Access Management (IAM) authentication. With some service instances, you authenticate to the API by using IAM.

- For _new_ service instances created in the locations indicated previously, you use IAM for authentication. You can pass either a bearer token or an API key. Tokens support authenticated requests without embedding service credentials in every call. API keys use basic authentication.

    When you use any of the Watson SDKs, you can pass the API key and let the SDK manage the lifecycle of the tokens. For more information and examples, see [Authentication](https://cloud.ibm.com/apidocs/language-translator#authentication){: external} in the API reference.
- For _existing_ service instances that you created before the indicated date, you continue to authenticate by providing the username and password for the service instance. Eventually, you will need to migrate these service instances to IAM authentication. Updates will be provided about migration process and dates. For more information about migration, see [Migrating Cloud Foundry service instances to a resource group](/docs/resources?topic=resources-migrate#migrate).

To find out which authentication to use, view the service credentials by clicking the service instance on the [{{site.data.keyword.cloud_notm}} resources page](https://cloud.ibm.com/resources){: external}.

## Service API Versioning
{: shortdesc}

API requests in {{site.data.keyword.languagetranslatorshort}} v3 require a version parameter that takes a date in the format `version=YYYY-MM-DD`. Whenever we change the API in a backwards-incompatible way, we release a new minor version of the API.

Send the version parameter with every API request. The service uses the API version for the date you specify, or the most recent version before that date. Don't default to the current date. Instead, specify a date that matches a version that is compatible with your app, and don't change it until your app is ready for a later version.

The current version is `2018-05-01`.

## 28 February 2020
{: #28-february-2020}

Added automatic source language detection in **Translate** requests. When you specify a target language without specifying a source language or translation model, the service attempts to identify the source language and continues with the translation. In the results, the service returns the identified language and a score indicating the confidence in the identification.

## 30 January 2020
{: #30-january-2020}

- New [translation models](/docs/language-translator?topic=language-translator-translation-models) are now available.
  - English to and from Latvian (`en-lv` and `lv-en`)
  - English to and from Urdu (`en-ur` and `ur-en`)
  - English to and from Vietnamese (`en-vi` and `vi-en`)
- General improvements for translating PowerPoint and Word documents.

## 12 December 2019
{: #12-december-2019}

- **Full support for IBM Cloud IAM**

    - {{site.data.keyword.languagetranslatorshort}} now supports the full implementation of {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). API keys for Watson services are no longer limited to a single service instance. You can create access policies and API keys that apply to more than one service, and you can grant access between services.
    - To support this change, the API service endpoints use a different domain and include the service instance ID. The pattern is `api.{location}.{offering}.watson.cloud.ibm.com/instances/{instance_id}`.

        Example URL for an instance hosted in the Dallas location: `api.us-south.language-translator.watson.cloud.ibm.com/instances/6bbda3b3-d572-45e1-8c54-22d6ed9e52c2`

        The previous public endpoint domain was `watsonplatform.net`.

        For more information about the URLs, see the [API reference](https://cloud.ibm.com/apidocs/language-translator/language-translator#service-endpoint){: external}.

        These URLs do not introduce a breaking change. The new URLs work both for your existing service instances and for new instances. The original URLs continue to work on your existing service instances for at least one year (until December 2020).
    - For more information about IAM, see [Authenticating to Watson services](/docs/watson?topic=watson-iam).
- **New network and data security features**
    - **Support for data encryption with customer-managed keys**
        - Users of new premium and dedicated instances can integrate {{site.data.keyword.keymanagementservicefull}} with {{site.data.keyword.languagetranslatorshort}} to encrypt their data and manage encryption keys. For more information, see [Protecting sensitive information in your Watson service](/docs/watson?topic=watson-keyservice).
    - **Support for private network endpoints**
        - Users of Premium plans can create private network endpoints to connect to {{site.data.keyword.languagetranslatorshort}} over a private network. Connections to private network endpoints do not require public internet access. For more information, see [Public and private network endpoints](/docs/watson?topic=watson-public-private-endpoints).

## 13 November 2019
{: #13-november-2019}

- **New South Korea location**: You can now create {{site.data.keyword.languagetranslatorshort}} instances in the Seoul location. As with other locations, the {{site.data.keyword.cloud_notm}} Seoul location uses token-based Identity and Access Management (IAM) authentication.

## 11 November 2019
{: #11-november-2019}

- Improved custom model training time.
- Improved language identification accuracy for English text and for text with more than 100 words.
- New [translation models](/docs/language-translator?topic=language-translator-translation-models) are now available.
  - English to and from Indonesian (`en-id` and `id-en`)
  - English to and from Irish (`en-ga` and `ga-en`)
  - English to and from Lithuanian (`en-lt` and `lt-en`)
  - English to and from Malay (`en-ms` and `ms-en`)
  - English to and from Thai (`en-th` and `th-en`)


## 21 August 2019
{: #21-august-2019}

- New [translation models](/docs/language-translator?topic=language-translator-translation-models) are now available.
  - English to and from Bulgarian (`en-bg` and `bg-en`)
  - English to and from Croatian (`en-hr` and `hr-en`)
  - English to and from Estonian (`en-et` and `et-en`)
  - English to and from Romanian (`en-ro` and `ro-en`)
  - English to and from Slovak (`en-sk` and `sk-en`)
  - English to and from Slovenian (`en-sl` and `sl-en`)
- The following languages can now be identified by the service.
  - Catalan (`ca`)
  - Croatian (`hr`)
  - Irish (`ga`)
  - Malay (`ms`)
  - Maltese (`mt`)
  - Serbian (`sr`)
  - Slovenian (`sl`)
  - Thai (`th`)

## 14 June 2019
{: #14-june-2019}

New [translation models](/docs/language-translator?topic=language-translator-translation-models) are now available for English and Greek.
- English to Greek (en-el)
- Greek to English (el-en)

## 13 June 2019
{: #13-june-2019}

New [translation models](/docs/language-translator?topic=language-translator-translation-models) are now available for English and Hebrew.
- English to Hebrew (en-he)
- Hebrew to English (he-en)

## 21 March 2019
{: #21-march-2019}

From March 21 2019, you will see only service credential information associated with the role that has been assigned to your {{site.data.keyword.cloud_notm}} account. For example, if you have assigned a `reader` role, any `writer` or higher levels of service credentials will not be visible.

This change does not affect API access for users or applications with existing service key credentials. Only the viewing of credentials within {{site.data.keyword.cloud_notm}} is affected.

For more information about service keys and user roles, see [IAM service API keys](/docs/watson?topic=watson-api-key-bp#api-key-bp).

## 14 December 2018
{: #14-december-2018}

- You can now create {{site.data.keyword.languagetranslatorshort}} service instances in the {{site.data.keyword.cloud_notm}} London location.

## 16 November 2018
{: #16-november-2018}

- [Translating documents (Beta)](/docs/language-translator?topic=language-translator-translating-documents) is now available through new API endpoints. Submit a Microsoft Office document, PDF, or other document with a supported file format, and {{site.data.keyword.languagetranslatorshort}} will provide a translated copy that preserves the original formatting.
  - [Supported file formats](/docs/language-translator?topic=language-translator-translating-documents#supported-file-types) include `.doc`, `.ppt`, `.pdf`, and more.

- New [translation models](/docs/language-translator?topic=language-translator-translation-models) for Hungarian are now available:
  - Hungarian to English (hu-en)
  - English to Hungarian (en-hu)

## 8 November 2018
{: #8-november-2018}

- You can now create {{site.data.keyword.languagetranslatorshort}} service instances in the {{site.data.keyword.cloud_notm}} Tokyo location.

## 9 August 2018
{: #9-august-2018}

New [translation models](/docs/language-translator?topic=language-translator-translation-models) for Norwegian Bokmål are now available:
  - Norwegian Bokmål to English (nb-en)
  - English to Norwegian Bokmål (en-nb)

## 27 June 2018
{: #27-june-2018}

New [translation models](/docs/language-translator?topic=language-translator-translation-models) that feature six new languages are now available:
  - Catalan
    - Catalan to Spanish (ca-es)
    - Spanish to Catalan (es-ca)
  - Czech
    - Czech to English (cs-en)
    - English to Czech (en-cs)
  - Danish
    - Danish to English (da-en)
    - English to Danish (en-da)
  - Finnish
    - Finnish to English (fi-en)
    - English to Finnish (en-fi)
  - Hindi
    - Hindi to English (hi-en)
    - English to Hindi (en-hi)
  - Swedish
    - Swedish to English (sv-en)
    - English to Swedish (en-sv)
  

## 15 June 2018
{: #15-june-2018}

As of 15 June 2018, new service instances created in the Germany and US South regions use [Identity and Access Management (IAM) authentication](#iam-auth-process).

New service instances that you create in Germany and US South will not be compatible with Language Translator v2. If you use Language Translator v2 and are planning to use new service instances in your application, you will need to [migrate to the v3 API](/docs/language-translator?topic=language-translator-migrating).

## 12 June 2018
{: #12-june-2018}

{{site.data.keyword.languagetranslatorshort}} v3 is now available. The v2 Language Translator API will no longer be available after July 31, 2018. To take advantage of the latest service enhancements, migrate to the v3 API. View the [Migrating to Language Translator v3](/docs/language-translator?topic=language-translator-migrating) page for more information.

### What's new in v3
{: #whats-new}

-  {{site.data.keyword.languagetranslatorshort}} API v3 comes with **Neural Machine Translation** (NMT) models that offer significantly improved translation results. All NMT models are now available for customization.
-  Use custom models as base models for forced glossary customization.
-  API v3 is a simplified, all-JSON subset of the retired API v2.
-  Introduces API version dates to give developers the freedom to adopt future API changes at their own pace.

### Breaking changes
{: #breaking-changes}

- Mandatory version date for all API endpoints: API v3 requests require a version date query parameter of the form `version=YYYY-MM-DD`. The latest API version is `version=2018-05-01`.
- Simplified API:
  - The **Translate** and **Identify** methods do not offer the option to return plain text responses in v3. The methods return only JSON responses.
  - `GET /translate` and `GET /identify` methods are not supported in v3. Use the `POST /translate` and `POST /identify` methods instead. 
- Monolingual corpus customization is not supported in v3.
- Creating custom models with both a parallel corpus and forced glossary now needs to be done in two API calls. First, customize the model with a parallel corpus. After the custom model has finished training, customize it again with the forced glossary. This change allows you to use a custom model trained with a parallel corpus as a base for forced glossary customization.
- Specialized patent and conversation domain models are not available in the v3 API. The translation quality provided by the NMT models in the patent and conversation domains is generally improved compared to the older specialized models.
- Error object keys have been renamed so that they are consistent with other Watson APIs. `error_code` has been renamed to `code`, and `error_message` has been renamed to `error`.

### IAM authentication

As of 12 June 2018, new service instances created in the Sydney and US East regions use [Identity and Access Management (IAM) authentication](#iam-auth-process).

## 12 January 2018
{: #12-january-2018}

New Neural Machine Translation (NMT) models are available to preview. You can try NMT models for the following language pairs. 

- English to and from: Arabic, Chinese, Dutch, French, German, Italian, Japanese, Korean, Polish, Portuguese (Brazilian), Russian, Spanish, and Turkish
- French to and from: German, Spanish
- German to and from: Italian

*The NMT models and the syntax for using them are subject to change during the preview period. Currently, NMT models do not support corpus customization. Only forced glossary customization is supported.*

To use an NMT preview model to translate, specify the header `X-Watson-Technology-Preview:2017-07-01` along with the character codes for the source and target languages of the model you want to use. The following example shows how to translate English to Spanish with an NMT preview model.

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}

You can watch a [video walkthrough on YouTube](https://youtu.be/L6ZC0QaUZ2k) that explains how to set up {{site.data.keyword.languagetranslatorshort}} with the NMT preview.

## 15 December 2016
{: #15-december-2016}

Additional News translation models were added: English to and from Japanese

## 15 November 2016
{: #15-november-2016}

The tooling that was previously available for the {{site.data.keyword.languagetranslatorshort}} service is no longer available or supported. 

Contact your sales representative or customer support for information about how to use the {{site.data.keyword.languagetranslatorshort}} API to accomplish the tasks supported by the {{site.data.keyword.languagetranslatorshort}} tool.

## 1 September 2016
{: #1-september-2016}

The IBM Watson&trade; Language Translation service was rebranded as the {{site.data.keyword.languagetranslatorshort}} service.

## 22 March 2016
{: #22-march-2016}

Support for additional languages was added: English to and from Italian, and Spanish to and from French.

## 3 December 2015
{: #3-december-2015}

As of January 15, 2016, all customization capabilities within the Standard Plan are discontinued. Applications that do not use customization features do not need to change, as the Standard Plan remains active for all API calls unrelated to customization or customized models. To use the GA customization features (the Trainable plan) of the {{site.data.keyword.languagetranslatorshort}} service with an {{site.data.keyword.cloud}} application that uses an earlier instance of the service, complete the following steps:

1.  Create a new Watson {{site.data.keyword.languagetranslatorshort}} instance and specify the GA "Trainable" plan.
2.  Bind the new "Trainable" instance of the service to your app in {{site.data.keyword.cloud_notm}}.
3.  Gather the data that was used to initially create the customized models. For more information, see [Structure of the training data](/docs/language-translator?topic=language-translator-customizing#structure).
4.  Upload the training data to create new customized models on the "Trainable" instance. For more information, see [Training a custom translation model](/docs/language-translator?topic=language-translator-customizing#training).
5.  In your app, point the "ModelID" field to the new customized models.
6.  Unbind the earlier service from your app in {{site.data.keyword.cloud_notm}}, and then delete it.

## 6 November 2015
{: #6-november-2015}

The {{site.data.keyword.languagetranslatorshort}} tool beta is released. The tool is a web application that provides a graphical user interface to manage and train models for more accurate machine translation. You can create projects, upload training data, train custom models, and translate text.

## 1 December 2014
{: #1-december-2014}

The beta Machine Translator and beta Language Identification APIs have been upgraded and combined into the {{site.data.keyword.languagetranslatorshort}} API. To immediately start using the new service, understand and update your code to reflect these changes:

- **New model\_id parameter**: In the beta API, you defined the `sid` parameter to select the model to use for translation. In this version, the `sid` parameter is renamed to `model_id` parameter. To retrieve the `model_id` allowed values, use the `GET/language  translator/api/v2/models` operation. This returns a list of all models and their corresponding `model_id` values.
- **Language pair support**: Instead of selecting a `model_id`, you can now specify a source and target language instead, and the model will default to the one that's trained on the general news domain.
- **JSON request body support**: When making a POST translation request, you can now make the request as a JSON submission. The JSON formatting allows you to submit multiple paragraphs for translation, instead of just a single piece of text in the form submission format.
- **JSON response body support**: The translation request returns support JSON formatting as well as plain text formatting. The JSON format allows support for the translated words to be returned in multiple paragraphs instead of a single piece of text.
- **Accept header support**: The accept header can now be used to define the format of the response in all of the operations (text/plain or application/json).
- **Language Identification support**: Language identification methods have been added to this API. This allows you to identify the language of the input texts, and lists all supported languages that can be detected by the API.

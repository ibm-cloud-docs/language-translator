---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-18"

keywords: language translator release notes

subcollection: language-translator

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for Language Translator
{: #release-notes}

The following new features and changes to the service are available.
{: shortdesc}

## Service API Versioning
{: #versioning}

API requests in {{site.data.keyword.languagetranslatorshort}} v3 require a version parameter that takes a date in the format `version=YYYY-MM-DD`. Whenever we change the API in a backwards-incompatible way, we release a new minor version of the API.

Send the version parameter with every API request. The service uses the API version for the date you specify, or the most recent version before that date. Don't default to the current date. Instead, specify a date that matches a version that is compatible with your app, and don't change it until your app is ready for a later version.

The current version is `2018-05-01`.

## 18 October 2022
{: #language-translator-18october2022}
{: release-note}

Most of the following changes were made available earlier. They are now documented.
{: note}

New translation limits for Advanced and Premium plans
:   The translation limits for service instances on the Advanced and Premium plans have increased. The **Translate document** method now enforces a document size limit of **50 MB** for instances on the Advanced Plan, and **150 MB** for instances on the Premium plan. The size limits for the Lite and Standard plans remain **2 MB** and **20 MB** respectively. For more information, see [Before you begin](/docs/language-translator?topic=language-translator-document-translator-tutorial#translate-prerequisites) in the topic *Translating documents*.

New support for additional subtitle file formats
:   The service now supports additional subtitle formats:
    -   Apple® iTunes® Timed Text (`.itt` files)
    -   Distribution Format Exchange Profile (`.dxfp` and `.xml` files)
    -   Source Code Control (`.scc` files)
    -   Synchronized Accessible Media Interchange (`.sami` and `.smi` files)
    -   SubStation Alpha (`.ssa` files)
    -   Time Text Markup Language (`.ttml` files)

    For more information about all supported file formats, see [Supported file formats](/docs/language-translator?topic=language-translator-document-translator-tutorial#supported-file-formats).

Identifying file formats for translation
:   The service accepts two forms of identification for most file formats. You can identify the format of a file that you send for translation in one of two ways:
    -   By specifying the appropriate file extension for the format.
    -   By specifying the content type (MIME type) of the format as the `type` of the `file` parameter.

    The documentation lists the valid file extensions and content types for each supported format. In most cases, specifying the correct file extension is preferred because it can eliminate ambiguity and is simpler. For subtitles, the documentation makes clear where either the file extension or the content type is needed. For more information about all file formats, their file extensions and content types, and how and when to specify the file extension or content type, see [Supported file formats](/docs/language-translator?topic=language-translator-document-translator-tutorial#supported-file-formats).

Documentation updates for bidirectional translation
:   The documentation now states that the service correctly translates from and to bidirectional languages that are written left-to-right and right-to-left (for example, Arabic, Hebrew, and Urdu). This is not new functionality, but the documentation had failed to emphasize the information.

## 5 August 2022
{: #language-translator-5august2022}
{: release-note}

The following changes were made available on 1 August 2021. They are now documented.
{: note}

Most document formats for translation are now generally available
:   Most supported file formats for document translation are now generally available (GA). In addition, subtitle formats for documentation translation are also GA. The PDF format remains experimental. For more information, see [Supported file formats](/docs/language-translator?topic=language-translator-document-translator-tutorial#supported-file-formats).

## 15 June 2022
{: #language-translator-15june2022}
{: release-note}

The following changes were made available on 1 November 2021. They are now documented.
{: note}

New customizable translation models
:   Added new customizable translation models for the following languages:

    -   English to Kannada (`en-kn`)
    -   English to Marathi (`en-mr`)
    -   English to Punjabi (Indian) (`en-pa`)
    -   English to Punjabi (Pakistani) (`en-pa-PK`)
    -   Kannada to English (`kn-en`)
    -   Marathi to English (`mr-en`)
    -   Punjabi (Indian) to English (`pa-en`)
    -   Punjabi (Pakistani) to English (`pa-PK-en`)

    The Kannada language is new; it is not identifiable. All of the languages except for Kannada already existed and are identifiable. For more information, see [Supported languages for translation](/docs/language-translator?topic=language-translator-translation-models).

Improved customizable translation models
:   Updated the existing customizable translation models for the following languages for improved translation:

    -   Bengali to English (`bn-en`)
    -   Malayalam to English (`ml-en`)
    -   Tamil to English (`ta-en`)
    -   Telugu to English (`te-en`)

    For more information, see [Supported languages for translation](/docs/language-translator?topic=language-translator-translation-models).

## 23 October 2020
{: #language-translator-23october2020}
{: release-note}

New customizable translation models
:   Added improved versions of the following customizable translation models for Korean:

    -   English to Korean (`en-ko`)
    -   Korean to English (`ko-en`)

    The models are improved to preserve markup in the translation if present in the source.

## 16 October 2020
{: #language-translator-16october2020}
{: release-note}

New customizable translation models
:   Added the following customizable translation models for Basque:

    -   Basque to Spanish (`eu-es`)
    -   Spanish to Basque (`es-eu`)

    For more information, see [List of supported languages](/docs/language-translator?topic=language-translator-translation-models#list-languages-supported).

## 25 September 2020
{: #language-translator-25september2020}
{: release-note}

New translation models
:   Added the following translation models for Montenegrin:

    -   Montenegrin to English (`cnr-en`)
    -   English to Montenegrin (`en-cnr`)

    Montenegrin cannot be identified by the service's language identification feature. (Bosnian, Croatian, and Montenegrin translation support is based on the Latin alphabet. Of the three very similar languages, only Croatian is identifiable.) The `cnr-en` and `en-cnr` translation models are not customizable at this time. For more information, see [List of supported languages](/docs/language-translator?topic=language-translator-translation-models#list-languages-supported).

## 16 September 2020
{: #language-translator-16september2020}
{: release-note}

Beta support for subtitle (caption) documents
:   Added beta support for translation of the following subtitle (caption) document formats:

    -   SubRip: `.srt`
    -   SubViewer: `.sbv`
    -   DirectVobSub or VSFilter: `.sub`
    -   MicroDVD: `.sub`
    -   WebVTT: `.vtt`

    These textual formats contain the transcript of a sound track or video source. For more information about the formats and the characteristics of subtitle translation, see [Supported subtitle formats](/docs/language-translator?topic=language-translator-document-translator-tutorial#supported-file-formats-subtitles).

## 14 August 2020
{: #language-translator-14august2020}
{: release-note}

New translation models
:   Added the following translation models:

    -   Bosnian to English (`bs-en`) and English to Bosnian (`en-bs`). Bosnian cannot be identified by the service's language identification feature.
    -   Canadian French to English (`fr-CA-en`) and English to Canadian French (`en-fr-CA`). Canadian French cannot be identified by the service's language identification feature.
    -   English to Welsh (`en-cy`). (The `cy-en` model was already available.)
    -   Serbian to English (`sr-en`) and English to Serbian (`en-sr`). Serbian translation support is based on the Cyrillic alphabet. (Bosnian and Croatian translation support is based on the Latin alphabet.)

    For more information, see [List of supported languages](/docs/language-translator?topic=language-translator-translation-models#list-languages-supported).

## 31 July 2020
{: #language-translator-31july2020}
{: release-note}

New method for listing supported languages
:   Added the [List supported languages](https://{DomainName}/apidocs/language-translator#listlanguages){: external} (`GET /v3/languages`) method to retrieve the list of supported languages for translation. The method returns a complete list of all supported languages, sorted by `language` code (for example, `af`, `ar`). In addition to basic information about each language, the response indicates whether the language is `supported_as_source` for translation and `supported_as_target` for translation. It also lists whether the language is `identifiable`.

    For more information, see [Listing supported languages for translation](/docs/language-translator?topic=language-translator-translation-models#list-languages).

## 14 July 2020
{: #language-translator-14july2020}
{: release-note}

New supported file types for customization
:   Added support for new file types for customization: CSV, TSV, XLSX (Microsoft Excel), XLIFF, and JSON. For more information, see [Supported document formats for training data](/docs/language-translator?topic=language-translator-customizing#supported-document-formats-for-training-data).

New translation models
:   Added Welsh-to-English (`cy-en`) support in translation, and added support for Welsh (`cy`) in language detection. For more information, see [List of supported languages](/docs/language-translator?topic=language-translator-translation-models#list-languages-supported).

## 11 June 2020
{: #language-translator-11june2020}
{: release-note}

New customizable translation models
:   Added the following customizable translation models for Ukrainian:
    -   Ukrainian to English (`uk-en`)
    -   English to Ukrainian (`en-uk`)

    For more information, see [List of supported languages](/docs/language-translator?topic=language-translator-translation-models#list-languages-supported).

Improved translation between Spanish and English
:   Improved results for the translation models between Spanish and English:
    -   Spanish to English (`es-en`)
    -   English to Spanish (`en-es`)

Improved document translation for Microsoft PowerPoint
:   Improved table handling with document translation for Microsoft PowerPoint.

## 28 May 2020
{: #language-translator-28may2020}
{: release-note}

Expanded language support for translation and identification
:   Expanded language support:
    -   Support for translating the following languages is now available:
        -   Nepali (`ne`)
        -   Sinhala (`si`)
    -   Support for identifying the following languages is now available:
        -   Burmese (`my`)
        -   Lao (`lo`)
        -   Marathi (`mr`)
        -   Nepali (`ne`)
        -   Punjabi (Shahmukhi script, Pakistan) (`pa-PK`)
        -   Sinhala (`si`)
        -   Tagalog (`tl`)

Improved translation results for Catalan and Chinese
:   Improved results when translating to and from the following languages:
    -   Catalan (`ca`)
    -   Chinese (Simplified) (`zh`)

New translation limits for Lite plan
:   For service instances on the Lite plan, the **Translate document** method now has a document size limit of **2 MB**. The document size limit for Standard, Advanced, and Premium plans remains **20 MB**.

## 22 April 2020
{: #language-translator-22april2020}
{: release-note}

Expanded language translation
:   The languages listed in [List of supported languages](/docs/language-translator?topic=language-translator-translation-models#list-languages-supported) can be translated to any other language in the list, with the exception of Catalan.

Expanded language support for translation
:   Support for translating the following languages is now available:
    -   Bengali (`bn`)
    -   Gujarati (`gu`)
    -   Malayalam (`ml`)
    -   Maltese (`mt`)
    -   Tamil (`ta`)
    -   Telugu (`te`)

Improved translation for English and Hindi
:   Improved translation quality for translation between English and Hindi.

Improved translation for Microsoft document types
:   Improved document translation performance for Microsoft Word, PowerPoint, and Excel documents.

## 28 February 2020
{: #language-translator-28february2020}
{: release-note}

Automatic source language detection in translation requests
:   Added automatic source language detection in **Translate** requests. When you specify a target language without specifying a source language or translation model, the service attempts to identify the source language and continues with the translation. In the results, the service returns the identified language and a score indicating the confidence in the identification.

## 30 January 2020
{: #language-translator-30january2020}
{: release-note}

New translation models
:   New translation models are now available:
    -   English to and from Latvian (`en-lv` and `lv-en`)
    -   English to and from Urdu (`en-ur` and `ur-en`)
    -   English to and from Vietnamese (`en-vi` and `vi-en`)

    For more information, see [List of supported languages](/docs/language-translator?topic=language-translator-translation-models#list-languages-supported).

Improved translation for Microsoft document types
:   Made general improvements for translating Microsoft Word and PowerPoint documents.

## 12 December 2019
{: #language-translator-12december2019}
{: release-note}

Full support for {{site.data.keyword.cloud_notm}} IAM
:   The {{site.data.keyword.languagetranslatorshort}} service now supports the full implementation of {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). API keys for Watson services are no longer limited to a single service instance. You can create access policies and API keys that apply to more than one service, and you can grant access between services.
    -   To support this change, the API service endpoints use a different domain and include the service instance ID. The pattern is `api.{location}.{offering}.watson.cloud.ibm.com/instances/{instance_id}`.

        Example URL for an instance hosted in the Dallas location: `api.us-south.language-translator.watson.cloud.ibm.com/instances/6bbda3b3-d572-45e1-8c54-22d6ed9e52c2`

        The previous public endpoint domain was `watsonplatform.net`.

        For more information about the URLs, see the [API & SDK reference](https://{DomainName}/apidocs/language-translator/language-translator#service-endpoint){: external}.

        These URLs do not introduce a breaking change. The new URLs work both for your existing service instances and for new instances. The original URLs continue to work on your existing service instances for at least one year (until December 2020).
    -   For more information about IAM, see [Authenticating to Watson services](/docs/watson?topic=watson-iam).

New network and data security features
:   Support for the following new network and data security features:
    -   *Support for private network endpoints*
        -   Users of Premium plans can create private network endpoints to connect to {{site.data.keyword.languagetranslatorshort}} over a private network. Connections to private network endpoints do not require public internet access. For more information, see [Public and private network endpoints](/docs/watson?topic=watson-public-private-endpoints).
    -   *Support for data encryption with customer-managed keys*
        -   Users of new Premium and Dedicated instances can integrate {{site.data.keyword.keymanagementservicefull}} with {{site.data.keyword.languagetranslatorshort}} to encrypt their data and manage encryption keys. For more information, see [Protecting sensitive information in your Watson service](/docs/watson?topic=watson-keyservice).

## 13 November 2019
{: #language-translator-13november2019}
{: release-note}

New Seoul location
:   You can now create {{site.data.keyword.languagetranslatorshort}} instances in the Seoul, South Korea, location. As with other locations, the {{site.data.keyword.cloud_notm}} Seoul location uses token-based Identity and Access Management (IAM) authentication.

## 11 November 2019
{: #language-translator-11november2019}
{: release-note}

Customization and identification improvements
:   Improved custom model training time. Also, Improved language identification accuracy for English text and for text with more than 100 words.

New translation models
:   New translation models are now available.
    -   English to and from Indonesian (`en-id` and `id-en`)
    -   English to and from Irish (`en-ga` and `ga-en`)
    -   English to and from Lithuanian (`en-lt` and `lt-en`)
    -   English to and from Malay (`en-ms` and `ms-en`)
    -   English to and from Thai (`en-th` and `th-en`)

    For more information, see [List of supported languages](/docs/language-translator?topic=language-translator-translation-models#list-languages-supported). Note that Indonesian cannot be identified by the service's language identification feature.

## 21 August 2019
{: #language-translator-21august2019}
{: release-note}

New translation models
:   New translation models are now available:
    -   English to and from Bulgarian (`en-bg` and `bg-en`)
    -   English to and from Croatian (`en-hr` and `hr-en`)
    -   English to and from Estonian (`en-et` and `et-en`)
    -   English to and from Romanian (`en-ro` and `ro-en`)
    -   English to and from Slovak (`en-sk` and `sk-en`)
    -   English to and from Slovenian (`en-sl` and `sl-en`)

New identifiable languages
:   The following languages can now be identified by the service:
    -   Catalan (`ca`)
    -   Croatian (`hr`)
    -   Irish (`ga`)
    -   Malay (`ms`)
    -   Maltese (`mt`)
    -   Serbian (`sr`)
    -   Slovenian (`sl`)
    -   Thai (`th`)

## 14 June 2019
{: #language-translator-14june2019}
{: release-note}

New translation models
:   New translation models are now available for English and Greek:

    -   English to Greek (`en-el`)
    -   Greek to English (`el-en`)

## 13 June 2019
{: #language-translator-13june2019}
{: release-note}

New translation models
:   New translation models are now available for English and Hebrew:

    -   English to Hebrew (`en-he`)
    -   Hebrew to English (`he-en`)

## 21 March 2019
{: #language-translator-21march2019}
{: release-note}

Changes to service credential information
:   From March 21 2019, you will see only service credential information associated with the role that has been assigned to your {{site.data.keyword.cloud_notm}} account. For example, if you have assigned a `reader` role, any `writer` or higher levels of service credentials will not be visible.

    This change does not affect API access for users or applications with existing service key credentials. Only the viewing of credentials within {{site.data.keyword.cloud_notm}} is affected.

    For more information about service keys and user roles, see [Authenticating to Watson services](/docs/watson?topic=watson-iam).

## 14 December 2018
{: #language-translator-14december2018}
{: release-note}

New London location
:   You can now create {{site.data.keyword.languagetranslatorshort}} service instances in the {{site.data.keyword.cloud_notm}} London location.

## 16 November 2018
{: #language-translator-16november2018}
{: release-note}

New beta support for document translation
:   [Translating documents](/docs/language-translator?topic=language-translator-document-translator-tutorial) is now available through new API endpoints. Submit a Microsoft Office document, PDF, or other document with a supported file format, and {{site.data.keyword.languagetranslatorshort}} will provide a translated copy that preserves the original formatting. [Supported file formats](/docs/language-translator?topic=language-translator-document-translator-tutorial#supported-file-formats) include `.doc`, `.ppt`, `.pdf`, and more.

New translation models
:   New translation models for Hungarian are now available:
    -   Hungarian to English (`hu-en`)
    -   English to Hungarian (`en-hu`)

## 8 November 2018
{: #language-translator-8november2018}
{: release-note}

New Tokyo location
:   You can now create {{site.data.keyword.languagetranslatorshort}} service instances in the {{site.data.keyword.cloud_notm}} Tokyo location.

## 9 August 2018
{: #language-translator-9august2018}
{: release-note}

New translation models
:   New translation models for Norwegian Bokmål are now available:

    -   Norwegian Bokmål to English (`nb-en`)
    -   English to Norwegian Bokmål (`en-nb`)

## 27 June 2018
{: #language-translator-27june2018}
{: release-note}

New translation models
:   New translation models that feature six new languages are now available:

    -   Catalan
        -   Catalan to Spanish (`ca-es`)
        -   Spanish to Catalan (`es-ca`)
    -   Czech
        -   Czech to English (`cs-en`)
        -   English to Czech (`en-cs`)
    -   Danish
        -   Danish to English (`da-en`)
        -   English to Danish (`en-da`)
    -   Finnish
        -   Finnish to English (`fi-en`)
        -   English to Finnish (`en-fi`)
    -   Hindi
        -   Hindi to English (`hi-en`)
        -   English to Hindi (`en-hi`)
    -   Swedish
        -   Swedish to English (`sv-en`)
        -   English to Swedish (`en-sv`)

## 15 June 2018
{: #language-translator-15june2018}
{: release-note}

New support for {{site.data.keyword.cloud_notm}} IAM
:   As of 15 June 2018, new service instances created in the Germany and US South regions use [Identity and Access Management (IAM) authentication](#iam-auth-process).

    New service instances that you create in Germany and US South will not be compatible with Language Translator v2. If you use Language Translator v2 and are planning to use new service instances in your application, migrate to the v3 API.

## 12 June 2018
{: #language-translator-12june2018}
{: release-note}

Version 3 of the service is now available
:    {{site.data.keyword.languagetranslatorshort}} v3 is now available. The v2 Language Translator API will no longer be available after July 31, 2018. To take advantage of the latest service enhancements, migrate to the v3 API.

New features in version 3
:   Version 3 includes the following new features:

    -   {{site.data.keyword.languagetranslatorshort}} API v3 comes with **Neural Machine Translation** (NMT) models that offer significantly improved translation results. All NMT models are now available for customization.
    -   Use custom models as base models for forced glossary customization.
    -   API v3 is a simplified, all-JSON subset of the retired API v2.
    -   Introduces API version dates to give developers the freedom to adopt future API changes at their own pace.

Breaking changes in version 3
:   Version 3 includes the following breaking changes:

    -   Mandatory version date for all API endpoints: API v3 requests require a version date query parameter of the form `version=YYYY-MM-DD`. The latest API version is `version=2018-05-01`.
    -   Simplified API:
        -   The **Translate** and **Identify** methods do not offer the option to return plain text responses in v3. The methods return only JSON responses.
        -   `GET /translate` and `GET /identify` methods are not supported in v3. Use the `POST /translate` and `POST /identify` methods instead.
    -   Monolingual corpus customization is not supported in v3.
    -   Creating custom models with both a parallel corpus and forced glossary now needs to be done in two API calls. First, customize the model with a parallel corpus. After the custom model has finished training, customize it again with the forced glossary. This change allows you to use a custom model trained with a parallel corpus as a base for forced glossary customization.
    -   Specialized patent and conversation domain models are not available in the v3 API. The translation quality provided by the NMT models in the patent and conversation domains is generally improved compared to the older specialized models.
    -   Error object keys have been renamed so that they are consistent with other Watson APIs. `error_code` has been renamed to `code`, and `error_message` has been renamed to `error`.

New support for {{site.data.keyword.cloud_notm}} IAM
:   As of 12 June 2018, new service instances created in the Sydney and US East regions use [Identity and Access Management (IAM) authentication](#iam-auth-process).

## 12 January 2018
{: #language-translator-12january2018}
{: release-note}

New Neural Machine Translation Models
:   New Neural Machine Translation (NMT) models are available to preview. You can try NMT models for the following language pairs.

    -   English to and from: Arabic, Chinese, Dutch, French, German, Italian, Japanese, Korean, Polish, Portuguese (Brazilian), Russian, Spanish, and Turkish
    -   French to and from: German, Spanish
    -   German to and from: Italian

    The NMT models and the syntax for using them are subject to change during the preview period. Currently, NMT models do not support corpus customization. Only forced glossary customization is supported.

    To use an NMT preview model to translate, specify the header `X-Watson-Technology-Preview:2017-07-01` along with the character codes for the source and target languages of the model you want to use. The following example shows how to translate English to Spanish with an NMT preview model.

    ```sh
    curl -X POST --user {username}:{password} \
    -H "Accept: application/json" \
    -H "X-Watson-Technology-Preview:2017-07-01" \
    -d '{"text":"Hello!","source":"en","target":"es"}' \
    "https://gateway.watsonplatform.net/language-translator/api/v2/translate"
    ```
    {: codeblock}

## 15 December 2016
{: #language-translator-15december2016}
{: release-note}

New translation models
:   New translation models were added: English to and from Japanese

## 15 November 2016
{: #language-translator-15november2016}
{: release-note}

Beta tooling no longer available or supported
:   The beta tooling that was previously available for the {{site.data.keyword.languagetranslatorshort}} service is no longer available or supported. Contact your sales representative or customer support for information about how to use the {{site.data.keyword.languagetranslatorshort}} API to accomplish the tasks supported by the {{site.data.keyword.languagetranslatorshort}} tool.

## 1 September 2016
{: #language-translator-1september2016}
{: release-note}

Service rebranding
:   The IBM Watson&trade; Language Translation service was rebranded as the {{site.data.keyword.languagetranslatorshort}} service.

## 22 March 2016
{: #language-translator-22march2016}
{: release-note}

New language support
:   Support for additional languages was added: English to and from Italian, and Spanish to and from French.

## 3 December 2015
{: #language-translator-3december2015}
{: release-note}

Customization no longer available with Standard plan
:   As of January 15, 2016, all customization capabilities within the Standard plan are discontinued. Applications that do not use customization features do not need to change, as the Standard plan remains active for all API calls unrelated to customization or customized models. To use the GA customization features (the Trainable plan) of the {{site.data.keyword.languagetranslatorshort}} service with an {{site.data.keyword.cloud}} application that uses an earlier instance of the service, complete the following steps:

    1.  Create a new Watson {{site.data.keyword.languagetranslatorshort}} instance and specify the GA "Trainable" plan.
    2.  Bind the new "Trainable" instance of the service to your app in {{site.data.keyword.cloud_notm}}.
    3.  Gather the data that was used to initially create the customized models.
    4.  Upload the training data to create new customized models on the "Trainable" instance.
    5.  In your app, point the "ModelID" field to the new customized models.
    6.  Unbind the earlier service from your app in {{site.data.keyword.cloud_notm}}, and then delete it.

## 6 November 2015
{: #language-translator-6november2015}
{: release-note}

Beta tooling available
:   The beta {{site.data.keyword.languagetranslatorshort}} tool is released. The tool is a web application that provides a graphical user interface to manage and train models for more accurate machine translation. You can create projects, upload training data, train custom models, and translate text.

## 1 December 2014
{: #language-translator-1december2014}
{: release-note}

Beta machine translation and language identification APIs upgraded
:   The beta Machine Translator and beta Language Identification APIs have been upgraded and combined into the {{site.data.keyword.languagetranslatorshort}} API. To immediately start using the new service, understand and update your code to reflect these changes:

    -   **New model_id parameter**: In the beta API, you defined the `sid` parameter to select the model to use for translation. In this version, the `sid` parameter is renamed to `model_id` parameter. To retrieve the `model_id` allowed values, use the `GET/language  translator/api/v2/models` operation. This returns a list of all models and their corresponding `model_id` values.
    -   **Language pair support**: Instead of selecting a `model_id`, you can now specify a source and target language instead, and the model will default to the one that's trained on the general news domain.
    -   **JSON request body support**: When making a POST translation request, you can now make the request as a JSON submission. The JSON formatting allows you to submit multiple paragraphs for translation, instead of just a single piece of text in the form submission format.
    -   **JSON response body support**: The translation request returns support JSON formatting as well as plain text formatting. The JSON format allows support for the translated words to be returned in multiple paragraphs instead of a single piece of text.
    -   **Accept header support**: The accept header can now be used to define the format of the response in all of the operations (text/plain or application/json).
    -   **Language Identification support**: Language identification methods have been added to this API. This allows you to identify the language of the input texts, and lists all supported languages that can be detected by the API.

New API authentication process
:   The {{site.data.keyword.languagetranslatorshort}} service has a new API authentication process for service instances that are hosted in the following locations:

    -   Dallas as of June 15, 2018
    -   Frankfurt as of June 15, 2018
    -   London
    -   Seoul
    -   Sydney as of June 12, 2018
    -   Tokyo
    -   Washington, DC as of June 12, 2018

    {{site.data.keyword.cloud_notm}} is migrating to token-based Identity and Access Management (IAM) authentication. With some service instances, you authenticate to the API by using IAM.

{{site.data.keyword.cloud_notm}} IAM available for service instances
:   {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) is available for new and existing service instances as follows:

    -   For *new* service instances created in the locations indicated previously, you use IAM for authentication. You can pass either a bearer token or an API key. Tokens support authenticated requests without embedding service credentials in every call. API keys use basic authentication.

        When you use any of the Watson SDKs, you can pass the API key and let the SDK manage the lifecycle of the tokens. For more information and examples, see [Authentication](https://{DomainName}/apidocs/language-translator#authentication){: external} in the API & SDK reference.
    -   For *existing* service instances that you created before the indicated date, you continue to authenticate by providing the username and password for the service instance. Eventually, you will need to migrate these service instances to IAM authentication. Updates will be provided about migration process and dates. For more information about migration, see [Migrating Watson services from Cloud Foundry](/docs/language-translator?topic=watson-migrate).

    To find out which authentication to use, view the service credentials by clicking the service instance on the [{{site.data.keyword.cloud_notm}} resources page](https://cloud.ibm.com/resources){: external}.

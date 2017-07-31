---

copyright:
  years: 2015, 2017
lastupdated: "2017-07-19"

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

# Release notes

The following new features and changes to the service are available.
{: shortdesc}

## 15 December 2016

Additional News translation models were added: English to and from Japanese

## 15 November 2016

The tooling that was previously available for the Language Translator service is no longer available or supported. 

Contact your sales representative or customer support for information about how to use the Language Translator API to accomplish the tasks supported by the Language Translator tool.

## 1 September 2016

The IBM Watson&trade; Language Translation service was rebranded as the {{site.data.keyword.languagetranslatorshort}} service. For information about migrating applications from the Language Translation service to the {{site.data.keyword.languagetranslatorshort}} service, see the [Migrating from Language Translation](/docs/services/language-translator/migrating.html) documentation.

## 22 March 2016

Support for additional languages was added: English to and from Italian, and Spanish to and from French.

## 3 December 2015

As of January 15, 2016, all customization capabilities within the Standard Plan are discontinued. Applications that do not use customization features do not need to change, as the Standard Plan remains active for all API calls unrelated to customization or customized models. To use the GA customization features (the Trainable plan) of the Language Translator service with a Bluemix&reg; application that uses an earlier instance of the service, complete the following steps:

1.  Create a new Watson Language Translator instance and specify the GA "Trainable" plan.
1.  Bind the new "Trainable" instance of the service to your app in {{site.data.keyword.Bluemix_notm}}.
1.  Gather the data that was used to initially create the customized models. For more information, see [Structure of the training data](/docs/services/language-translator/customizing.html#structure).
1.  Upload the training data to create new customized models on the "Trainable" instance. For more information, see [Training a custom translation model](/docs/services/language-translator/customizing.html#training).
1.  In your app, point the "ModelID" field to the new customized models.
1.  Unbind the earlier service from your app in {{site.data.keyword.Bluemix_notm}}, and then delete it.

## 6 November 2015

The Language Translator tool beta is released. The tool is a web application that provides a graphical user interface to manage and train models for more accurate machine translation. You can create projects, upload training data, train custom models, and translate text.

## 1 December 2014

The beta Machine Translator and beta Language Identification APIs have been upgraded and combined into the Language Translator API. To immediately start using the new service, understand and update your code to reflect these changes:

- **New model\_id parameter**: In the beta API, you defined the `sid` parameter to select the model to use for translation. In this version, the `sid` parameter is renamed to `model_id` parameter. To retrieve the `model_id` allowed values, use the `GET/language  translator/api/v2/models` operation. This returns a list of all models and their corresponding `model_id` values.
- **Language pair support**: Instead of selecting a `model_id`, you can now specify a source and target language instead, and the model will default to the one that's trained on the general news domain.
- **JSON request body support**: When making a POST translation request, you can now make the request as a JSON submission. The JSON formatting allows you to submit multiple paragraphs for translation, instead of just a single piece of text in the form submission format.
- **JSON response body support**: The translation request returns support JSON formatting as well as plain text formatting. The JSON format allows support for the translated words to be returned in multiple paragraphs instead of a single piece of text.
- **Accept header support**: The accept header can now be used to define the format of the response in all of the operations (text/plain or application/json).
- **Language Identification support**: Language identification methods have been added to this API. This allows you to identify the language of the input texts, and lists all supported languages that can be detected by the API.


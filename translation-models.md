---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-04"

keywords: translation models,list translation models,customizable models

subcollection: language-translator

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:deprecated: .deprecated}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:preview: .preview}
{:beta: .beta}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

# Supported languages for translation
{: #translation-models}

{{site.data.keyword.languagetranslatorfull}} supports a wide array of translatable languages. It also supports customization of many translation models.

## Listing supported languages for translation
{: #list-languages}

You can use the [List supported languages](https://cloud.ibm.com/apidocs/language-translator#list-supported-languages){: external} method to retrieve the list of supported languages for translation. The following example calls the method.

```sh
curl -X GET --user "apikey:{apikey}" \
"{url}/v3/languages?version=2018-05-01"
```
{: pre}

The method returns a complete list of all supported languages, sorted by `language` code (for example, `af`, `ar`). In addition to basic information about each language, the response indicates whether the language is `supported_as_source` for translation and `supported_as_target` for translation.

```json
"languages": [
  {
    "language": "af",
    "language_name": "Afrikaans",
    "native_language_name": "Afrikaans",
    "country_code": "ZA",
    "words_separated": true,
    "direction": "left_to_right",
    "supported_as_source": false,
    "supported_as_target": false,
    "identifiable": true
  },
  {
    "language": "ar",
    "language_name": "Arabic",
    "native_language_name": "العربية",
    "country_code": "AR",
    "words_separated": true,
    "direction": "right_to_left",
    "supported_as_source": true,
    "supported_as_target": true,
    "identifiable": true
  },
  . . .
]
```
{: codeblock}

## List of supported languages
{: #list-languages-supported}

The following table list the translatable languages. The service can translate from the following languages to any other language in the list (with the exception of Catalan).

Not all language combinations that are supported for translation are also customizable. Usually, only the combinations with English as source or target language are customizable. Click the name of a language to see the customizable translation models for that language.

|Language                                     | Language code |Language                             | Language code |
|---------------------------------------------|:-------------:|-------------------------------------|:-------------:|
|[Arabic](#arabic)                            |`ar`         |[Latvian](#latvian)                  |`lv`|
|[Bengali](#bengali)                          |`bn`         |[Lithuanian](#lithuanian)            |`lt`|
|[Bulgarian](#bulgarian)                      |`bg`         |[Malay](#malay)                      |`ms`|
|[Catalan](#catalan) **[1]**                  |`ca`         |[Malayalam](#malayalam)              |`ml`|
|[Chinese (Simplified)](#chinese-simplified)  |`zh`         |[Maltese](#maltese)                  |`mt`|
|[Chinese (Traditional)](#chinese-traditional)|`zh-TW`      |[Nepali](#nepali)                    |`ne`|
|[Croatian](#croatian)                        |`hr`         |[Norwegian Bokmål](#norwegian-bokmal)|`nb`|
|[Czech](#czech)                              |`cs`         |[Polish](#polish)                    |`pl`|
|[Danish](#danish)                            |`da`         |[Portuguese](#portuguese)            |`pt`|
|[Dutch](#dutch)                              |`nl`         |[Romanian](#romanian)                |`ro`|
|[English](#english)                          |`en`         |[Russian](#russian)                  |`ru`|
|[Estonian](#estonian)                        |`et`         |[Sinhala](#sinhala)                  |`si`|
|[Finnish](#finnish)                          |`fi`         |[Slovak](#slovak)                    |`sk`|
|[French](#french)                            |`fr`         |[Slovenian](#slovenian)              |`sl`|
|[German](#german)                            |`de`         |[Spanish](#spanish)                  |`es`|
|[Greek](#greek)                              |`el`         |[Swedish](#swedish)                  |`sv`|
|[Gujarati](#gujarati)                        |`gu`         |[Tamil](#tamil)                      |`ta`|
|[Hebrew](#hebrew)                            |`he`         |[Telugu](#telugu)                    |`te`|
|[Hindi](#hindi)                              |`hi`         |[Thai](#thai)                        |`th`|
|[Hungarian](#hungarian)                      |`hu`         |[Turkish](#turkish)                  |`tr`|
|[Irish](#irish)                              |`ga`         |[Ukrainian](#ukrainian)              |`uk`|
|[Indonesian](#indonesian)                    |`id`         |[Urdu](#urdu)                        |`ur`|
|[Italian](#italian)                          |`it`         |[Vietnamese](#Vietnamese)            |`vi`|
|[Japanese](#japanese)                        |`ja`         |[Welsh](#welsh)                      |`cy`|
|[Korean](#korean)                            |`ko`         | | |

**[1]** Catalan is supported only for translation to and from Spanish.

## Listing supported translation models for customization
{: #customizable-models}

You can use the [List models](https://cloud.ibm.com/apidocs/language-translator#list-models){: external} method to view the available translation models and any custom models that you created. You can filter results by language with the `source` and `target` parameters. The following example lists models that can translate from English to Spanish.

```sh
curl -X GET --user "apikey:{apikey}" \
"{url}/v3/models?source=en&target=es&version=2018-05-01"
```
{: pre}

The method returns information about the `en-es` translation model that you can use to translate from English to Spanish. The model is customizable.

```json
"models": [
  {
    "model_id": "en-es",
    "source": "en",
    "target": "es",
    "base_model_id": "",
    "domain": "general",
    "customizable": true,
    "default_model": true,
    "owner": "",
    "status": "available",
    "name": "en-es"
  },
]
```
{: codeblock}

## List of customizable translation models
{: #customizable-models-supported}

The following sections list the customizable translation models for each language. As mentioned previously, not all language combinations that are supported for translation are also customizable. Typically, only language combinations with English as the source or target language are customizable.

### Arabic
{: #arabic}

The following Arabic translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `ar-en`  | Arabic (`ar`) | English (`en`) | general |

### Bengali
{: #bengali}

The following Bengali translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `bn-en`  | Bengali (`bn`) | English (`en`) | general |


### Bulgarian
{: #bulgarian}

The following Bulgarian translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `ar-en`  | Arabic (`ar`) | English (`en`) | general |

### Catalan
{: #catalan}

The following Catalan translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `ca-es`  | Catalan (`ca`) | Spanish (`es`) | general |

### Chinese (Simplified)
{: #chinese-simplified}

The following Chinese (Simplified) translation models can be customized.

| Model ID | Source                    | Target         | Domain  |
|----------|---------------------------|----------------|---------|
| `zh-en`  | Simplified Chinese (`zh`) | English (`en`) | general |

### Chinese (Traditional)
{: #chinese-traditional}

The following Chinese (Traditional) translation models can be customized.

| Model ID   | Source                       | Target         | Domain  |
|------------|------------------------------|----------------|---------|
| `zh-TW-en` | Simplified Chinese (`zh-TW`) | English (`en`) | general |

### Croatian
{: #croatian}

The following Croatian translation models can be customized.

| Model ID | Source          | Target         | Domain  |
|----------|-----------------|----------------|---------|
| `hr-en`  | Croatian (`hr`) | English (`en`) | general |

### Czech
{: #czech}

The following Czech translation models can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `cs-en`  | Czech (`cs`) | English (`en`) | general |

### Danish
{: #danish}

The following Danish translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `da-en`  | Danish (`da`) | English (`en`) | general |

### Dutch
{: #dutch}

The following Dutch translation models can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `nl-en`  | Dutch (`nl`) | English (`en`) | general |

### English
{: #english}

The following English translation models can be customized.

| Model ID   | Source         | Target                        | Domain  |
|------------|----------------|-------------------------------|---------|
| `en-ar`    | English (`en`) | Arabic (`ar`)                 | general |
| `en-bg`    | English (`en`) | Bulgarian (`bg`)              | general |
| `en-bn`    | English (`en`) | Bengali (`bn`)                | general |
| `en-cs`    | English (`en`) | Czech (`cs`)                  | general |
| `en-da`    | English (`en`) | Danish (`da`)                 | general |
| `en-de`    | English (`en`) | German (`de`)                 | general |
| `en-el`    | English (`en`) | Greek (`el`)                  | general |
| `en-es`    | English (`en`) | Spanish (`es`)                | general |
| `en-et`    | English (`en`) | Estonian (`et`)               | general |
| `en-fi`    | English (`en`) | Finnish (`fi`)                | general |
| `en-fr`    | English (`en`) | French (`fr`)                 | general |
| `en-ga`    | English (`en`) | Irish (`ga`)                  | general |
| `en-gu`    | English (`en`) | Gujarati (`gu`)               | general |
| `en-he`    | English (`en`) | Hebrew (`he`)                 | general |
| `en-hi`    | English (`en`) | Hindi (`hi`)                  | general |
| `en-hr`    | English (`en`) | Croatian (`hr`)               | general |
| `en-hu`    | English (`en`) | Hungarian (`hu`)              | general |
| `en-id`    | English (`en`) | Indonesian (`id`)             | general |
| `en-it`    | English (`en`) | Italian (`it`)                | general |
| `en-ja`    | English (`en`) | Japanese (`ja`)               | general |
| `en-ko`    | English (`en`) | Korean (`ko`)                 | general |
| `en-lt`    | English (`en`) | Lithuanian (`lt`)             | general |
| `en-lv`    | English (`en`) | Latvian (`lv`)                | general |
| `en-ml`    | English (`en`) | Malayalam (`ml`)              | general |
| `en-ms`    | English (`en`) | Malay (`ms`)                  | general |
| `en-mt`    | English (`en`) | Maltese (`mt`)                | general |
| `en-ne`    | English (`en`) | Nepali (`ne`)                 | general |
| `en-nb`    | English (`en`) | Norwegian Bokmal (`nb`)       | general |
| `en-nl`    | English (`en`) | Dutch (`nl`)                  | general |
| `en-pl`    | English (`en`) | Polish (`pl`)                 | general |
| `en-pt`    | English (`en`) | Portuguese (`pt`)             | general |
| `en-ro`    | English (`en`) | Romanian (`ro`)               | general |
| `en-ru`    | English (`en`) | Russian (`ru`)                | general |
| `en-si`    | English (`en`) | Sinhala (`si`)                | general |
| `en-sk`    | English (`en`) | Slovak (`sk`)                 | general |
| `en-sl`    | English (`en`) | Slovenian (`sl`)              | general |
| `en-sv`    | English (`en`) | Swedish (`sv`)                | general |
| `en-ta`    | English (`en`) | Tamil (`ta`)                  | general |
| `en-te`    | English (`en`) | Telugu (`te`)                 | general |
| `en-th`    | English (`en`) | Thai (`th`)                   | general |
| `en-tr`    | English (`en`) | Turkish (`tr`)                | general |
| `en-uk`    | English (`en`) | Ukrainian (`uk`)              | general |
| `en-ur`    | English (`en`) | Urdu (`ur`)                   | general |
| `en-vi`    | English (`en`) | Vietnamese (`vi`)             | general |
| `en-zh`    | English (`en`) | Simplified Chinese (`zh`)     | general |
| `en-zh-TW` | English (`en`) | Traditional Chinese (`zh-TW`) | general |

### Estonian
{: #estonian}

The following Estonian translation models can be customized.

| Model ID | Source          | Target         | Domain  |
|----------|-----------------|----------------|---------|
| `et-en`  | Estonian (`et`) | English (`en`) | general |

### Finnish
{: #finnish}

The following Finnish translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `fi-en`  | Finnish (`fi`) | English (`en`) | general |

### French
{: #french}

The following French translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `fr-en`  | French (`fr`) | English (`en`) | general |

### German
{: #german}

The following German translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `de-en`  | German (`de`) | English (`en`) | general |
| `de-fr`  | German (`de`) | French (`fr`)  | general |
| `de-it`  | German (`de`) | Italian (`it`) | general |

### Greek
{: #greek}

The following Greek translation models can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `el-en`  | Greek (`el`) | English (`en`) | general |

### Gujarati
{: #gujarati}

The following Gujarati translation models can be customized.

| Model ID | Source          | Target         | Domain  |
|----------|-----------------|----------------|---------|
| `gu-en`  | Gujarati (`gu`) | English (`en`) | general |

### Hebrew
{: #hebrew}

The following Hebrew translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `he-en`  | Hebrew (`he`) | English (`en`) | general |

### Hindi
{: #hindi}

The following Hindi translation models can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `hi-en`  | Hindi (`hi`) | English (`en`) | general |

### Hungarian
{: #hungarian}

The following Hungarian translation models can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|------------------|----------------|---------|
| `hu-en`  | Hungarian (`hu`) | English (`en`) | general |

### Indonesian
{: #indonesian}

The following Indonesian translation models can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `id-en`  | Indonesian (`id`) | English (`en`) | general |

### Irish
{: #irish}

The following Irish translation models can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `ga-en`  | Irish (`ga`) | English (`en`) | general |

### Italian
{: #italian}

The following Italian translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `it-de`  | Italian (`it`) | German (`de`)  | general |
| `it-en`  | Italian (`it`) | English (`en`) | general |

### Japanese
{: #japanese}

The following Japanese translation models can be customized.

| Model ID | Source          | Target         | Domain  |
|----------|-----------------|----------------|---------|
| `ja-en`  | Japanese (`ja`) | English (`en`) | general |

### Korean
{: #korean}

The following Korean translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `ko-en`  | Korean (`ko`) | English (`en`) | general |

### Latvian
{: #latvian}

The following Latvian translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `lv-en`  | Latvian (`lv`) | English (`en`) | general |

### Lithuanian
{: #lithuanian}

The following Lithuanian translation models can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `lt-en`  | Lithuanian (`lt`) | English (`en`) | general |

### Malay
{: #malay}

The following Malay translation models can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `ms-en`  | Malay (`ms`) | English (`en`) | general |

### Malayalam
{: #malayalam}

The following Malayalam translation models can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|------------------|----------------|---------|
| `ml-en`  | Malayalam (`ml`) | English (`en`) | general |

### Maltese
{: #maltese}

The following Maltese translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `mt-en`  | Maltese (`mt`) | English (`en`) | general |

### Nepali
{: #nepali}

The following Nepali translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `ne-en`  | Nepali (`ne`) | English (`en`) | general |

### Norwegian Bokmål
{: #norwegian-bokmal}

The following Norwegian Bokmål translation models can be customized.

| Model ID | Source                  | Target         | Domain  |
|----------|-------------------------|----------------|---------|
| `nb-en`  | Norwegian Bokmal (`nb`) | English (`en`) | general |

### Polish
{: #polish}

The following Polish translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `pl-en`  | Polish (`pl`) | English (`en`) | general |

### Portuguese
{: #portuguese}

The following Portuguese translation models can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `pt-en`  | Portuguese (`pt`) | English (`en`) | general |

### Romanian
{: #romanian}

The following Romanian translation models can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `ro-en`  | Romanian (`ro`)   | English (`en`) | general |

### Russian
{: #russian}

The following Russian translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `ru-en`  | Russian (`ru`) | English (`en`) | general |

### Sinhala
{: #sinhala}

The following Sinhala translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `si-en`  | Sinhala (`si`) | English (`en`) | general |

### Slovak
{: #slovak}

The following Slovak translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `sk-en`  | Slovak (`sk`) | English (`en`) | general |

### Slovenian
{: #slovenian}

The following Slovenian translation models can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|------------------|----------------|---------|
| `sl-en`  | Slovenian (`sl`) | English (`en`) | general |

### Spanish
{: #spanish}

The following Spanish translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `es-ca`  | Spanish (`es`) | Catalan (`ca`) | general |
| `es-en`  | Spanish (`es`) | English (`en`) | general |
| `es-fr`  | Spanish (`es`) | French (`fr`)  | general |

### Swedish
{: #swedish}

The following Swedish translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `sv-en`  | Swedish (`sv`) | English (`en`) | general |

### Tamil
{: #tamil}

The following Tamil translation models can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `ta-en`  | Tamil (`ta`) | English (`en`) | general |

### Telugu
{: #telugu}

The following Telugu translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `te-en`  | Telugu (`te`) | English (`en`) | general |

### Thai
{: #thai}

The following Thai translation models can be customized.

| Model ID | Source      | Target         | Domain  |
|----------|-------------|----------------|---------|
| `th-en`  | Thai (`th`) | English (`en`) | general |

### Turkish
{: #turkish}

The following Turkish translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `tr-en`  | Turkish (`tr`) | English (`en`) | general |

### Ukrainian
{: #ukrainian}

The following Ukrainian translation models can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|------------------|----------------|---------|
| `uk-en`  | Ukrainian (`uk`) | English (`en`) | general |

### Urdu
{: #urdu}

The following Urdu translation models can be customized.

| Model ID | Source      | Target         | Domain  |
|----------|-------------|----------------|---------|
| `ur-en`  | Urdu (`ur`) | English (`en`) | general |

### Vietnamese
{: #vietnamese}

The following Vietnamese translation models can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `vi-en`  | Vietnamese (`vi`) | English (`en`) | general |

### Welsh
{: #welsh}

The following Welsh translation models can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `cy-en`  | Welsh (`cy`)      | English (`en`) | general |

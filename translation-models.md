---

copyright:
  years: 2015, 2020
lastupdated: "2020-06-23"

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

{{site.data.keyword.languagetranslatorshort}} can translate from the following languages to any other language in the list, with the exception of Catalan. Click a language to see the customizable translation models for that language.

|Language|Language code|
|---|---|
|[Arabic](#arabic)|`ar`|
|[Bengali](#bengali)|`bn`|
|[Bulgarian](#bulgarian)|`bg`|
|[Catalan](#catalan)\*|`ca`|
|[Chinese (Simplified)](#chinese-simplified)|`zh`|
|[Chinese (Traditional)](#chinese-traditional)|`zh-TW`|
|[Croatian](#croatian)|`hr`|
|[Czech](#czech)|`cs`|
|[Danish](#danish)|`da`|
|[Dutch](#dutch)|`nl`|
|[English](#english)|`en`|
|[Estonian](#estonian)|`et`|
|[Finnish](#finnish)|`fi`|
|[French](#french)|`fr`|
|[German](#german)|`de`|
|[Greek](#greek)|`el`|
|[Gujarati](#gujarati)|`gu`|
|[Hebrew](#hebrew)|`he`|
|[Hindi](#hindi)|`hi`|
|[Hungarian](#hungarian)|`hu`|
|[Irish](#irish)|`ga`|
|[Indonesian](#indonesian)|`id`|
|[Italian](#italian)|`it`|
|[Japanese](#japanese)|`ja`|
|[Korean](#korean)|`ko`|
|[Latvian](#latvian)|`lv`|
|[Lithuanian](#lithuanian)|`li`|
|[Malay](#malay)|`ms`|
|[Malayalam](#malayalam)|`ml`|
|[Maltese](#maltese)|`mt`|
|[Nepali](#nepali)|`ne`|
|[Norwegian Bokmål](#norwegian-bokmal)|`nb`|
|[Polish](#polish)|`pl`|
|[Portuguese](#portuguese)|`pt`|
|[Romanian](#romanian)|`ro`|
|[Russian](#russian)|`ru`|
|[Sinhala](#sinhala)|`si`|
|[Slovak](#slovak)|`sk`|
|[Slovenian](#slovenian)|`sl`|
|[Spanish](#spanish)|`es`|
|[Swedish](#swedish)|`sv`|
|[Tamil](#tamil)|`ta`|
|[Telugu](#telugu)|`te`|
|[Thai](#thai)|`th`|
|[Turkish](#turkish)|`tr`|
|[Ukrainian](#ukrainian)|`uk`|
|[Urdu](#urdu)|`ur`|
|[Vietnamese](#Vietnamese)|`vi`|

\* Catalan is supported only for translation to and from Spanish.

## Customization support
{: #customization-support}

The following sections list the customizable translation models for each language.

You can also use the [List models](https://cloud.ibm.com/apidocs/language-translator#list-models){: external} API method to view the available translation models and custom models that you created. You can filter results by language with the `source` and `target` parameters. The following example lists models that can translate English to Spanish.

```sh
curl --user "apikey:{apikey}" "https://{url}/v3/models?source=en&target=es&version=2018-05-01"
```
{: pre}

### Arabic
{: #arabic}

The following Arabic translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `ar-en`  | Arabic (`ar`) | English (`en`) | general | true         |

### Bengali
{: #bengali}

The following Bengali translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `bn-en`  | Bengali (`bn`) | English (`en`) | general | true         |


### Bulgarian
{: #bulgarian}

The following Bulgarian translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `ar-en`  | Arabic (`ar`) | English (`en`) | general | true         |

### Catalan
{: #catalan}

The following Catalan translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `ca-es`  | Catalan (`ca`) | Spanish (`es`) | general | true         |

### Chinese (Simplified)
{: #chinese-simplified}

The following Chinese (Simplified) translation models can be customized.

| Model ID | Source                    | Target         | Domain  | Customizable |
|----------|---------------------------|----------------|---------|--------------|
| `zh-en`  | Simplified Chinese (`zh`) | English (`en`) | general | true         |

### Chinese (Traditional)
{: #chinese-traditional}

The following Chinese (Traditional) translation models can be customized.

| Model ID   | Source                       | Target         | Domain  | Customizable |
|------------|------------------------------|----------------|---------|--------------|
| `zh-TW-en` | Simplified Chinese (`zh-TW`) | English (`en`) | general | true         |

### Croatian
{: #croatian}

The following Croatian translation models can be customized.

| Model ID | Source          | Target         | Domain  | Customizable |
|----------|-----------------|----------------|---------|--------------|
| `hr-en`  | Croatian (`hr`) | English (`en`) | general | true         |

### Czech
{: #czech}

The following Czech translation models can be customized.

| Model ID | Source       | Target         | Domain  | Customizable |
|----------|--------------|----------------|---------|--------------|
| `cs-en`  | Czech (`cs`) | English (`en`) | general | true         |

### Danish
{: #danish}

The following Danish translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `da-en`  | Danish (`da`) | English (`en`) | general | true         |

### Dutch
{: #dutch}

The following Dutch translation models can be customized.

| Model ID | Source       | Target         | Domain  | Customizable |
|----------|--------------|----------------|---------|--------------|
| `nl-en`  | Dutch (`nl`) | English (`en`) | general | true         |

### English
{: #english}

The following English translation models can be customized.

| Model ID   | Source         | Target                        | Domain  | Customizable |
|------------|----------------|-------------------------------|---------|--------------|
| `en-ar`    | English (`en`) | Arabic (`ar`)                 | general | true         |
| `en-bg`    | English (`en`) | Bulgarian (`bg`)              | general | true         |
| `en-bn`    | English (`en`) | Bengali (`bn`)                | general | true         |
| `en-cs`    | English (`en`) | Czech (`cs`)                  | general | true         |
| `en-da`    | English (`en`) | Danish (`da`)                 | general | true         |
| `en-de`    | English (`en`) | German (`de`)                 | general | true         |
| `en-el`    | English (`en`) | Greek (`el`)                  | general | true         |
| `en-es`    | English (`en`) | Spanish (`es`)                | general | true         |
| `en-et`    | English (`en`) | Estonian (`et`)               | general | true         |
| `en-fi`    | English (`en`) | Finnish (`fi`)                | general | true         |
| `en-fr`    | English (`en`) | French (`fr`)                 | general | true         |
| `en-ga`    | English (`en`) | Irish (`ga`)                  | general | true         |
| `en-gu`    | English (`en`) | Gujarati (`gu`)               | general | true         |
| `en-he`    | English (`en`) | Hebrew (`he`)                 | general | true         |
| `en-hi`    | English (`en`) | Hindi (`hi`)                  | general | true         |
| `en-hr`    | English (`en`) | Croatian (`hr`)               | general | true         |
| `en-hu`    | English (`en`) | Hungarian (`hu`)              | general | true         |
| `en-id`    | English (`en`) | Indonesian (`id`)             | general | true         |
| `en-it`    | English (`en`) | Italian (`it`)                | general | true         |
| `en-ja`    | English (`en`) | Japanese (`ja`)               | general | true         |
| `en-ko`    | English (`en`) | Korean (`ko`)                 | general | true         |
| `en-lt`    | English (`en`) | Lithuanian (`lt`)             | general | true         |
| `en-lv`    | English (`en`) | Latvian (`lv`)                | general | true         |
| `en-ml`    | English (`en`) | Malayalam (`ml`)              | general | true         |
| `en-ms`    | English (`en`) | Malay (`ms`)                  | general | true         |
| `en-mt`    | English (`en`) | Maltese (`mt`)                | general | true         |
| `en-ne`    | English (`en`) | Nepali (`ne`)                 | general | true         |
| `en-nb`    | English (`en`) | Norwegian Bokmal (`nb`)       | general | true         |
| `en-nl`    | English (`en`) | Dutch (`nl`)                  | general | true         |
| `en-pl`    | English (`en`) | Polish (`pl`)                 | general | true         |
| `en-pt`    | English (`en`) | Portuguese (`pt`)             | general | true         |
| `en-ro`    | English (`en`) | Romanian (`ro`)               | general | true         |
| `en-ru`    | English (`en`) | Russian (`ru`)                | general | true         |
| `en-si`    | English (`en`) | Sinhala (`si`)                | general | true         |
| `en-sk`    | English (`en`) | Slovak (`sk`)                 | general | true         |
| `en-sl`    | English (`en`) | Slovenian (`sl`)              | general | true         |
| `en-sv`    | English (`en`) | Swedish (`sv`)                | general | true         |
| `en-ta`    | English (`en`) | Tamil (`ta`)                  | general | true         |
| `en-te`    | English (`en`) | Telugu (`te`)                 | general | true         |
| `en-th`    | English (`en`) | Thai (`th`)                   | general | true         |
| `en-tr`    | English (`en`) | Turkish (`tr`)                | general | true         |
| `en-uk`    | English (`en`) | Ukrainian (`uk`)              | general | true         |
| `en-ur`    | English (`en`) | Urdu (`ur`)                   | general | true         |
| `en-vi`    | English (`en`) | Vietnamese (`vi`)             | general | true         |
| `en-zh`    | English (`en`) | Simplified Chinese (`zh`)     | general | true         |
| `en-zh-TW` | English (`en`) | Traditional Chinese (`zh-TW`) | general | true         |

### Estonian
{: #estonian}

The following Estonian translation models can be customized.

| Model ID | Source          | Target         | Domain  | Customizable |
|----------|-----------------|----------------|---------|--------------|
| `et-en`  | Estonian (`et`) | English (`en`) | general | true         |

### Finnish
{: #finnish}

The following Finnish translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `fi-en`  | Finnish (`fi`) | English (`en`) | general | true         |

### French
{: #french}

The following French translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `fr-en`  | French (`fr`) | English (`en`) | general | true         |

### German
{: #german}

The following German translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `de-en`  | German (`de`) | English (`en`) | general | true         |
| `de-fr`  | German (`de`) | French (`fr`)  | general | true         |
| `de-it`  | German (`de`) | Italian (`it`) | general | true         |

### Greek
{: #greek}

The following Greek translation models can be customized.

| Model ID | Source       | Target         | Domain  | Customizable |
|----------|--------------|----------------|---------|--------------|
| `el-en`  | Greek (`el`) | English (`en`) | general | true         |

### Gujarati
{: #gujarati}

The following Gujarati translation models can be customized.

| Model ID | Source          | Target         | Domain  | Customizable |
|----------|-----------------|----------------|---------|--------------|
| `gu-en`  | Gujarati (`gu`) | English (`en`) | general | true         |

### Hebrew
{: #hebrew}

The following Hebrew translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `he-en`  | Hebrew (`he`) | English (`en`) | general | true         |

### Hindi
{: #hindi}

The following Hindi translation models can be customized.

| Model ID | Source       | Target         | Domain  | Customizable |
|----------|--------------|----------------|---------|--------------|
| `hi-en`  | Hindi (`hi`) | English (`en`) | general | true         |

### Hungarian
{: #hungarian}

The following Hungarian translation models can be customized.

| Model ID | Source           | Target         | Domain  | Customizable |
|----------|------------------|----------------|---------|--------------|
| `hu-en`  | Hungarian (`hu`) | English (`en`) | general | true         |

### Indonesian
{: #indonesian}

The following Indonesian translation models can be customized.

| Model ID | Source            | Target         | Domain  | Customizable |
|----------|-------------------|----------------|---------|--------------|
| `id-en`  | Indonesian (`id`) | English (`en`) | general | true         |

### Irish
{: #irish}

The following Irish translation models can be customized.

| Model ID | Source       | Target         | Domain  | Customizable |
|----------|--------------|----------------|---------|--------------|
| `ga-en`  | Irish (`ga`) | English (`en`) | general | true         |

### Italian
{: #italian}

The following Italian translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `it-de`  | Italian (`it`) | German (`de`)  | general | true         |
| `it-en`  | Italian (`it`) | English (`en`) | general | true         |

### Japanese
{: #japanese}

The following Japanese translation models can be customized.

| Model ID | Source          | Target         | Domain  | Customizable |
|----------|-----------------|----------------|---------|--------------|
| `ja-en`  | Japanese (`ja`) | English (`en`) | general | true         |

### Korean
{: #korean}

The following Korean translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `ko-en`  | Korean (`ko`) | English (`en`) | general | true         |

### Latvian
{: #latvian}

The following Latvian translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `lv-en`  | Latvian (`lv`) | English (`en`) | general | true         |

### Lithuanian
{: #lithuanian}

The following Lithuanian translation models can be customized.

| Model ID | Source            | Target         | Domain  | Customizable |
|----------|-------------------|----------------|---------|--------------|
| `lt-en`  | Lithuanian (`lt`) | English (`en`) | general | true         |

### Malay
{: #malay}

The following Malay translation models can be customized.

| Model ID | Source       | Target         | Domain  | Customizable |
|----------|--------------|----------------|---------|--------------|
| `ms-en`  | Malay (`ms`) | English (`en`) | general | true         |

### Malayalam
{: #malayalam}

The following Malayalam translation models can be customized.

| Model ID | Source           | Target         | Domain  | Customizable |
|----------|------------------|----------------|---------|--------------|
| `ml-en`  | Malayalam (`ml`) | English (`en`) | general | true         |

### Maltese
{: #maltese}

The following Maltese translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `mt-en`  | Maltese (`mt`) | English (`en`) | general | true         |

### Nepali
{: #nepali}

The following Nepali translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `ne-en`  | Nepali (`ne`) | English (`en`) | general | true         |

### Norwegian Bokmål
{: #norwegian-bokmal}

The following Norwegian Bokmål translation models can be customized.

| Model ID | Source                  | Target         | Domain  | Customizable |
|----------|-------------------------|----------------|---------|--------------|
| `nb-en`  | Norwegian Bokmal (`nb`) | English (`en`) | general | true         |

### Polish
{: #polish}

The following Polish translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `pl-en`  | Polish (`pl`) | English (`en`) | general | true         |

### Portuguese
{: #portuguese}

The following Portuguese translation models can be customized.

| Model ID | Source            | Target         | Domain  | Customizable |
|----------|-------------------|----------------|---------|--------------|
| `pt-en`  | Portuguese (`pt`) | English (`en`) | general | true         |

### Romanian
{: #romanian}

The following Romanian translation models can be customized.

| Model ID | Source            | Target         | Domain  | Customizable |
|----------|-------------------|----------------|---------|--------------|
| `ro-en`  | Romanian (`ro`) | English (`en`) | general | true         |

### Russian
{: #russian}

The following Russian translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `ru-en`  | Russian (`ru`) | English (`en`) | general | true         |

### Sinhala
{: #sinhala}

The following Sinhala translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `si-en`  | Sinhala (`si`) | English (`en`) | general | true         |

### Slovak
{: #slovak}

The following Slovak translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `sk-en`  | Slovak (`sk`) | English (`en`) | general | true         |

### Slovenian
{: #slovenian}

The following Slovenian translation models can be customized.

| Model ID | Source           | Target         | Domain  | Customizable |
|----------|------------------|----------------|---------|--------------|
| `sl-en`  | Slovenian (`sl`) | English (`en`) | general | true         |

### Spanish
{: #spanish}

The following Spanish translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `es-ca`  | Spanish (`es`) | Catalan (`ca`) | general | true         |
| `es-en`  | Spanish (`es`) | English (`en`) | general | true         |
| `es-fr`  | Spanish (`es`) | French (`fr`)  | general | true         |

### Swedish
{: #swedish}

The following Swedish translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `sv-en`  | Swedish (`sv`) | English (`en`) | general | true         |

### Tamil
{: #tamil}

The following Tamil translation models can be customized.

| Model ID | Source       | Target         | Domain  | Customizable |
|----------|--------------|----------------|---------|--------------|
| `ta-en`  | Tamil (`ta`) | English (`en`) | general | true         |

### Telugu
{: #telugu}

The following Telugu translation models can be customized.

| Model ID | Source        | Target         | Domain  | Customizable |
|----------|---------------|----------------|---------|--------------|
| `te-en`  | Telugu (`te`) | English (`en`) | general | true         |

### Thai
{: #thai}

The following Thai translation models can be customized.

| Model ID | Source      | Target         | Domain  | Customizable |
|----------|-------------|----------------|---------|--------------|
| `th-en`  | Thai (`th`) | English (`en`) | general | true         |

### Turkish
{: #turkish}

The following Turkish translation models can be customized.

| Model ID | Source         | Target         | Domain  | Customizable |
|----------|----------------|----------------|---------|--------------|
| `tr-en`  | Turkish (`tr`) | English (`en`) | general | true         |

### Ukrainian
{: #ukrainian}

The following Ukrainian translation models can be customized.

| Model ID | Source           | Target         | Domain  | Customizable |
|----------|------------------|----------------|---------|--------------|
| `uk-en`  | Ukrainian (`uk`) | English (`en`) | general | true         |

### Urdu
{: #urdu}

The following Urdu translation models can be customized.

| Model ID | Source      | Target         | Domain  | Customizable |
|----------|-------------|----------------|---------|--------------|
| `ur-en`  | Urdu (`ur`) | English (`en`) | general | true         |

### Vietnamese
{: #vietnamese}

The following Vietnamese translation models can be customized.

| Model ID | Source            | Target         | Domain  | Customizable |
|----------|-------------------|----------------|---------|--------------|
| `vi-en`  | Vietnamese (`vi`) | English (`en`) | general | true         |

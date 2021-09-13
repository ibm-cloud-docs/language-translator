---

copyright:
  years: 2015, 2020
lastupdated: "2020-10-30"

keywords: translation models,list translation models,customizable models

subcollection: language-translator

---

{{site.data.keyword.attribute-definition-list}}

# Supported languages for translation
{: #translation-models}

{{site.data.keyword.languagetranslatorfull}} supports a wide array of translatable languages. It also supports customization of many translation models.
{: shortdesc}

## Listing supported languages for translation
{: #list-languages}

You can use the [List supported languages](https://{DomainName}/apidocs/language-translator#listlanguages){: external} method to retrieve the list of supported languages for translation. The following example calls the method:

```sh
curl -X GET --user "apikey:{apikey}" \
"{url}/v3/languages?version=2018-05-01"
```
{: pre}

The method returns a complete list of all supported languages, sorted by `language` code (for example, `af`, `ar`). In addition to basic information about each language, the response indicates whether the language is `supported_as_source` for translation and `supported_as_target` for translation. It also lists whether the language is `identifiable`.

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

The list of support languages is long, reporting more than 75 languages.

## List of supported languages
{: #list-languages-supported}

The following table list the translatable languages. The service can translate from the following languages to any other language in the list (with the exception of Basque and Catalan).

Not all language combinations that are supported for translation are also customizable. Usually, only the combinations with English as source or target language are customizable. Click the name of a language to see the customizable translation models for that language.

|Language                                     | Language code |Language                             | Language code |
|---------------------------------------------|:-------------:|-------------------------------------|:-------------:|
|[Arabic](#arabic)                            |`ar`         |[Korean](#korean)                    |`ko`   |
|[Basque](#basque)  **[1]**                   |`eu`         |[Latvian](#latvian)                  |`lv`   |
|[Bengali](#bengali)                          |`bn`         |[Lithuanian](#lithuanian)            |`lt`   |
|[Bosnian](#bosnian)                          |`bs`         |[Malay](#malay)                      |`ms`   |
|[Bulgarian](#bulgarian)                      |`bg`         |[Malayalam](#malayalam)              |`ml`   |
|[Catalan](#catalan) **[1]**                  |`ca`         |[Maltese](#maltese)                  |`mt`   |
|[Chinese (Simplified)](#chinese-simplified)  |`zh`         |[Montenegrin](#montenegrin) **[2]**  |`cnr`  |
|[Chinese (Traditional)](#chinese-traditional)|`zh-TW`      |[Nepali](#nepali)                    |`ne`   |
|[Croatian](#croatian)                        |`hr`         |[Norwegian Bokmål](#norwegian-bokmal)|`nb`   |
|[Czech](#czech)                              |`cs`         |[Polish](#polish)                    |`pl`   |
|[Danish](#danish)                            |`da`         |[Portuguese](#portuguese)            |`pt`   |
|[Dutch](#dutch)                              |`nl`         |[Romanian](#romanian)                |`ro`   |
|[English](#english)                          |`en`         |[Russian](#russian)                  |`ru`   |
|[Estonian](#estonian)                        |`et`         |[Serbian](#serbian) **[3]**          |`sr`   |
|[Finnish](#finnish)                          |`fi`         |[Sinhala](#sinhala)                  |`si`   |
|[French](#french)                            |`fr`         |[Slovak](#slovak)                    |`sk`   |
|[French (Canadian)](#french-canadian)        |`fr`         |[Slovenian](#slovenian)              |`sl`   |
|[German](#german)                            |`de`         |[Spanish](#spanish)                  |`es`   |
|[Greek](#greek)                              |`el`         |[Swedish](#swedish)                  |`sv`   |
|[Gujarati](#gujarati)                        |`gu`         |[Tamil](#tamil)                      |`ta`   |
|[Hebrew](#hebrew)                            |`he`         |[Telugu](#telugu)                    |`te`   |
|[Hindi](#hindi)                              |`hi`         |[Thai](#thai)                        |`th`   |
|[Hungarian](#hungarian)                      |`hu`         |[Turkish](#turkish)                  |`tr`   |
|[Irish](#irish)                              |`ga`         |[Ukrainian](#ukrainian)              |`uk`   |
|[Indonesian](#indonesian)                    |`id`         |[Urdu](#urdu)                        |`ur`   |
|[Italian](#italian)                          |`it`         |[Vietnamese](#vietnamese)            |`vi`   |
|[Japanese](#japanese)                        |`ja`         |[Welsh](#welsh)                      |`cy`   |
{: caption="Table 1. Translatable languages"}

Notes:

1.  Basque and Catalan are supported only for translation to and from Spanish.
2.  The translation models for Montenegrin are not customizable at this time.
3.  Serbian translation support is based on the Cyrillic alphabet. (Bosnian, Croatian, and Montenegrin translation support is based on the Latin alphabet.)

## Listing supported translation models for customization
{: #customizable-models}

You can use the [List models](https://{DomainName}/apidocs/language-translator#listmodels){: external} method to view the available translation models and any custom models that you created. You can filter results by language with the `source` and `target` parameters. The following example lists models that can translate from English to Spanish.

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

The following Arabic translation model can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `ar-en`  | Arabic (`ar`) | English (`en`) | general |
{: caption="Table 2. Arabic translation model"}

### Basque
{: #basque}

The following Basque translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `eu-es`  | Basque (`eu`)  | Spanish (`es`) | general |
{: caption="Table 3. Basque translation model"}

### Bengali
{: #bengali}

The following Bengali translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `bn-en`  | Bengali (`bn`) | English (`en`) | general |
{: caption="Table 4. Bengali translation model"}

### Bosnian
{: #bosnian}

The following Bosnian translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `bs-en`  | Bosnian (`bs`) | English (`en`) | general |
{: caption="Table 5. Bosnian translation model"}

### Bulgarian
{: #bulgarian}

The following Bulgarian translation model can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|------------------|----------------|---------|
| `bg-en`  | Bulgarian (`bg`) | English (`en`) | general |
{: caption="Table 6. Bulgarian translation model"}

### Catalan
{: #catalan}

The following Catalan translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `ca-es`  | Catalan (`ca`) | Spanish (`es`) | general |
{: caption="Table 7. Catalan translation model"}

### Chinese (Simplified)
{: #chinese-simplified}

The following Chinese (Simplified) translation model can be customized.

| Model ID | Source                    | Target         | Domain  |
|----------|---------------------------|----------------|---------|
| `zh-en`  | Simplified Chinese (`zh`) | English (`en`) | general |
{: caption="Table 8. Simplified Chinese translation model"}

### Chinese (Traditional)
{: #chinese-traditional}

The following Chinese (Traditional) translation model can be customized.

| Model ID   | Source                       | Target         | Domain  |
|------------|------------------------------|----------------|---------|
| `zh-TW-en` | Simplified Chinese (`zh-TW`) | English (`en`) | general |
{: caption="Table 9. Traditional Chinese translation model"}

### Croatian
{: #croatian}

The following Croatian translation model can be customized.

| Model ID | Source          | Target         | Domain  |
|----------|-----------------|----------------|---------|
| `hr-en`  | Croatian (`hr`) | English (`en`) | general |
{: caption="Table 10. Croatian translation model"}

### Czech
{: #czech}

The following Czech translation model can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `cs-en`  | Czech (`cs`) | English (`en`) | general |
{: caption="Table 11. Czech translation model"}

### Danish
{: #danish}

The following Danish translation model can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `da-en`  | Danish (`da`) | English (`en`) | general |
{: caption="Table 12. Danish translation model"}

### Dutch
{: #dutch}

The following Dutch translation model can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `nl-en`  | Dutch (`nl`) | English (`en`) | general |
{: caption="Table 13. Dutch translation model"}

### English
{: #english}

The following English translation models can be customized.

The English-to-Montenegrin translation model (`en-cnr`) is not customizable at this time. It can be used for translation but **cannot** be customized.
{: note}

| Model ID   | Source         | Target                        | Domain  |
|------------|----------------|-------------------------------|---------|
| `en-ar`    | English (`en`) | Arabic (`ar`)                 | general |
| `en-bg`    | English (`en`) | Bulgarian (`bg`)              | general |
| `en-bn`    | English (`en`) | Bengali (`bn`)                | general |
| `en-bs`    | English (`en`) | Bosnian (`bs`)                | general |
| `en-cnr`   | English (`en`) | Montenegrin (`cnr`)           | general |
| `en-cs`    | English (`en`) | Czech (`cs`)                  | general |
| `en-cy`    | English (`en`) | Welsh (`cy`)                  | general |
| `en-da`    | English (`en`) | Danish (`da`)                 | general |
| `en-de`    | English (`en`) | German (`de`)                 | general |
| `en-el`    | English (`en`) | Greek (`el`)                  | general |
| `en-es`    | English (`en`) | Spanish (`es`)                | general |
| `en-et`    | English (`en`) | Estonian (`et`)               | general |
| `en-fi`    | English (`en`) | Finnish (`fi`)                | general |
| `en-fr`    | English (`en`) | French (`fr`)                 | general |
| `en-fr-CA` | English (`en`) | Canadian French (`fr-CA`)     | general |
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
| `en-nb`    | English (`en`) | Norwegian Bokmål (`nb`)       | general |
| `en-nl`    | English (`en`) | Dutch (`nl`)                  | general |
| `en-pl`    | English (`en`) | Polish (`pl`)                 | general |
| `en-pt`    | English (`en`) | Portuguese (`pt`)             | general |
| `en-ro`    | English (`en`) | Romanian (`ro`)               | general |
| `en-ru`    | English (`en`) | Russian (`ru`)                | general |
| `en-si`    | English (`en`) | Sinhala (`si`)                | general |
| `en-sk`    | English (`en`) | Slovak (`sk`)                 | general |
| `en-sl`    | English (`en`) | Slovenian (`sl`)              | general |
| `en-sr`    | English (`en`) | Serbian (`sr`)                | general |
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
{: caption="Table 14. English translation models"}

### Estonian
{: #estonian}

The following Estonian translation model can be customized.

| Model ID | Source          | Target         | Domain  |
|----------|-----------------|----------------|---------|
| `et-en`  | Estonian (`et`) | English (`en`) | general |
{: caption="Table 15. Estonian translation model"}

### Finnish
{: #finnish}

The following Finnish translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `fi-en`  | Finnish (`fi`) | English (`en`) | general |
{: caption="Table 16. Finnish translation model"}

### French
{: #french}

The following French translation model can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|---------------------------|----------------|---------|
| `fr-en`  | French (`fr`)    | English (`en`) | general |
{: caption="Table 17. French translation model"}

### French (Canadian)
{: #french-canadian}

The following French (Canadian) translation model can be customized.

| Model ID   | Source                    | Target         | Domain  |
|------------|---------------------------|----------------|---------|
| `fr-CA-en` | Canadian French (`fr-CA`) | English (`en`) | general |
{: caption="Table 18. Canadian French translation model"}

### German
{: #german}

The following German translation models can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `de-en`  | German (`de`) | English (`en`) | general |
| `de-fr`  | German (`de`) | French (`fr`)  | general |
| `de-it`  | German (`de`) | Italian (`it`) | general |
{: caption="Table 19. German translation models"}

### Greek
{: #greek}

The following Greek translation model can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `el-en`  | Greek (`el`) | English (`en`) | general |
{: caption="Table 20. Greek translation model"}

### Gujarati
{: #gujarati}

The following Gujarati translation model can be customized.

| Model ID | Source          | Target         | Domain  |
|----------|-----------------|----------------|---------|
| `gu-en`  | Gujarati (`gu`) | English (`en`) | general |
{: caption="Table 21. Gujarati translation model"}

### Hebrew
{: #hebrew}

The following Hebrew translation model can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `he-en`  | Hebrew (`he`) | English (`en`) | general |
{: caption="Table 22. Hebrew translation model"}

### Hindi
{: #hindi}

The following Hindi translation model can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `hi-en`  | Hindi (`hi`) | English (`en`) | general |
{: caption="Table 23. Hindi translation model"}

### Hungarian
{: #hungarian}

The following Hungarian translation model can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|------------------|----------------|---------|
| `hu-en`  | Hungarian (`hu`) | English (`en`) | general |
{: caption="Table 24. Hungarian translation model"}

### Indonesian
{: #indonesian}

The following Indonesian translation model can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `id-en`  | Indonesian (`id`) | English (`en`) | general |
{: caption="Table 25. Indonesian translation model"}

### Irish
{: #irish}

The following Irish translation model can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `ga-en`  | Irish (`ga`) | English (`en`) | general |
{: caption="Table 26. Irish translation model"}

### Italian
{: #italian}

The following Italian translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `it-de`  | Italian (`it`) | German (`de`)  | general |
| `it-en`  | Italian (`it`) | English (`en`) | general |
{: caption="Table 27. Italian translation models"}

### Japanese
{: #japanese}

The following Japanese translation model can be customized.

| Model ID | Source          | Target         | Domain  |
|----------|-----------------|----------------|---------|
| `ja-en`  | Japanese (`ja`) | English (`en`) | general |
{: caption="Table 28. Japanese translation model"}

### Korean
{: #korean}

The following Korean translation model can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `ko-en`  | Korean (`ko`) | English (`en`) | general |
{: caption="Table 29. Korean translation model"}

### Latvian
{: #latvian}

The following Latvian translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `lv-en`  | Latvian (`lv`) | English (`en`) | general |
{: caption="Table 30. Latvian translation model"}

### Lithuanian
{: #lithuanian}

The following Lithuanian translation model can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `lt-en`  | Lithuanian (`lt`) | English (`en`) | general |
{: caption="Table 31. Lithuanian translation model"}

### Malay
{: #malay}

The following Malay translation model can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `ms-en`  | Malay (`ms`) | English (`en`) | general |
{: caption="Table 32. Malay translation model"}

### Malayalam
{: #malayalam}

The following Malayalam translation model can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|------------------|----------------|---------|
| `ml-en`  | Malayalam (`ml`) | English (`en`) | general |
{: caption="Table 33. Malayalam translation model"}

### Maltese
{: #maltese}

The following Maltese translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `mt-en`  | Maltese (`mt`) | English (`en`) | general |
{: caption="Table 34. Maltese translation model"}

### Montenegrin
{: #montenegrin}

The following Montenegrin translation model cannot be customized.

| Model ID | Source              | Target         | Domain  |
|----------|---------------------|----------------|---------|
| `cnr-en` | Montenegrin (`cnr`) | English (`en`) | general |
{: caption="Table 35. Montenegrin translation model"}

The Montenegrin-to-English translation model (`cnr-en`) is not customizable at this time. It can be used for translation but **cannot** be customized.
{: note}

### Nepali
{: #nepali}

The following Nepali translation model can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `ne-en`  | Nepali (`ne`) | English (`en`) | general |
{: caption="Table 36. Nepali translation model"}

### Norwegian Bokmål
{: #norwegian-bokmal}

The following Norwegian Bokmål translation model can be customized.

| Model ID | Source                  | Target         | Domain  |
|----------|-------------------------|----------------|---------|
| `nb-en`  | Norwegian Bokmål (`nb`) | English (`en`) | general |
{: caption="Table 37. Norwegian Bokmål translation model"}

### Polish
{: #polish}

The following Polish translation model can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `pl-en`  | Polish (`pl`) | English (`en`) | general |
{: caption="Table 38. Polish translation model"}

### Portuguese
{: #portuguese}

The following Portuguese translation model can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `pt-en`  | Portuguese (`pt`) | English (`en`) | general |
{: caption="Table 39. Portuguese translation model"}

### Romanian
{: #romanian}

The following Romanian translation model can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `ro-en`  | Romanian (`ro`)   | English (`en`) | general |
{: caption="Table 40. Romanian translation model"}

### Russian
{: #russian}

The following Russian translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `ru-en`  | Russian (`ru`) | English (`en`) | general |
{: caption="Table 41. Russian translation model"}

### Serbian
{: #serbian}

The following Serbian translation model can be customized. The service supports translation for Serbian based on the Cyrillic alphabet, not the Latin alphabet.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `sr-en`  | Serbian (`sr`) | English (`en`) | general |
{: caption="Table 42. Serbian translation model"}

### Sinhala
{: #sinhala}

The following Sinhala translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `si-en`  | Sinhala (`si`) | English (`en`) | general |
{: caption="Table 43. Sinhala translation model"}

### Slovak
{: #slovak}

The following Slovak translation model can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `sk-en`  | Slovak (`sk`) | English (`en`) | general |
{: caption="Table 44. Slovak translation model"}

### Slovenian
{: #slovenian}

The following Slovenian translation model can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|------------------|----------------|---------|
| `sl-en`  | Slovenian (`sl`) | English (`en`) | general |
{: caption="Table 45. Slovenian translation model"}

### Spanish
{: #spanish}

The following Spanish translation models can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `es-ca`  | Spanish (`es`) | Catalan (`ca`) | general |
| `es-en`  | Spanish (`es`) | English (`en`) | general |
| `es-fr`  | Spanish (`es`) | French (`fr`)  | general |
| `es-eu`  | Spanish (`es`) | Basque (`eu`)  | general |
{: caption="Table 46. Spanish translation models"}

### Swedish
{: #swedish}

The following Swedish translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `sv-en`  | Swedish (`sv`) | English (`en`) | general |
{: caption="Table 47. Swedish translation model"}

### Tamil
{: #tamil}

The following Tamil translation model can be customized.

| Model ID | Source       | Target         | Domain  |
|----------|--------------|----------------|---------|
| `ta-en`  | Tamil (`ta`) | English (`en`) | general |
{: caption="Table 48. Tamil translation model"}

### Telugu
{: #telugu}

The following Telugu translation model can be customized.

| Model ID | Source        | Target         | Domain  |
|----------|---------------|----------------|---------|
| `te-en`  | Telugu (`te`) | English (`en`) | general |
{: caption="Table 49. Telugu translation model"}

### Thai
{: #thai}

The following Thai translation model can be customized.

| Model ID | Source      | Target         | Domain  |
|----------|-------------|----------------|---------|
| `th-en`  | Thai (`th`) | English (`en`) | general |
{: caption="Table 50. Thai translation model"}

### Turkish
{: #turkish}

The following Turkish translation model can be customized.

| Model ID | Source         | Target         | Domain  |
|----------|----------------|----------------|---------|
| `tr-en`  | Turkish (`tr`) | English (`en`) | general |
{: caption="Table 51. Turkish translation model"}

### Ukrainian
{: #ukrainian}

The following Ukrainian translation model can be customized.

| Model ID | Source           | Target         | Domain  |
|----------|------------------|----------------|---------|
| `uk-en`  | Ukrainian (`uk`) | English (`en`) | general |
{: caption="Table 52. Ukrainian translation model"}

### Urdu
{: #urdu}

The following Urdu translation model can be customized.

| Model ID | Source      | Target         | Domain  |
|----------|-------------|----------------|---------|
| `ur-en`  | Urdu (`ur`) | English (`en`) | general |
{: caption="Table 53. Urdu translation model"}

### Vietnamese
{: #vietnamese}

The following Vietnamese translation model can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `vi-en`  | Vietnamese (`vi`) | English (`en`) | general |
{: caption="Table 54. Vietnamese translation model"}

### Welsh
{: #welsh}

The following Welsh translation model can be customized.

| Model ID | Source            | Target         | Domain  |
|----------|-------------------|----------------|---------|
| `cy-en`  | Welsh (`cy`)      | English (`en`) | general |
{: caption="Table 55. Welsh translation model"}

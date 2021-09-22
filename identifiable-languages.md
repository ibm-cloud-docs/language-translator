---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-22"

keywords: identify language,identifiable languages

subcollection: language-translator

---

{{site.data.keyword.attribute-definition-list}}

# Identifiable languages
{: #identifiable-languages}

{{site.data.keyword.languagetranslatorfull}} can identify a variety of languages.
{: shortdesc}

## Listing identifiable languages
{: #list-identifiable}

You can use the [List identifiable languages](https://{DomainName}/apidocs/language-translator#listidentifiablelanguages) method to retrieve the list of identifiable languages. The following example calls the method:

```sh
curl -X GET --user "apikey:{apikey}" \
"{url}/v3/identifiable_languages?version=2018-05-01"
```
{: pre}

The method returns a complete list of all identifiable languages, sorted by `language` code (for example, `af`, `ar`). The output includes the `name` of the language.

```json
{
  "languages": [
    {
      "language": "af",
      "name": "Afrikaans"
    },
    {
      "language": "ar",
      "name": "Arabic"
    },
    {
      "language": "az",
      "name": "Azerbaijani"
    },
    {
      "language": "ba",
      "name": "Bashkir"
    }
    . . .
  ]
}
```
{: codeblock}

## List of identifiable languages
{: #list-languages-identifiable}

The following table list the identifiable languages. The table is sorted by language name and provides the language code for each language.

| Language name                        | Language code | Language name                        | Language code |
|--------------------------------------|:-------------:|--------------------------------------|:-------------:|
| Afrikaans                            | `af`          | Kirghiz                              | `ky`          |
| Albanian                             | `sq`          | Korean                               | `ko`          |
| Arabic                               | `ar`          | Kurdish                              | `ku`          |
| Armenian                             | `hy`          | Lao                                  | `lo`          |
| Azerbaijani                          | `az`          | Latvian                              | `lv`          |
| Bashkir                              | `ba`          | Lithuanian                           | `lt`          |
| Basque                               | `eu`          | Malay                                | `ms`          |
| Belarusian                           | `be`          | Malayalam                            | `ml`          |
| Bengali                              | `bn`          | Maltese                              | `mt`          |
| Bulgarian                            | `bg`          | Marathi                              | `mr`          |
| Burmese                              | `my`          | Mongolian                            | `mn`          |
| Catalan                              | `ca`          | Nepali                               | `ne`          |
| Central Khmer                        | `km`          | Norwegian Bokmål                     | `nb`          |
| Chinese (Simplified)                 | `zh`          | Norwegian Nynorsk                    | `nn`          |
| Chinese (Traditional)                | `zh-TW`       | Punjabi                              | `pa`          |
| Chuvash                              | `cv`          | Punjabi  \n (Shahmukhi script, Pakistan) | `pa-PK`       |
| Croatian                             | `hr`          | Persian                              | `fa`          |
| Czech                                | `cs`          | Polish                               | `pl`          |
| Danish                               | `da`          | Portuguese                           | `pt`          |
| Dutch                                | `nl`          | Pushto                               | `ps`          |
| English                              | `en`          | Romanian                             | `ro`          |
| Esperanto                            | `eo`          | Russian                              | `ru`          |
| Estonian                             | `et`          | Serbian                              | `sr`          |
| Finnish                              | `fi`          | Sinhala                              | `si`          |
| French                               | `fr`          | Slovakian                            | `sk`          |
| Georgian                             | `ka`          | Slovenian                            | `sl`          |
| German                               | `de`          | Somali                               | `so`          |
| Greek                                | `el`          | Spanish                              | `es`          |
| Gujarati                             | `gu`          | Swedish                              | `sv`          |
| Haitian                              | `ht`          | Tagalog                              | `tl`          |
| Hebrew                               | `he`          | Tamil                                | `ta`          |
| Hindi                                | `hi`          | Telugu                               | `te`          |
| Hungarian                            | `hu`          | Thai                                 | `th`          |
| Icelandic                            | `is`          | Turkish                              | `tr`          |
| Irish                                | `ga`          | Ukrainian                            | `uk`          |
| Italian                              | `it`          | Urdu                                 | `ur`          |
| Japanese                             | `ja`          | Vietnamese                           | `vi`          |
| Kazakh                               | `kk`          | Welsh                                | `cy`          |
{: caption="Table 1. Identifiable languages"}

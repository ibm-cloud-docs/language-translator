---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-31"

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

# About

With the {{site.data.keyword.languagetranslatorfull}} service, you can create an application that identifies the language of input text and uses a domain-specific linguistic model to translate the text into another language.
{: shortdesc}

To translate industry-specific jargon or other types of specialized terminology, you can customize the linguistic model to optimize it for your needs.

**Note:** The IBM Watson&trade; Language Translation service was rebranded as the {{site.data.keyword.languagetranslatorshort}} service. The {{site.data.keyword.languagetranslatorshort}} service provides the same capabilities as the Language Translation service, but with simpler pricing. For information about migrating applications from the Language Translation service to the {{site.data.keyword.languagetranslatorshort}} service, see the [Migrating from Language Translation](/docs/services/language-translator/migrating.html) documentation.

## How to use the service

Use the service to identify the language of text, and to translate text from one language to another. For example, pass an English word, such as *Hello*, and the service can identify it as English. Or translate the English greeting into its Spanish equivalent, *Hola*.

To teach the service to perform domain-specific translations, you can make the following enhancements to one of the linguistic models that is provided with the service:

- Add your own glossary of terms or phrases in a source and target language. The glossary can supplement standard translations or be identified as the only terms to use.
- Upload a large body of text in your target language to serve as a language sample. The service can evaluate the sample and use what it learns to improve the quality of its translation.

    For more information about customization, see [Customizing your model](/docs/services/language-translator/customizing.html).

## Quick links

- Try out a working [demo ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://language-translator-demo.mybluemix.net/){: new_window}.
- View the list of [SDKs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/developer-tools.html){: new_window}.
- Interact with the API through the [API Explorer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){: new_window}.

## Supported languages

The linguistic models that are provided with the service can perform translations between the following languages:

- **News**: Targeted at news articles and transcripts.  Translate English to and from Arabic, Brazilian Portuguese, French, German, Italian, Japanese, Korean, and Spanish. You can also translate Spanish to and from French.
- **Conversational**: Targeted at conversational colloquialisms. Translate English to and from Arabic, Brazilian Portuguese, French, Italian, and Spanish.
- **Patents**: Targeted at technical and legal terminology. Translate Brazilian Portuguese, Chinese, Korean, and Spanish to English.

The `/identify` endpoint can recognize the following languages:

- Afrikaans
- Albanian
- Arabic
- Armenian
- Azerbaijani
- Bashkir
- Basque
- Belarusian
- Bengali
- Bosnian
- Bulgarian
- Central Khmer
- Chinese
- Chuvash
- Czech
- Danish
- Dutch
- English
- Esperanto
- Estonian
- Finnish
- French
- Georgian
- German
- Greek
- Gujarati
- Haitian
- Hebrew
- Hindi
- Hungarian
- Icelandic
- Indonesian
- Italian
- Japanese
- Kazakh
- Kirghiz
- Korean
- Kurdish
- Latvian
- Lithuanian
- Malayalam
- Mongolian
- Norwegian Bokmal
- Norwegian Nynorsk
- Panjabi
- Persian
- Polish
- Portuguese
- Pushto
- Romanian
- Russian
- Slovakian
- Somali
- Spanish
- Swedish
- Tamil
- Telugu
- Traditional Chinese
- Turkish
- Ukrainian
- Urdu
- Vietnamese


---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

---
<!-- Attribute definitions -->
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Guía de aprendizaje de iniciación
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} le permite traducir de forma programática texto en dominios de noticias, conversacionales y patentes. Esta guía de aprendizaje describe los mandatos para traducir algún contenido de ejemplo del inglés al español y elegir el dominio.
{:shortdesc}

## Antes de empezar
{: #prerequisites}

- Cree una instancia del servicio:
    - {: download} Si ve esto, significa que ha creado la instancia del servicio. Ahora debe obtener las credenciales.
    - Cree un proyecto a partir de un servicio:
        1.  Vaya a la página [Servicios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.{DomainName}/developer/watson/services){: new_window} de la consola del desarrollador de {{site.data.keyword.watson}}.
        1.  Seleccione {{site.data.keyword.languagetranslatorshort}}, pulse **Añadir servicios** y regístrese para obtener una cuenta gratuita de {{site.data.keyword.Bluemix_notm}} o inicie sesión.
        1.  Escriba `language-tutorial` como nombre de proyecto y pulse **Crear proyecto**.
- Copie las credenciales para autenticarse en la instancia de servicio:
    - {: download} En el panel de control del servicio (lo que está viendo):
        1.  Pulse el separador **Credenciales de servicio**.
        1.  Pulse **Ver credenciales** bajo **Acciones**.
        1.  Copie los valores `username`, `password` y `url`.
        {: download}
    - Desde el proyecto **language-tutorial** en la consola del desarrollador, copie los valores `username`, `password` y `url` para `"language_translator"` de la sección **Credenciales**.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Si utiliza {{site.data.keyword.Bluemix_dedicated_notm}}, cree la instancia de servicio desde la página de [{{site.data.keyword.languagetranslatorshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.{DomainName}/catalog/services/language-translator/){: new_window} en el catálogo. Para obtener detalles sobre cómo encontrar las credenciales de servicio, consulte [Credenciales de servicio para servicios de Watson ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Paso 1: Traducir texto
{: #translate-text}

Utilice el siguiente ejemplo para traducir "Hello, world!" del inglés al español. Sustituya `{username}` y `{password}` por las credenciales de servicio que ha copiado en el paso anterior.

```bash
curl -X POST --user {username}:{password} --header "Accept: application/json" --data "{\"text\":\"Hello, world\",\"source\":\"en\",\"target\":\"es\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{:codeblock}

Ahora hay disponible una previsualización de nuevos modelos NMT (traducción automática neuronal) que ofrecen mejores traducciones. Para obtener más detalles, consulte las [notas del release](release-notes.html#12-january-2018).
{: tip}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  version: 'v2',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
});
language_translator.translate({
    text: 'Hello, world!',
    source: 'en',
    target: 'es'
  },
  function(err, translation) {
    if (err)
      console.log(err)
    else
      console.log(translation);
});
```
{:node}
{:codeblock} -->

<!-- ```java
LanguageTranslator service = new LanguageTranslator();
service.setUsernameAndPassword("username","password");

TranslationResult result = service.translate("Hello, world!", "en", "es");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
    username="username",
    password="password")

translation = language_translator.translate(
    text="Hello, world!",
    source="en",
    target="es"
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->


## Paso 2: Pruebe un modelo específico de dominio
{: #specify-model}

{{site.data.keyword.languagetranslatorshort}} dispone de modelos especializados para dominios de noticias, conversacionales y patentes. Cuando especifica los idiomas `source` (origen) y `target` (destino) en el paso 2, el servicio normalmente utiliza de forma predeterminada el modelo de dominio de noticias para la traducción. Para utilizar un modelo específico del dominio, especifique el `model_id` en lugar de los idiomas `source` (origen) y `target` (destino). También puede utilizar un [modelo personalizado](customizing.html), si ha creado uno.

_No se da soporte a los modelos específicos de dominio en solicitudes que contienen la [cabecera de previsualización NMT](release-notes.html#12-january-2018)._

El siguiente ejemplo traduce "Hey world, whats up?" con el modelo conversacional del inglés al español. Sustituya `{username}` y `{password}` por su información:

```bash
curl -X POST --user {username}:{password} --header "Content-Type: application/json" --header "Accept: application/json" --data "{\"text\":\"Hey world, whats up?\",\"model_id\":\"en-es-conversational\"}" "https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{:codeblock}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
  version: 'v2',
});
language_translator.translate({
    text: 'Hey, world! What's up?',
    model_id: 'en-es-conversational'
  },
  function(err, translation) {
    if (err)
      console.log(err)
    else
      console.log(translation);
});
```
{:node}
{:codeblock} -->

<!-- ```java
LanguageTranslator service = new LanguageTranslator();
service.setUsernameAndPassword("username","password");

TranslationResult result = service.translate("Hey, world! What's up?", "en-es-conversational");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```python
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
  username="username",
  password="password"
)

translation = language_translator.translate(
  text="Hey, world! What's up?",
  model_id="en-es-conversational"
)
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->

Puede utilizar el método [Lista de modelos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models){: new_window} para ver los modelos disponibles para la instancia de servicio.
{:tip}

## Pasos siguientes
{: #next-steps}

- Aprenda a [personalizar](/docs/services/language-translator/customizing.html) {{site.data.keyword.languagetranslatorshort}} para que funcione con su caso de uso.
- Consulte la [Referencia de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){:new_window}.
- Interactúe con la API en el [Explorador de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){:new_window}.
- Pruebe la [app de ejemplo de Node.js ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/watson-developer-cloud/language-translator-nodejs){:new_window}.

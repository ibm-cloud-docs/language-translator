---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-04"

---
<!-- Attribute definitions -->
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Guía de aprendizaje de iniciación
{: #gettingstarted}

{{site.data.keyword.languagetranslatorfull}} le permite traducir texto mediante programación de un idioma a otro.
{:shortdesc}
{: hide-dashboard}

En esta guía de aprendizaje se muestran los mandatos para traducir texto de inglés a español e identificar el idioma de un ejemplo de texto.

## Antes de empezar
{: #prerequisites}

- {: hide-dashboard} Cree una instancia del servicio:
    1.  {: hide-dashboard} Vaya a la página [{{site.data.keyword.languagetranslatorshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/catalog/services/language-translator){: new_window} en el catálogo de {{site.data.keyword.Bluemix_notm}}.
    2.  Regístrese para obtener una cuenta de {{site.data.keyword.Bluemix_notm}} gratuita o inicie una sesión.
    3.  Pulse **Crear**.
- Copie las credenciales para autenticarse en la instancia de servicio:
    1.  En la página **Gestionar**, pulse **Mostrar** para visualizar las credenciales.
    2.  Copie los valores de `Clave de API` y `URL`.
- Asegúrese de que tiene el mandato `curl`:
    - Los ejemplos utilizan el mandato `curl` para llamar a métodos de la interfaz HTTP. Instale la versión correspondiente a su sistema operativo desde [curl.haxx.se ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://curl.haxx.se/){: new_window}. Instale la versión que da soporte al protocolo SSL (Secure Sockets Layer). Asegúrese de incluir el archivo binario instalado en la variable de entorno `PATH`.

Esta guía de aprendizaje utiliza la clave de API para realizar la autenticación. Para los usos de producción, asegúrese de revisar las [mejores prácticas](/docs/services/watson/apikey-bp.html#api-bp) de la clave de API.
{: tip}

## Paso 1: Traducir texto
{: #translate-text}

Utilice el siguiente ejemplo para traducir dos frases, "Hello, world!" y "How are you?" del inglés al español. <span class="hide-dashboard">Sustituya `{apikey}` y `{url}` por sus credenciales de servicio.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## Paso 2: Identificar el idioma
{: #identify-language}

Utilice el ejemplo siguiente para identificar el idioma del texto. <span class="hide-dashboard">Sustituya `{apikey}` y `{url}` por sus credenciales de servicio.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## Siguientes pasos
{: #next-steps}

- Aprenda a [personalizar](/docs/services/language-translator?topic=language-translator-customizing) {{site.data.keyword.languagetranslatorshort}} para que funcione con su caso de uso
- Intente [traducir documentos (Beta)](/docs/services/language-translator?topic=language-translator-document-translator-tutorial)
- Vea la [Referencia de API](https://{DomainName}/apidocs/language-translator)
- Explore las [aplicaciones de ejemplo](/docs/services/language-translator?topic=language-translator-sample-applications)
- Consulte la información de soporte de idiomas:
    - [Modelos de traducción](/docs/services/language-translator?topic=language-translator-translation-models)
    - [Idiomas identificables](/docs/services/language-translator?topic=language-translator-identifiable-languages)

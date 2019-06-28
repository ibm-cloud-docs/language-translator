---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

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

# Traducción de documentos (Beta)
{: #document-translator-tutorial}


Traduzca archivos de un idioma a otro conservando el formato original. Se pueden traducir más de 12 formatos de archivos diferentes, incluidos MS Office, Open Office y PDF.
{:shortdesc}

## Antes de empezar
{: #prerequisites}

- [Comience](/docs/services/language-translator?topic=language-translator-getting-started) con {{site.data.keyword.languagetranslatorshort}}. Necesitará las credenciales de servicio de {{site.data.keyword.languagetranslatorshort}} (`apikey` y `url`).
- Asegúrese de que el documento que desea traducir cumple los requisitos siguientes:
    - Tamaño máximo de archivo: **20 MB**
    - [Formatos de archivos admitidos](#supported-file-formats)
    - [Modelos de traducción admitidos](/docs/services/language-translator?topic=language-translator-translation-models)

## Paso 1: Enviar un documento a traducir
{: #submit-document-to-translate}

La siguiente solicitud de ejemplo envía un archivo de ejemplo *curriculum.pdf* al servicio y lo traduce de inglés a francés. Sustituya `{apikey}` y `{url}` por sus credenciales de servicio y sustituya `curriculum.pdf` por la vía de acceso relativa a su archivo.

Solicitud de ejemplo:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Para traducir un documento con un [modelo personalizado](/docs/services/language-translator?topic=language-translator-customizing), utilice el parámetro **model_id**. La siguiente solicitud traduce el documento con el modelo personalizado identificado por el ID de modelo `96221b69-8e46-42e4-a3c1-808e17c787ca`.

Solicitud de ejemplo:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
{url}/v3/documents?version=2018-05-01
```
{: pre}


Una solicitud correcta devolverá un `document_id` en la respuesta.


Ejemplo de respuesta:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "processing",
  "created": "2018-10-11T03:31:25"
}
```
{: codeblock}

## Paso 2: Comprobar el estado de la traducción
{: #check-translation-status}

Después de haber enviado un documento a traducir, puede comprobar el estado de la traducción para averiguar cuándo está disponible el documento traducido para poderlo descargar. La siguiente solicitud de ejemplo comprueba el estado de la traducción del documento con el ID de documento `bae02796-0d28-435c-9115-888359fdde62`. 

Solicitud de ejemplo:
```bash
curl -X GET \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Ejemplo de respuesta:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "available",
  "created": "2018-10-11T03:31:25",
  "completed": "2018-10-11T03:31:38"
}
```
{: codeblock}

Cuando el valor `status` de la respuesta es `available`, significa que el documento traducido está listo para que lo descargue.

## Paso 3: Descargar el documento traducido
{: #download-translated-document}

La siguiente solicitud de ejemplo guarda el documento traducido con el ID de documento `bae02796-0d28-435c-9115-888359fdde62` en el archivo *curriculum-fr.pdf*. 

Solicitud de ejemplo:
```bash
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01
```
{: pre}

## Paso 4: Traducir un documento enviado previamente
{: #translate-document-by-reference}

La siguiente solicitud de ejemplo hace referencia al archivo original inglés *curriculum.pdf* con el `document_id` `bae02796-0d28-435c-9115-888359fdde62` y lo traduce al portugués.

Solicitud de ejemplo:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Ejemplo de respuesta:
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

La respuesta contiene un nuevo `document_id`. Repita los pasos dos y tres con el nuevo `document_id` para comprobar el estado de la traducción y para descargar el archivo traducido una vez esté disponible.

## Paso 5: Suprimir documentos
{: #delete-documents}

Los documentos originales y los documentos traducidos asociados se suprimen automáticamente si no se han utilizado durante un cierto periodo de tiempo. Consulte [Seguridad de la información](/docs/services/language-translator?topic=language-translator-information-security) para obtener más información.
{: tip}

Para suprimir documentos manualmente, utilice el método **Suprimir documento**. En esta guía de aprendizaje, el archivo *curriculum.pdf* ha participado en dos traducciones, de modo que se necesitan dos solicitudes para suprimir todas las copias del documento original.

Suprima el envío original de *curriculum.pdf* y la traducción al francés:
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Suprima el duplicado del archivo *curriculum.pdf* original y la traducción al portugués:
```bash
curl -X DELETE \
--user "apikey:{apikey}" \
{url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01
```
{: pre}

## Formatos de archivos admitidos
{: #supported-file-formats}

-  Microsoft Office
    - Word: `.doc`, `.docx`
    - PowerPoint: `.ppt`, `.pptx`
    - Excel: `.xls`, `.xlsx`
    - Rich Text Format: `.rtf`
- Open Office
    - Writer: `.odt`
    - Impress: `.odp`
    - Calc: `.ods`
- Otros formatos
    - PDF: `.pdf`
    - HTML: `.htm`, `.html`
    - XML: `.xml`
    - JSON: `.json` (se traducen los valores con el tipo `string` o `string array`)
    - Texto: `.txt`

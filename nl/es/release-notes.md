---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

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

# Notas del release

Están disponibles las siguientes nuevas características y cambios en el servicio.
{: shortdesc}

## 12 de enero de 2018
{: #12-january-2018}

Hay disponibles nuevos modelos NMT (traducción automática neuronal) para su previsualización. Puede probar los modelos NMT para los pares de idiomas siguientes. 

- Del y al inglés: árabe, chino, holandés, francés, alemán, italiano, japonés, coreano, polaco, portugués (de Brasil), ruso, español y turco
- Del y al francés: alemán, español
- Del y al alemán: italiano

*Los modelos NMT y la sintaxis para utilizarlos están sujetos a cambios durante el periodo de previsualización. Actualmente, los modelos NMT no dan soporte a la personalización del corpus. Solo se da soporte a la personalización del glosario forzado.*

Para utilizar un modelo de previsualización NMT para traducir, especifique la cabecera `X-Watson-Technology-Preview:2017-07-01` junto con los códigos de caracteres para los idiomas de origen y destino del modelo que desea utilizar. El ejemplo siguiente muestra cómo traducir del inglés al español con un modelo de previsualización NMT.

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}


## 15 de diciembre de 2016
{: #15-december-2016}

Se han añadido modelos de traducción de noticias adicionales: inglés al y del japonés

## 15 de noviembre de 2016
{: #15-november-2016}

Las herramientas que antes estaban disponibles para el servicio {{site.data.keyword.languagetranslatorshort}} ya no están disponibles ni soportadas. 

Póngase en contacto con el representante de ventas o soporte al cliente para obtener información sobre cómo utilizar la API de {{site.data.keyword.languagetranslatorshort}} para realizar las tareas soportadas por la herramienta {{site.data.keyword.languagetranslatorshort}}.

## 1 de septiembre de 2016
{: #1-september-2016}

El servicio IBM Watson&trade; Language Translation ha cambiado de nombre por {{site.data.keyword.languagetranslatorshort}}.

## 22 de marzo de 2016
{: #22-march-2016}

Se ha añadido soporte para idiomas adicionales: inglés al y del italiano, y español al y del francés.

## 3 de diciembre de 2015
{: #3-december-2015}

A partir del 15 de enero de 2016, se retiran todas las capacidades de personalización dentro del plan Estándar. Las aplicaciones que no utilizan características de personalización no requieren cambios, ya que el plan Estándar permanece activo para todas las llamadas de API no relacionadas con la personalización o los modelos personalizados. Para utilizar las características de personalización de disponibilidad general (el plan Entrenamiento) del servicio {{site.data.keyword.languagetranslatorshort}} con una aplicación de {{site.data.keyword.cloud}} que utiliza una instancia anterior del servicio, siga los siguientes pasos:

1.  Cree una nueva instancia de Watson {{site.data.keyword.languagetranslatorshort}} y especifique el plan de disponibilidad general "Entrenamiento".
1.  Enlace la nueva instancia "Entrenamiento" del servicio a la app en {{site.data.keyword.cloud_notm}}.
1.  Recopile los datos que se utilizaron inicialmente para crear los modelos personalizados. Para obtener más información, consulte [Estructura de los datos de entrenamiento](/docs/services/language-translator/customizing.html#structure).
1.  Cargue los datos de entrenamiento para crear nuevos modelos personalizados en la instancia "Entrenamiento". Para obtener más información, consulte [Entrenamiento de un modelo de traducción personalizado](/docs/services/language-translator/customizing.html#training).
1.  En la app, el campo "ModelID" debe hacer referencia a los nuevos modelos personalizados.
1.  Desenlace el servicio anterior de su app en {{site.data.keyword.cloud_notm}} y luego suprímala.

## 6 de noviembre de 2015
{: #6-november-2015}

Se ha presentado la herramienta {{site.data.keyword.languagetranslatorshort}} beta. La herramienta es una aplicación web que proporciona una interfaz gráfica de usuario para gestionar y entrenar modelos para obtener una traducción más precisa. Puede crear objetos, cargar datos de entrenamiento, entrenar modelos personalizados y traducir texto.

## 1 de diciembre de 2014
{: #1-december-2014}

Las API de Machine Translator beta y Language Identification beta se han actualizado y combinado con la API de {{site.data.keyword.languagetranslatorshort}}. Para empezar a utilizar inmediatamente el nuevo servicio, debe conocer y actualizar el código para reflejar estos cambios:

- **New model\_id parameter**: En la API beta, se definía el parámetro `sid` para seleccionar el modelo para utilizar en la traducción. En esta versión, el parámetro `sid` se ha renombrado a `model_id`. Para recuperar el los valores permitidos de `model_id`, utilice la operación `GET/language  translator/api/v2/models`. Esto devuelve una lista de todos los modelos y los valores `model_id` correspondientes.
- **Soporte para pares de idiomas**: En lugar de seleccionar un `model_id`, ahora puede especificar un idioma de origen y de destino, y se utilizará de forma predeterminada el modelo entrenado en el dominio de noticias generales.
- **Soporte para cuerpos de solicitud JSON**: Al hacer una solicitud de traducción POST, ahora puede realizar la solicitud como un envío JSON. El formato JSON permite enviar varios párrafos a traducir, en lugar de un único fragmento de texto en el formato de envío del formulario.
- **Soporte para cuerpo de respuesta JSON**: Los datos de la solicitud de traducción que se devuelven dan soporte al formato JSON, así como al formato de texto sin formato. El formato JSON permite que las palabras traducidas se devuelvan en varios párrafos en lugar de un único fragmento de texto.
- **Soporte para cabeceras de aceptación**: Ahora la cabecera de aceptación puede utilizarse para definir el formato de la respuesta en todas las operaciones (text/plain o application/json).
- **Soporte para identificación de idioma**: Se han añadido métodos de identificación de idioma a esta API. Esto le permite identificar el idioma de los textos de entrada, y muestra una lista de todos los idiomas soportados que pueden ser detectados por la API.


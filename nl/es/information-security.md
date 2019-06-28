---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-04"

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

# Seguridad de la información
{: #information-security}

IBM se ha comprometido a proporcionar a nuestros clientes y socios soluciones innovadoras de privacidad, seguridad y gobierno de datos.
{: shortdesc}

**Aviso:**
Los clientes son responsables de garantizar su propio cumplimiento con diversas leyes y reglamentos, incluido el Reglamento General de Protección de Datos de la Unión Europea. Los clientes son los únicos responsables de obtener asesoramiento legal competente referente a la identificación y la interpretación de cualquier ley relevante que pudiera afectar a su negocio, así como cualquier medida que debieran tomar para cumplir con dichas leyes y normativas.

Los productos, los servicios y otras prestaciones descritas en este documento no son adecuados para todas las situaciones de los clientes y su disponibilidad puede estar restringida. IBM no proporciona recomendaciones legales, contables o de auditoría ni garantiza que sus servicios o productos garantizarán que los clientes cumplan ninguna legislación o normativa.

Si tiene que solicitar soporte de GDPR para los recursos de {{site.data.keyword.cloud}} {{site.data.keyword.watson}} que se crean

-   En la Unión Europea (UE), consulte [Solicitud de soporte para recursos de IBM Cloud Watson creados en la Unión Europea](/docs/services/watson/getting-started-gdpr-sar.html#request-EU).
-   Fuera de la Unión Europea, consulte [Solicitud de soporte para recursos fuera de la Unión Europea](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU).

## Reglamento General de Protección de Datos de la Unión Europea (GDPR)
{: #gdpr}

IBM se ha comprometido a proporcionar a nuestros clientes y socios soluciones innovadoras de privacidad, seguridad y gobierno de datos para ayudarles a cumplir con el GDPR.

Obtenga más información sobre la implantación del GDPR en IBM y las prestaciones y las ofertas de GDPR para ayudarle a cumplirlo [aquí ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](../../icons/launch-glyph.svg "Icono de enlace externo")](http://www.ibm.com/gdpr){: new_window}.

## Etiquetado y supresión de datos en Language Translator
{: #gdpr-in-service}

El servicio {{site.data.keyword.languagetranslatorshort}} almacena temporalmente en la memoria caché los datos de traducción de las solicitudes de traducción y almacena los datos de entrenamiento que se utilizan para crear modelos personalizados.

### Traducción de datos y de documentos
{: #translation-data-and-documents}

Cuando envía texto a {{site.data.keyword.languagetranslatorshort}} en el método **Traducir**, el servicio almacena en la memoria caché el texto de origen y el resultado de la traducción para mejorar el rendimiento cuando recibe el mismo texto en las posteriores solicitudes de **Traducir**. El texto de la traducción de la memoria caché solo se suprime después de que no se utilice durante un periodo de 15 días.

Los documentos que se envían al servicio para la traducción a través del método **Traducir documento** se almacenan internamente para proporcionar el archivo traducido y para dar soporte a las solicitudes **Traducir documento** adicionales por referencia al documento original cargado. El documento original y los documentos traducidos asociados solo se suprimen después de que no se utilicen en las solicitudes posteriores de **Traducir documento** durante un periodo de 15 días. Se puede utilizar el método **Suprimir documento** para suprimir documentos antes de la fecha límite de supresión. 

Los datos y documentos de la traducción están cifrados cuando están en proceso y cuando están en reposo.

### Datos de entrenamiento de modelos personalizados
{: #custom-model-training-data}

Cuando entrena un modelo personalizado, los datos de entrenamiento que se utilizan para crear el modelo se almacenan para proporcionarle el modelo personalizado. Los modelos personalizados y los datos de entrenamiento están cifrados cuando están en proceso y en reposo. Los datos de entrenamiento cifrados permanecen en el almacenamiento hasta que el modelo se suprime con el método **Suprimir modelo**.

Los modelos personalizados solo se pueden suprimir a nivel de modelo. Los datos de los componentes que se utilizan para crear un modelo personalizado no se pueden suprimir. Si utiliza datos personales al crear un modelo personalizado, se debe crear un modelo personalizado distinto para cada cliente y el modelo `name` se debe etiquetar para identificar al cliente, de modo que se pueda suprimir si se solicita. 

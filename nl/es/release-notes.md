---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-14"

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

## Nuevo proceso de autenticación de API
{: #iam-auth-process }

El servicio {{site.data.keyword.languagetranslatorshort}} tiene un nuevo proceso de autenticación de API para instancias de servicio que están alojadas en las ubicaciones siguientes:

- Dallas a partir del 15 de junio de 2018
- Frankfurt a partir del 15 de junio de 2018
- Londres
- Sídney a partir del 12 de junio de 2018
- Tokio
- Washington, DC a partir del 12 de junio de 2018

{{site.data.keyword.cloud_notm}} está migrando a la autenticación de IAM (Identity and Access Management) basada en señales. Con algunas instancias de servicio, se autentica en la API mediante IAM.

- Para las _nuevas_ instancias de servicio creadas en las ubicaciones indicadas anteriormente, utilice IAM para la autenticación. Puede pasar una señal de portadora (bearer) o una clave de API. Las señales dan soporte a solicitudes autenticadas sin incluir credenciales de servicio en cada llamada. Las claves de API utilizan la autenticación básica.

    Cuando utilice cualquiera de los SDK de Watson, puede pasar la clave de API y dejar que el SDK gestione el ciclo de vida de las señales. Para obtener más información y para ver ejemplos, consulte el apartado sobre [Autenticación ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/apidocs/language-translator#authentication){: new_window} en la consulta de API.
- Para las instancias de servicio _existentes_ que ha creado antes de la fecha indicada, seguirá autenticándose proporcionando el nombre de usuario y la contraseña para la instancia de servicio. Es posible que tenga que migrar estas instancias de servicio a la autenticación de IAM. Se proporcionarán actualizaciones sobre el proceso de migración y las fechas. Para obtener más información sobre la migración, consulte [Migración de instancias de servicio de Cloud Foundry a un grupo de recursos](/docs/resources?topic=resources-migrate#migrate).

Para averiguar qué autenticación debe utilizar, visualice las credenciales de servicio pulsando la instancia de servicio en la página de recursos de [{{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/resources){: new_window}.

## Versiones de la API del servicio
{: shortdesc}

Las solicitudes de API en {{site.data.keyword.languagetranslatorshort}} v3 requieren un parámetro de versión que toma una fecha en el formato `version=AAAA-MM-DD`. Siempre que cambiamos la API de forma que sea compatible con versiones anteriores, ponemos a su disposición una versión menor de la API.

Envíe el parámetro version con cada solicitud de API. El servicio utiliza la versión de la API correspondiente a la fecha que especifique, o la versión más reciente anterior a dicha fecha. No se utiliza como valor predeterminado la fecha actual. Especifique una fecha que coincida con una versión que sea compatible con su app y no la modifique hasta que la app esté lista para una versión posterior.

La versión actual es `2018-05-01`.

## 14 de junio de 2019
{: #14-june-2019}

Ahora dispone de nuevos [modelos de traducción](/docs/services/language-translator?topic=language-translator-translation-models) para inglés y griego.
- Inglés a griego (en-el)
- Griego a inglés (el-en)

## 13 de junio de 2019
{: #13-june-2019}

Ahora dispone de nuevos [modelos de traducción](/docs/services/language-translator?topic=language-translator-translation-models) para inglés y hebreo.
- Inglés a hebreo (en-he)
- Hebreo a inglés (he-en)

## 21 de marzo de 2019
{: #21-march-2019}

A partir del 21 de marzo de 2019, solo verá la información de credenciales de servicio asociada con el rol que se ha asignado a su cuenta de {{site.data.keyword.cloud_notm}}. Por ejemplo, si tiene asignado el rol de `lector`, no podrá ver ninguna credencial de servicio de `escritor` o de niveles superiores.

Este cambio no afecta al acceso a la API para usuarios o aplicaciones con las credenciales de clave de servicio existentes. Solo afecta a la visualización de credenciales dentro de {{site.data.keyword.cloud_notm}}.

Para obtener más información sobre las claves de servicio y los roles de usuario, consulte [Claves de API del servicio IAM](/docs/services/watson?topic=watson-api-key-bp#api-key-bp).

## 14 de diciembre de 2018
{: #14-december-2018}

- Ahora puede crear instancias del servicio {{site.data.keyword.languagetranslatorshort}} en la ubicación Londres de {{site.data.keyword.cloud_notm}}.

## 16 de noviembre de 2018
{: #16-november-2018}

- La función de [traducción de documentos (Beta)](/docs/services/language-translator?topic=language-translator-translating-documents) ya está disponible mediante nuevos puntos finales de API. Envíe un documento de Microsoft Office, un archivo PDF y otro documento con un formato de archivo admitido y {{site.data.keyword.languagetranslatorshort}} le proporcionará una copia traducida que conserva el formato original.
  - Los [formatos de archivo admitidos](/docs/services/language-translator?topic=language-translator-translating-documents#supported-file-types) incluyen `.doc`, `.ppt`, `.pdf` y más.

- Ahora dispone de nuevos [modelos de traducción](/docs/services/language-translator?topic=language-translator-translation-models) para húngaro:
  - Húngaro a inglés (hu-en)
  - Inglés a húngaro (en-hu)

## 8 de noviembre de 2018
{: #8-november-2018}

- Ahora puede crear instancias del servicio {{site.data.keyword.languagetranslatorshort}} en la ubicación Tokio de {{site.data.keyword.cloud_notm}}.

## 9 de agosto de 2018
{: #9-august-2018}

Ahora dispone de nuevos [modelos de traducción](/docs/services/language-translator?topic=language-translator-translation-models) para noruego bokmål:
  - Noruego bokmål a inglés (nb-en)
  - Inglés a noruego bokmål (en-nb)

## 27 de junio de 2018
{: #27-june-2018}

Están disponibles nuevos [modelos de traducción](/docs/services/language-translator?topic=language-translator-translation-models) que ofrecen seis nuevos idiomas:
  - Catalán
    - Catalán a español (ca-es)
    - Español a catalán (es-ca)
  - Checo
    - Checo a inglés (cs-en)
    - Inglés a checo (en-cs)
  - Danés
    - Danés a inglés (da-en)
    - Inglés a danés (en-da)
  - Finés
    - Finés a inglés (fi-en)
    - Inglés a finés (en-fi)
  - Hindi
    - Hindi a inglés (hi-en)
    - Inglés a hindi (en-hi)
  - Sueco
    - Sueco a inglés (sv-en)
    - Inglés a sueco (en-sv)
  

## 15 de junio de 2018
{: #15-june-2018}

A partir del 15 de junio de 2018, las nuevas instancias de servicio creadas en las regiones de Alemania y de EE. UU. sur utilizan la [autenticación de Identity and Access Management (IAM)](#iam-auth-process).

Las nuevas instancias de servicio que cree en Alemania y en el sur de EE. UU. no serán compatibles con el programa Language Translator v2. Si utiliza Language Translator v2 y tiene intención de utilizar nuevas instancias de servicio en su aplicación, tendrá que [migrar a la API de la v3](/docs/services/language-translator?topic=language-translator-migrating).

## 12 de junio de 2018
{: #12-june-2018}

Ahora está disponible {{site.data.keyword.languagetranslatorshort}} v3. La API de Language Translator v2 dejará de estar disponible a partir del 31 de julio de 2018. Para beneficiarse de las últimas mejoras del servicio, migre a la API v3. Consulte la página [Migración a Language Translator v3](/docs/services/language-translator?topic=language-translator-migrating) para obtener más información.

### Novedades de la v3
{: #whats-new}

-  La API {{site.data.keyword.languagetranslatorshort}} v3 viene con los modelos **Neural Machine Translation** (NMT), que ofrecen resultados de traducción significativamente mejorados. Todos los modelos NMT se pueden personalizar.
-  Utilice modelos personalizados como modelos base para la personalización del glosario forzado.
-  La API v3 es un subconjunto JSON simplificado de la API v2 retirada.
-  Incorpora fechas de la versión de API para ofrecer a los desarrolladores la libertad de adoptar a su ritmo futuros cambios en la API.

### Cambios importantes
{: #breaking-changes}

- Fecha de versión obligatoria para todos los puntos finales de API: las solicitudes de API v3 requieren un parámetro de consulta de fecha de versión con el formato `version=AAAA-MM-DD`. La versión más reciente de la API es `version=2018-05-01`.
- API simplificada:
  - Los métodos **Translate** e **Identify** no ofrecen la opción de devolver respuestas en texto sin formato en la v3. Estos métodos solo devuelven respuestas JSON.
  - Los métodos `GET /translate` y `GET /identify` no reciben soporte en la v3. Utilice en su lugar los métodos `POST /translate` y `POST /identify`. 
- La personalización de corpus monolingüe no recibe soporte en la v3.
- Ahora la creación de modelos personalizados con corpus paralelo y glosario forzado se debe realizar en dos llamadas de API. Primero debe personalizar el modelo con un corpus paralelo. Una vez finaliza el entrenamiento del modelo personalizado, puede volverlo a personalizar con el glosario forzado. Este cambio le permite utilizar un modelo personalizado que se ha entrenado con un corpus paralelo como base para la personalización del glosario forzada.
- Los modelos especializados de dominio de conversación y de patentes no están disponibles en la API v3. La calidad de la traducción que proporcionan los modelos NMT en los dominios de patentes y de conversación se ha mejorado a nivel general, en comparación con los modelos especializados antiguos.
- Se ha cambiado el nombre de las claves de objeto de error para que sean coherentes con otras API Watson. `error_code` ahora se denomina `code` y `error_message` ahora se denomina `error`.

### Autenticación de IAM

A partir del 12 de junio de 2018, las nuevas instancias de servicio creadas en las regiones de Sídney y de EE. UU. este utilizan la [autenticación de Identity and Access Management (IAM)](#iam-auth-process).

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

Puede ver el [vídeo en YouTube ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://youtu.be/L6ZC0QaUZ2k) en el que se explica cómo configurar {{site.data.keyword.languagetranslatorshort}} con una vista previa de NMT.


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
2.  Enlace la nueva instancia "Entrenamiento" del servicio a la app en {{site.data.keyword.cloud_notm}}.
3.  Recopile los datos que se utilizaron inicialmente para crear los modelos personalizados. Para obtener más información, consulte [Estructura de los datos de entrenamiento](/docs/services/language-translator?topic=language-translator-customizing#structure).
4.  Cargue los datos de entrenamiento para crear nuevos modelos personalizados en la instancia "Entrenamiento". Para obtener más información, consulte [Entrenamiento de un modelo de traducción personalizado](/docs/services/language-translator?topic=language-translator-customizing#training).
5.  En la app, el campo "ModelID" debe hacer referencia a los nuevos modelos personalizados.
6.  Desenlace el servicio anterior de su app en {{site.data.keyword.cloud_notm}} y luego suprímala.

## 6 de noviembre de 2015
{: #6-november-2015}

Se ha presentado la herramienta {{site.data.keyword.languagetranslatorshort}} beta. La herramienta es una aplicación web que proporciona una interfaz gráfica de usuario para gestionar y entrenar modelos para obtener una traducción más precisa. Puede crear objetos, cargar datos de entrenamiento, entrenar modelos personalizados y traducir texto.

## 1 de diciembre de 2014
{: #1-december-2014}

Las API de Machine Translator beta y Language Identification beta se han actualizado y combinado con la API de {{site.data.keyword.languagetranslatorshort}}. Para empezar a utilizar inmediatamente el nuevo servicio, debe conocer y actualizar el código para reflejar estos cambios:

- **New model\_id parameter**: En la API beta, se definía el parámetro `sid` para seleccionar el modelo para utilizar en la traducción. En esta versión, el parámetro `sid` se ha renombrado a `model_id`. Para recuperar los valores permitidos de `model_id`, utilice la operación `GET/language  translator/api/v2/models`. Esto devuelve una lista de todos los modelos y los valores `model_id` correspondientes.
- **Soporte para pares de idiomas**: En lugar de seleccionar un `model_id`, ahora puede especificar un idioma de origen y de destino, y se utilizará de forma predeterminada el modelo entrenado en el dominio de noticias generales.
- **Soporte para cuerpos de solicitud JSON**: Al hacer una solicitud de traducción POST, ahora puede realizar la solicitud como un envío JSON. El formato JSON permite enviar varios párrafos a traducir, en lugar de un único fragmento de texto en el formato de envío del formulario.
- **Soporte para cuerpo de respuesta JSON**: Los datos de la solicitud de traducción que se devuelven dan soporte al formato JSON, así como al formato de texto sin formato. El formato JSON permite que las palabras traducidas se devuelvan en varios párrafos en lugar de un único fragmento de texto.
- **Soporte para cabeceras de aceptación**: Ahora la cabecera de aceptación puede utilizarse para definir el formato de la respuesta en todas las operaciones (text/plain o application/json).
- **Soporte para identificación de idioma**: Se han añadido métodos de identificación de idioma a esta API. Esto le permite identificar el idioma de los textos de entrada, y muestra una lista de todos los idiomas soportados que pueden ser detectados por la API.

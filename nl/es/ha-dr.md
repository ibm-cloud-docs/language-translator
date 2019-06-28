---

copyright:
  years: 2019
lastupdated: "2019-03-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Alta disponibilidad y recuperación tras desastre
{: #ha-dr}

{{site.data.keyword.languagetranslatorfull}} ofrece alta disponibilidad dentro de múltiples ubicaciones de {{site.data.keyword.cloud_notm}} (por ejemplo, Dallas y Washington, DC). Sin embargo, la recuperación de desastres potenciales que afectan a toda una ubicación requiere planificación y preparación.
{: shortdesc}

Usted es el responsable de comprender su configuración, personalización y uso del servicio. También es responsable de estar preparado para volver a crear una instancia del servicio en una nueva ubicación y de restaurar los datos en cualquier ubicación. Consulte [¿Cómo puedo asegurar un tiempo de inactividad cero? ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} para obtener más información.

## Alta disponibilidad
{: #high-availability}

{{site.data.keyword.languagetranslatorshort}} da soporte a la alta disponibilidad sin ningún punto único de anomalía. El servicio consigue una alta disponibilidad de forma automática y transparente utilizando la característica de región multizona (MZR) proporcionada por {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} habilita varias zonas que no comparten un único punto de anomalía dentro de una única ubicación. También proporciona equilibrio de carga automático entre las zonas dentro de una región.


## Recuperación tras desastre
{: #disaster-recovery}

En el caso de que se produzca un error catastrófico en una región, siga estos pasos.

- Cree una nueva instancia de servicio de {{site.data.keyword.languagetranslatorshort}}.
- Ajuste el software de la aplicación para que utilice el nuevo URL y las nuevas credenciales de la instancia de servicio.
- Cree nuevos modelos personalizados para sustituir los que haya perdido. Utilice los mismos glosarios forzados y corpus paralelos que ha utilizado para crear los modelos personalizados anteriores. Consulte [Personalización del modelo](/docs/services/language-translator?topic=language-translator-customizing#customizing) para obtener más información sobre modelos personalizados.
  - Para prepararse para una recuperación rápida, guarde copias de seguridad de los archivos de entrenamiento siempre que cree un modelo. Puede utilizar los campos `name` y `model_id` de los modelos personalizados junto con los nombres de archivo de los archivos de entrenamiento para mantener un registro de los archivos que utiliza para cada modelo. 
- Ajuste el software de la aplicación para que utilice los nuevos modelos personalizados.


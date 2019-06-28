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

# Haute disponibilité et reprise après incident
{: #ha-dr}

{{site.data.keyword.languagetranslatorfull}} est hautement disponible dans plusieurs emplacements {{site.data.keyword.cloud_notm}} (par exemple, Dallas et Washington, DC). Cependant, la reprise après un incident affectant l'emplacement dans son ensemble nécessite une planification et une préparation.
{: shortdesc}

Il vous appartient de bien connaître la configuration, la personnalisation et l'utilisation du service. Vous êtes également tenu d'être prêt à recréer une instance du service sur un nouveau site et à restaurer vos données sur n'importe quel site.
Voir [Comment garantir une disponibilité permanente ? ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} pour plus d'informations. 

## Haute disponibilité
{: #high-availability}

{{site.data.keyword.languagetranslatorshort}} prend en charge la haute disponibilité sans aucun point de défaillance unique. Ce service assure automatiquement et de manière transparente la haute disponibilité à l'aide de la fonctionnalité MZR (régions multi-zones) fournie par {{site.data.keyword.cloud_notm}}. 

{{site.data.keyword.cloud_notm}} autorise des zones multiples qui ne partagent aucun point de défaillance unique au sein d'un emplacement. Il fournit également un équilibrage automatique de la charge entre les zones d'une région. 


## Reprise après incident
{: #disaster-recovery}

Dans l'éventualité d'un incident grave dans une région, procédez comme suit : 

- Créez une instance de service {{site.data.keyword.languagetranslatorshort}}.
- Ajustez votre logiciel d'application pour qu'il utilise l'URL et les données d'identification de la nouvelle instance de service. 
- Créez des modèles personnalisés pour remplacer ceux que vous avez perdus. Utilisez les glossaires forcés et les corpus parallèles que vous avez utilisés pour créer vos modèles personnalisés précédents. Pour plus d'informations sur les modèles personnalisés, voir [Personnalisation de votre modèle](/docs/services/language-translator?topic=language-translator-customizing#customizing). 
  - Pour vous préparer à une récupération rapide, stockez des copies de sauvegarde de vos fichiers d'entraînement chaque fois que vous créez un modèle. Vous pouvez utiliser les zones `name` et `model_id` de vos modèles personnalisés avec les noms de vos fichiers d'entraînement pour conserver une trace des fichiers que vous utilisez pour chaque modèle.  
- Ajustez votre logiciel d'application pour qu'il utilise les nouveaux modèles personnalisés. 


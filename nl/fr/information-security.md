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

# Sécurité des informations
{: #information-security}

IBM s'est engagée à fournir à ses clients et partenaires des solutions innovantes de confidentialité, de sécurité et de gouvernance des données.
{: shortdesc}

**Remarque :**
Il appartient à chaque entreprise de se conformer aux lois et réglementations, notamment relatives à la protection des données personnelles. Il relève de la seule responsabilité du client de consulter les services juridiques compétents aussi bien pour identifier et interpréter les lois et règlements susceptibles d’affecter son activité, que pour toute action à entreprendre pour se mettre en conformité avec ces lois et réglementations. 

Les produits, services et autres fonctionnalités décrits ici ne sont pas adaptés à toutes les situations client et ne pourront être proposés que sous réserve de disponibilité. IBM ne fournit aucun conseil juridique, comptable ou financier, et ne garantit pas que ses produits ou services permettent
d'assurer la conformité des clients aux lois ou réglementations applicables.

Si vous avez besoin d'une assistance RGPD pour les ressources {{site.data.keyword.cloud}} {{site.data.keyword.watson}} créées

-   Dans l'Union européenne (EU), voir [Demande de support pour des ressources IBM Cloud Watson créées dans l'Union européenne](/docs/services/watson/getting-started-gdpr-sar.html#request-EU).
-   hors UE, voir [Demande de support pour les ressources situées en dehors de l'Union européenne](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU).

## Règlement général sur la protection des données (RGPD) de l'Union européenne
{: #gdpr}

IBM s'efforce de fournir à ses clients et partenaires des solutions innovantes de confidentialité, de sécurité et de gouvernance des données
pour les accompagner dans leur mise en conformité au RGPD. 

Pour en savoir plus sur le parcours préparatoire au RGPD d'IBM ainsi que sur nos session proposées et offres liées au RGPD pour la prise en charge de votre parcours de conformité, cliquez sur [ici ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/gdpr){: new_window}.

## Etiquetage et suppression de données dans Language Translator
{: #gdpr-in-service}

Le service {{site.data.keyword.languagetranslatorshort}} met temporairement en cache les données de traduction des demandes de traduction et stocke les données d'entraînement utilisées pour créer des modèles personnalisés. 

### Documents et données de traduction
{: #translation-data-and-documents}

Lorsque vous envoyez du texte à {{site.data.keyword.languagetranslatorshort}} dans la méthode **Translate**, le service met en cache le texte source et le résultat de la traduction pour améliorer les performances lorsqu'il reçoit le même texte dans les demandes **Traduire** suivantes. Le texte traduit en cache n'est supprimé qu'une fois qu'il n'a pas été utilisé pendant une période de 15 jours. 

Les documents soumis au service pour traduction par l'intermédiaire de la méthode **Translate document** sont stockés en interne pour fournir le fichier traduit et prendre en charge les demandes **Traduire le document** supplémentaires par référence au document téléchargé d'origine. Le document d'origine et les documents traduits associés ne sont supprimés que s'ils n'ont pas été utilisés dans les demandes **Translate document** ultérieures pendant une période de 15 jours. La méthode **Delete document** peut être utilisée pour supprimer des documents avant l'échéance de suppression.  

Les documents et données de traduction sont chiffrés à la volée et au repos. 

### Données d'entraînement des modèles personnalisés
{: #custom-model-training-data}

Lorsque vous entraînez un modèle personnalisé, les données d'entraînement que vous utilisez pour créer le modèle sont stockées pour vous fournir le modèle personnalisé. Les modèles personnalisés et les données d'entraînement sont chiffrés à la volée et au repos. Les données d'entraînement chiffrées restent stockées tant que le modèle n'a pas été supprimé à l'aide de la méthode **Delete model**. 

Les modèles personnalisés ne peuvent être supprimés qu'au niveau du modèle. Les données de composant utilisées pour créer un modèle personnalisé ne peuvent pas être supprimées. Si vous utilisez des données à caractère personnel lors de la création d'un modèle personnalisé, un modèle personnalisé distinct doit être créé pour chaque client et le `nom` de ce modèle doit identifier le client afin de pouvoir être supprimé sur demande.  

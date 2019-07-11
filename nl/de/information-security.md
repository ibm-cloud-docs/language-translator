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

# Informationssicherheit
{: #information-security}

IBM ist bestrebt, seinen Kunden und Partnern innovative Datenschutz-, Sicherheits- und Governance-Lösungen zur Verfügung zu stellen.
{: shortdesc}

**Hinweis:** Jeder Kunde ist für die Einhaltung der geltenden Gesetze und Verordnungen, einschließlich der Datenschutz-Grundverordnung der Europäischen Union selbst verantwortlich. Es obliegt allein den Kunden, sich von kompetenter juristischer Stelle zu Inhalt und Auslegung aller relevanten Gesetze und gesetzlichen Bestimmungen beraten zu lassen, die ihre Geschäftstätigkeit und die von ihnen eventuell einzuleitenden Maßnahmen zur Einhaltung dieser Gesetze und Bestimmungen betreffen.

Die hierin beschriebenen Produkte, Services und sonstigen Funktionen eignen sich nicht für alle Kundensituationen und sind möglicherweise nur eingeschränkt verfügbar. IBM erteilt keine Rechts- oder Steuerberatung und gibt keine Garantie bezüglich der Konformität von IBM Produkten oder Services mit den geltenden Gesetzen und gesetzlichen Bestimmungen.

In den folgenden Abschnitten wird beschrieben, wie Sie Unterstützung für {{site.data.keyword.cloud}} {{site.data.keyword.watson}}-Ressourcen anfordern können:

-   Für Ressourcen, die in der Europäischen Union (EU) erstellt werden, lesen Sie [Unterstützung für IBM Cloud Watson-Ressourcen anfordern, die in der Europäischen Union erstellt werden](/docs/services/watson/getting-started-gdpr-sar.html#request-EU).
-   Für Ressourcen, die außerhalb der Europäischen Union (EU) erstellt werden, lesen Sie [Unterstützung für Ressourcen anfordern, die außerhalb der Europäischen Union erstellt werden](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU).

## Datenschutz-Grundverordnung der Europäischen Union (DSGVO)
{: #gdpr}

IBM ist bestrebt, seinen Kunden und Partnern innovative Datenschutz-, Sicherheits- und Governance-Lösungen zur Verfügung zu stellen, die sie bei der Umsetzung der DSGVO unterstützen.

Weitere Informationen zu den Bestrebungen von IBM zur Umsetzung der DSGVO und zu den IBM Funktionen und Angeboten, die Sie bei der Umsetzung der DSGVO unterstützen, finden Sie [hier ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](../../icons/launch-glyph.svg "Symbol für externen Link")](http://www.ibm.com/gdpr){: new_window}.

## Daten in Language Translator kennzeichnen und löschen
{: #gdpr-in-service}

Der {{site.data.keyword.languagetranslatorshort}}-Service stellt die Übersetzungsdaten aus Übersetzungsanforderungen vorübergehend in einen Cache und speichert die Trainingsdaten, die zum Erstellen angepasster Modelle verwendet werden.

### Übersetzungsdaten und -dokumente
{: #translation-data-and-documents}

Wenn Sie in der Methode zum **Übersetzen** Text an {{site.data.keyword.languagetranslatorshort}} senden, speichert der Service den Quellentext und das Übersetzungsergebnis im Cache für den Fall, dass derselbe Text in späteren **Übersetzungsanforderungen** nochmals empfangen wird. Dadurch wird die Verarbeitungsleistung verbessert. Im Cache gespeicherter Übersetzungstext wird erst gelöscht, wenn er für einen Zeitraum von 15 Tagen nicht verwendet wird.

Dokumente, die dem Service über die Methode zur **Dokumentübersetzung** zur Übersetzung übergeben werden, werden intern gespeichert, um die übersetzte Datei bereitzustellen und um zusätzliche Anforderungen zur **Dokumentübersetzung** zu unterstützen, indem sie auf ein bereits zuvor hochgeladenes Dokument verweisen. Das Originaldokument und alle zugehörigen übersetzten Dokumente werden erst gelöscht, wenn sie in den darauffolgenden 15 Tagen nicht in weiteren Anforderungen zur **Dokumentübersetzung** verwendet wurden. Die Methode zum **Löschen von Dokumenten** kann verwendet werden, um Dokumente vor Ablauf dieser Frist zu löschen. 

Die Übersetzungsdaten und -dokumente werden im Ruhezustand und bei der Übertragung (in flight) verschlüsselt.

### Trainingsdaten für angepasste Modelle
{: #custom-model-training-data}

Wenn Sie ein angepasstes Modell trainieren, werden die Trainingsdaten gespeichert, die Sie zum Erstellen des Modells verwenden, um Ihnen das angepasste Modell zur Verfügung zu stellen. Angepasste Modelle und Trainingsdaten werden im Ruhezustand und bei der Übertragung (in flight) verschlüsselt. Die verschlüsselten Trainingsdaten bleiben im Speicher erhalten, bis das Modell mit der Methode zum **Löschen von Modellen** gelöscht wird.

Angepasste Modelle können nur auf Modellebene gelöscht werden. Komponentendaten, die zum Erstellen eines angepassten Modells verwendet werden, können nicht gelöscht werden. Wenn Sie bei der Erstellung eines angepassten Modells personenbezogene Daten verwenden, muss für jeden Kunden ein separates angepasstes Modell erstellt werden und der `Name` des Modells muss den Kunden angeben, damit es bei Bedarf gelöscht werden kann. 

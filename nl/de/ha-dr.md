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

# Hochverfügbarkeit und Disaster-Recovery
{: #ha-dr}

{{site.data.keyword.languagetranslatorfull}} bietet hohe Verfügbarkeit über mehrere {{site.data.keyword.cloud_notm}}-Standorte hinweg (z. B. Dallas und Washington, DC). Eine Wiederherstellung nach potenziellen Stör- und Katastrophenfällen, die sich auf einen ganzen Standort auswirken, erfordert jedoch Planung und Vorbereitung.
{: shortdesc}

Sie müssen mit der Konfiguration, Anpassung und Verwendung des Service vertraut sein. Sie müssen außerdem in der Lage sein, eine Instanz des Service an einem anderen Standort neu zu erstellen und Ihre Daten an jedem beliebigen Standort wiederherzustellen. Weitere Informationen finden Sie unter [Wie kann sichergestellt werden, dass keine Ausfallzeiten auftreten? ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window}.

## Hohe Verfügbarkeit
{: #high-availability}

{{site.data.keyword.languagetranslatorshort}} unterstützt eine hohe Verfügbarkeit ohne "Single Point of Failure". Der Service erzielt die hohe Verfügbarkeit automatisch und transparent über die von {{site.data.keyword.cloud_notm}} bereitgestellte MZR-Funktion (MZR = Multi-Zone Region).

{{site.data.keyword.cloud_notm}} aktiviert mehrere Zonen, die keinen gemeinsamen Single Point of Failure innerhalb eines Standorts haben. Darüber hinaus wird ein automatischer Lastausgleich über die Zonen innerhalb einer Region zur Verfügung gestellt.


## Disaster-Recovery
{: #disaster-recovery}

Wenn innerhalb einer Region ein Stör- oder Katastrophenfall eintritt, können Sie die folgenden Schritte ausführen.

- Erstellen einer neuen {{site.data.keyword.languagetranslatorshort}}-Serviceinstanz.
- Anpassen Ihrer Anwendungssoftware, um die neue Serviceinstanz-URL und die neuen Berechtigungsnachweise zu verwenden.
- Erstellen neuer angepasster Modelle, wenn Modelle verloren gingen. Sie können dieselben Vorgabewörterbücher und parallelen Korpora verwenden, die Sie zum Erstellen Ihrer vorherigen angepassten Modelle verwendet haben. Weitere Informationen zu angepassten Modellen finden Sie unter [Modell anpassen](/docs/services/language-translator?topic=language-translator-customizing#customizing).
  - Speichern von Sicherungskopien Ihrer Trainingsdateien schon während der Modellerstellung, um eine schnelle Wiederherstellung zu ermöglichen. Sie können die Felder `name` und `model_id` Ihrer angepassten Modelle zusammen mit den Dateinamen Ihrer Trainingsdateien verwenden, um festzuhalten, welche Dateien Sie für jedes Modell verwenden. 
- Anpassen Ihrer Anwendungssoftware, um die neuen Modelle zu verwenden.


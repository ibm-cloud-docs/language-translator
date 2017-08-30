---

copyright:
  years: 2015, 2017
lastupdated: "2017-07-19"

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

# Migrating from Language Translation
{: #migrating}

The Language Translator service was formerly known as the Language Translation service. If you created any instances of the Language Translation service that you are not using, delete them.
{: shortdesc}

If you are using an instance of the Language Translation service in an application, it will continue to function until September 2017. However, migrate your applications to use the Language Translator service as quickly as possible, because the service is not being enhanced after September 1, 2016. All enhancements and new features are made to the Language Translator service only.

Custom models that you created with the Language Translation service will work with the Language Translator service, but must be retrained.

Follow this process to migrate your application to use an instance of the Language Translator service:

1. Go to the [Language Translator catalog page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/language-translator) in Bluemix, and log in.
1.  Select a pricing plan that has at least the same level of support as the plan that is associated with the Language Translation instance that your application is currently using, then click **Create**.
1.  Go to your [Bluemix dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/dashboard/)
1.  Select the application that currently uses the Language Translation service from the list that is displayed under **Cloud Foundry Apps**.
1.  Click **Connections** in the navigation menu.
1.  Find the card for your Language Translation service instance, right-click on the menu icon, and select **Unbind service**.
1.  Click **OK** in the confirmation window to delete the instance of the Language Translation service. Close the "Delete Service" window. A "Restage app" window is displayed.

    When you delete a service that is associated with a {{site.data.keyword.Bluemix_notm}} application, you need to restart that application in {{site.data.keyword.Bluemix_notm}} with its new configuration.

    You will restage your application after you add the instance of the Language Translator service that you created earlier in this process. For now, click **Cancel**.

1.  Modify the source code for your application to replace calls to the Language Translation methods with calls to Language Translator methods. For details, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){: new_window}.

1. From the **Connections** page in your application console, click **Connect existing**. Select the instance of the Language Translator service that you created earlier in this process, and click **Connect**.
1. Click **Restage** in the "Restage app" window.

If your application is not running after restaging is complete, [examine the logs ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/CloudLogAnalysis/cfapps/logging_cf_apps.html#logging_bluemix_cf_apps_log_methods) for your application.

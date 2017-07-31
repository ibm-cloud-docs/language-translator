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

1.  Go to the [Catalog](https://console.ng.bluemix.net/catalog/?category=watson) of {{site.data.keyword.watson}} services in Bluemix.
1.  Click the **Language Translator** tile.
1. After you log in, specify values for these fields, then click **CREATE** 
    1. Provide a service name. 
    1. Select a plan that has at least the same level of support as the plan that is associated with the Language Translation instance that your application is currently using.
1.  Select **Dashboard** from the header menu.
1.  Select **CF APPS** from the navigation bar, and select the application that currently uses the Language Translation service from the list that is displayed under **CF APPS**.
1.  Scroll down the main page until you see the instance of the Language Translation service that your app is using.
1.  Right-click the gear icon for that instance of the Language Translation service, and then select **Unbind service**.
1.  Click **REMOVE** in the confirmation window to delete the instance of the Language Translation service. Close the "Delete Service" window. A "Restage Application" window is displayed.

    When you delete a service that is associated with a {{site.data.keyword.Bluemix_notm}} application, you need to restart that application in {{site.data.keyword.Bluemix_notm}} with its new configuration.

    You will restage your application after you add the instance of the Language Translator service that you created earlier in this process. For now, click **CANCEL**.

1.  Modify the source code for your application to replace calls to the Language Translation methods with calls to Language Translator methods. For details, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){: new_window}.

1. Click **BIND A SERVICE OR API**. Add the instance of the Language Translator service that you created earlier in this process in the "Add Service" window.
1. Click **RESTAGE** in the "Restage Application" window.

After the application is restarted with its updated service bindings, the **APP HEALTH** field states that your application is running.

If the **APP HEALTH** field states that your application is not running, examine the console logs for your application:

- For applications that are running in {{site.data.keyword.Bluemix_notm}}, use the following command to show the most recent portion of the logs for the application named *APPLICATION*:

    ```bash
    cf logs APPLICATION --recent
    ```
    {: pre}

- For applications that are running outside of {{site.data.keyword.Bluemix_notm}}, check the appropriate location for log messages:

    - If you started the application from a terminal window, for example, check the terminal window for relevant messages. 
    - If you started the application from an IDE, such as Eclipse, check the IDE console window. If you have not correctly updated all of the method calls, the console window will show the calls that have not been updated as part of a stack trace.


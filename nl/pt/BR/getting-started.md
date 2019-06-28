---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-04"

---
<!-- Attribute definitions -->
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:go: .ph data-hd-programlang='go'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Tutorial de introdução
{: #gettingstarted}

O {{site.data.keyword.languagetranslatorfull}} permite traduzir texto programaticamente de um idioma para outro.
{:shortdesc}
{: hide-dashboard}

Este tutorial fornece orientação durante os comandos para traduzir texto do inglês para o espanhol e para identificar o idioma de uma amostra de texto.

## Antes de Começar
{: #prerequisites}

- {: hide-dashboard} Crie uma instância do serviço:
    1.  {: hide-dashboard} Acesse a página [{{site.data.keyword.languagetranslatorshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/services/language-translator){: new_window} no {{site.data.keyword.Bluemix_notm}} Catalog.
    2.  Inscreva-se para obter uma conta gratuita do {{site.data.keyword.Bluemix_notm}} ou efetue login.
    3.  Clique em **Criar**.
- Copie as credenciais para autenticação em sua instância de serviço:
    1.  Na página **Gerenciar**, clique em **Mostrar** para visualizar suas credenciais.
    2.  Copie os valores `API Key` e `URL`.
- Certifique-se de que você tenha o comando `curl`:
    - Os exemplos usam o comando `curl` para chamar métodos da interface HTTP. Instale a versão para seu sistema operacional de [curl.haxx.se ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://curl.haxx.se/){: new_window}. Instale a versão que suporta o protocolo Secure Sockets Layer (SSL). Certifique-se de incluir o arquivo binário instalado em sua variável de ambiente `PATH`.

Este tutorial usa uma chave API para autenticação. Para usos de produção, certifique-se de revisar as [melhores práticas](/docs/services/watson/apikey-bp.html#api-bp) da chave API.
{: tip}

## Etapa 1: traduzir texto
{: #translate-text}

Use o exemplo a seguir para traduzir duas frases, "Hello, world!" e "How are you?" do inglês para o espanhol. <span class="hide-dashboard">Substitua `{apikey}` e `{url}` por suas credenciais de serviço.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: application/json" --data "{\"text\": [\"Hello, world! \", \"How are you?\"], \"model_id\":\"en-es\"}" "{url}/v3/translate?version=2018-05-01"{: url}
```
{: pre}

## Etapa 2: identificar idioma
{: #identify-language}

Use o exemplo a seguir para identificar o idioma do texto. <span class="hide-dashboard">Substitua `{apikey}` e `{url}` por suas credenciais de serviço.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} --header "Content-Type: text/plain" --data "Language Translator translates text from one language to another" "{url}/v3/identify?version=2018-05-01"{: url}
```
{: pre}

## Próximas etapas
{: #next-steps}

- Saiba como [customizar](/docs/services/language-translator?topic=language-translator-customizing) o {{site.data.keyword.languagetranslatorshort}} para trabalhar para seu caso de uso
- Tente [traduzir documentos (Beta)](/docs/services/language-translator?topic=language-translator-document-translator-tutorial)
- Visualize a [Referência de API](https://{DomainName}/apidocs/language-translator)
- Explore os [aplicativos de amostra](/docs/services/language-translator?topic=language-translator-sample-applications)
- Visualizar informações de suporte ao idioma:
    - [Modelos de tradução](/docs/services/language-translator?topic=language-translator-translation-models)
    - [Idiomas identificáveis](/docs/services/language-translator?topic=language-translator-identifiable-languages)

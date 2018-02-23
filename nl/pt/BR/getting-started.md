---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

---
<!-- Attribute definitions -->
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:curl: .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Tutorial de introdução
{: #gettingstarted}

O {{site.data.keyword.languagetranslatorfull}} permite traduzir texto programaticamente em notícias, conversação e domínios de patentes. Este tutorial o conduz pelos comandos para traduzir conteúdos de amostra do inglês para espanhol e escolher o domínio.
{:shortdesc}

## Antes de Começar
{: #prerequisites}

- Crie uma instância do serviço:
    - {: download} Se estiver vendo isso, você criou sua instância de serviço. Agora, obtenha suas credenciais.
    - Criar um projeto de um serviço:
        1.  Acesse a página {{site.data.keyword.watson}} Developer Console [Services ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Selecione {{site.data.keyword.languagetranslatorshort}}, clique em **Incluir serviços** e inscreva-se para uma conta do {{site.data.keyword.Bluemix_notm}} grátis ou efetue login.
        1.  Digite `language-tutorial` como o nome do projeto e clique em **Criar projeto**.
- Copie as credenciais para autenticação em sua instância de serviço:
    - {: download} No painel de serviço (que você está vendo):
        1.  Clique na guia **Credenciais de serviço**.
        1.  Clique em **Visualizar credenciais** em **Ações**.
        1.  Copie os valores de `username`, `password` e `url`.
        {: download}
    - De seu projeto **idioma-tutorial** no Developer Console, copie os valores `username`, `password` e `url` para `"language_translator"` da seção **Credenciais**.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Se você usa o {{site.data.keyword.Bluemix_dedicated_notm}}, crie sua instância de serviço na página [{{site.data.keyword.languagetranslatorshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.{DomainName}/catalog/services/language-translator/){: new_window} no Catálogo. Para obter detalhes sobre como localizar suas credenciais de serviço, consulte
[Credencias
de serviço para serviços do Watson ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Etapa 1: traduzir texto
{: #translate-text}

Use o exemplo a seguir para converter "Hello, world!" do inglês para o espanhol. Substitua `{username}` e `{password}` com as credenciais de serviço que você copiou na etapa anterior.

```bash
curl -X POST --user {username}:{password} --header "Accept: application/json" --data "{\"text\":\"Hello, world\",\"source\":\"en\",\"target\":\"es\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate
```
{:codeblock}

Uma visualização prévia dos novos modelos do Neural Machine Translation que oferecem traduções melhoradas já está disponível. Para obter mais detalhes, consulte as [notas sobre a liberação](release-notes.html#12-january-2018).
{: tip}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  version: 'v2',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
});
language_translator.translate({
    text: 'Hello, world!',
    source: 'en',
    target: 'es'
  },
  function(err, translation) {
    if (err)
      console.log(err)
    else
      console.log(translation);
});
```
{:node}
{:codeblock} -->

<!-- ```java
LanguageTranslator service = new LanguageTranslator();
service.setUsernameAndPassword("username","password");

TranslationResult result = service.translate("Hello, world!", "en", "es");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
    username="username",
    password="password")

translation = language_translator.translate(
    text="Hello, world!",
    source="en",
    target="es"
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->


## Etapa 2: experimente um modelo de domínio específico
{: #specify-model}

O {{site.data.keyword.languagetranslatorshort}} tem modelos especializados para domínios de notícias, de conversação e de patente. Quando você especifica os idiomas `source` e `target` como na Etapa 2, o serviço geralmente é padronizado para o modelo de domínio de notícias desse caminho de tradução. Para usar um modelo específico de domínio, especifique o `model_id` em vez dos idiomas `source` e `target`. Também é possível usar um [modelo customizado](customizing.html) se você tem um criado.

_Os modelos específicos de domínio não são suportados em solicitações que contêm o [Cabeçalho de visualização do NMT](release-notes.html#12-january-2018)._

O exemplo a seguir converte "Hey world, whats up?" com o modelo de conversação inglês para espanhol. Substitua `{username}` e `{password}` com suas informações:

```bash
curl -X POST --user {username}:{password} --header "Content-Type: application/json" --header "Accept: application/json" --data "{\"text\":\"Hey world, whats up?\",\"model_id\":\"en-es-conversational\"}" "https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{:codeblock}

<!-- ```
var watson = require('watson-developer-cloud');
var language_translator = watson.language_translator({
  username: 'username',
  password: 'password',
  url: 'https://gateway.watsonplatform.net/language-translator/api'
  version: 'v2',
});
language_translator.translate({
    text: 'Hey, world! What's up?',
    model_id: 'en-es-conversational'
  },
  function(err, translation) {
    if (err)
      console.log(err)
    else
      console.log(translation);
});
```
{:node}
{:codeblock} -->

<!-- ```java
LanguageTranslator service = new LanguageTranslator();
service.setUsernameAndPassword("username","password");

TranslationResult result = service.translate("Hey, world! What's up?", "en-es-conversational");
System.out.println(result);
```
{:java}
{:codeblock} -->

<!-- ```python
import json
from watson_developer_cloud import LanguageTranslatorV2 as LanguageTranslator

language_translator = LanguageTranslator(
  username="username",
  password="password"
)

translation = language_translator.translate(
  text="Hey, world! What's up?",
  model_id="en-es-conversational"
)
print(json.dumps(translation, indent=2, ensure_ascii=False))
```
{:python}
{:codeblock} -->

É possível usar o método [Listar modelos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/#list-models){: new_window} para visualizar os modelos disponíveis para sua instância de serviço.
{:tip}

## Próximas etapas
{: #next-steps}

- Saiba como [customizar](/docs/services/language-translator/customizing.html) o {{site.data.keyword.languagetranslatorshort}} para trabalhar para seu caso de uso.
- Visualize a [Referência de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/language-translator/api/v2/){:new_window}.
- Interaja com a API no [Explorador de API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://watson-api-explorer.mybluemix.net/apis/language-translator-v2){:new_window}.
- Experimente o [aplicativo de amostra Node.js ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/watson-developer-cloud/language-translator-nodejs){:new_window}.

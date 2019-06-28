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

# Nota sobre a Liberação

Os novos recursos e mudanças a seguir para o serviço estão disponíveis.
{: shortdesc}

## Novo processo de autenticação de API
{: #iam-auth-process }

O serviço {{site.data.keyword.languagetranslatorshort}} possui um novo processo de autenticação de API para instâncias de serviço hospedadas nas localizações a seguir:

- Dallas a partir de 15 de junho de 2018
- Frankfurt a partir de 15 de junho de 2018
- Londres
- Sydney a partir de 12 de junho de 2018
- Tóquio
- Washington, DC, a partir de 12 de junho de 2018

O {{site.data.keyword.cloud_notm}} está migrando para a autenticação Identity and Access Management (IAM) baseada em token. Com algumas instâncias de serviço, você autentica para a API usando o IAM.

- Para _novas_ instâncias de serviço criadas nos locais indicados anteriormente, use o IAM para autenticação. É possível passar um token de acesso ou uma chave de API. Os tokens suportam solicitações autenticadas sem as credenciais de serviço incorporadas em cada chamada. As chaves API usam autenticação básica.

    Ao usar qualquer um dos SDKs do Watson, é possível passar a chave de API e deixar que o SDK gerencie o ciclo de vida dos tokens. Para obter mais informações e exemplos, consulte [Autenticação ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/apidocs/language-translator#authentication){: new_window} na referência de API.
- Para instâncias de serviço _existentes_ que você criou antes da data indicada, continue a autenticar fornecendo o nome de usuário e a senha para a instância de serviço. Eventualmente, será necessário migrar essas instâncias de serviço para a autenticação IAM. Atualizações serão fornecidas sobre o processo de migração e as datas. Para obter mais informações sobre migração, consulte [Migrando instâncias de serviço do Cloud Foundry para um grupo de recursos](/docs/resources?topic=resources-migrate#migrate).

Para descobrir qual autenticação deve ser usada, visualize as credenciais de serviço clicando na instância de serviço na [página de recursos do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/resources){: new_window}.

## Versão da API de Serviço
{: shortdesc}

As solicitações de API no {{site.data.keyword.languagetranslatorshort}} v3 requerem um parâmetro de versão que usa uma data no formato `version=YYYY-MM-DD`. Sempre que mudamos a API de uma maneira incompatível com versões anteriores, lançamos uma nova versão secundária da API.

Envie o parâmetro version com cada solicitação de API. O serviço usa a versão da API para a data que você especificar ou a versão mais recente antes dessa data. Não padronize com a data atual. Em vez disso, especifique uma data que corresponda a uma versão que seja compatível com seu aplicativo e não a mude até que o aplicativo esteja pronto para uma versão mais recente.

A versão atual é `2018-05-01`.

## 14 de junho de 2019
{: #14-june-2019}

Novos [modelos de tradução](/docs/services/language-translator?topic=language-translator-translation-models) estão agora disponíveis para inglês e grego.
- Inglês para grego (en-el)
- Grego para inglês (el-en)

## 13 de junho de 2019
{: #13-june-2019}

Novos [modelos de tradução](/docs/services/language-translator?topic=language-translator-translation-models) estão agora disponíveis para inglês e hebraico.
- Inglês para hebraico (en-he)
- Hebraico para inglês (he-en)

## 21 de Março de 2019
{: #21-march-2019}

A partir de 21 de março de 2019, você verá apenas informações de credencial de serviço associadas à função designada a sua conta do {{site.data.keyword.cloud_notm}}. Por exemplo, se você tiver designado uma função `reader`, qualquer `writer` ou níveis mais altos de credenciais de serviço não estarão visíveis.

Essa mudança não afeta o acesso à API para usuários ou aplicativos com credenciais de chave de serviço existentes. Somente a visualização de credenciais no {{site.data.keyword.cloud_notm}} é afetada.

Para obter mais informações sobre chaves de serviço e funções de usuário, consulte [Chaves de API do serviço IAM](/docs/services/watson?topic=watson-api-key-bp#api-key-bp).

## 14 de dezembro de 2018
{: #14-december-2018}

- Agora é possível criar instâncias de serviço do {{site.data.keyword.languagetranslatorshort}} no local em Londres do {{site.data.keyword.cloud_notm}}.

## 16 de novembro de 2018
{: #16-november-2018}

- [A tradução de documentos (Beta)](/docs/services/language-translator?topic=language-translator-translating-documents) agora está disponível por meio de novos terminais de API. Envie um documento, um PDF ou outro documento do Microsoft Office com um formato de arquivo suportado e o {{site.data.keyword.languagetranslatorshort}} fornecerá uma cópia traduzida que preserva a formatação original.
  - Os [formatos de arquivo suportados](/docs/services/language-translator?topic=language-translator-translating-documents#supported-file-types) incluem `.doc`, `.ppt`, `.pdf` e mais.

- Novos [modelos de tradução](/docs/services/language-translator?topic=language-translator-translation-models) para o húngaro estão agora disponíveis:
  - Húngaro para inglês (hu-en)
  - Inglês para húngaro (en-hu)

## 8 de novembro de 2018
{: #8-november-2018}

- Agora é possível criar instâncias de serviço do {{site.data.keyword.languagetranslatorshort}} no local em Tóquio do {{site.data.keyword.cloud_notm}}.

## 9 de agosto de 2018
{: #9-august-2018}

Novos [modelos de tradução](/docs/services/language-translator?topic=language-translator-translation-models) para o bokmål norueguês estão agora disponíveis:
  - Bokmål norueguês para o inglês (nb-en)
  - Inglês para o bokmål norueguês (en-nb)

## 27 de junho de 2018
{: #27-june-2018}

Novos [modelos de tradução](/docs/services/language-translator?topic=language-translator-translation-models) que apresentam seis novos idiomas estão agora disponíveis:
  - Catalão
    - Catalão para espanhol (ca-es)
    - Espanhol para catalão (es-ca)
  - Tcheco
    - Tcheco para inglês (cs-en)
    - Inglês para tcheco (en-cs)
  - Dinamarquês
    - Dinamarquês para inglês (da-en)
    - Inglês para dinamarquês (en-da)
  - Finlandês
    - Finlandês para inglês (fi-en)
    - Inglês para finlandês (en-fi)
  - Hindi
    - Hindi para inglês (hi-en)
    - Inglês para hindi (en-hi)
  - Sueco
    - Sueco para inglês (sv-en)
    - Inglês para sueco (en-sv)
  

## 15 de junho de 2018
{: #15-june-2018}

A partir de 15 de junho de 2018, novas instâncias de serviço criadas nas regiões da Alemanha e do sul dos EUA usam a [autenticação Identity and Access Management (IAM)](#iam-auth-process).

Novas instâncias de serviço criadas na Alemanha e no sul dos EUA não serão compatíveis com o Language Translator v2. Se você usar o Language Translator v2 e estiver planejando usar novas instâncias de serviço em seu aplicativo, será necessário [migrar para a API v3](/docs/services/language-translator?topic=language-translator-migrating).

## 12 de junho de 2018
{: #12-june-2018}

O {{site.data.keyword.languagetranslatorshort}} v3 está agora disponível. A API do Language Translator v2 não estará mais disponível depois de 31 de julho de 2018. Para aproveitar os aprimoramentos de serviço mais recentes, migre para a API da v3. Visualize a página [Migrando para o Language Translator v3](/docs/services/language-translator?topic=language-translator-migrating) para obter mais informações.

### O que há de novo na v3
{: #whats-new}

-  O {{site.data.keyword.languagetranslatorshort}} API v3 é fornecido com os modelos **Neural Machine Translation** (NMT) que oferecem resultados de tradução significativamente melhorados. Todos os modelos NMT estão agora disponíveis para customização.
-  Use modelos customizados como modelos base para customização do glossário forçado.
-  A API v3 é um subconjunto simplificado de todos os JSON da API v2 obsoleta.
-  Introduz datas de versão da API para fornecer aos desenvolvedores a liberdade de adotar futuras mudanças de API em seu próprio ritmo.

### Alterações que afetam o processamento da mensagem
{: #breaking-changes}

- Data da versão obrigatória de todos os terminais de API: as solicitações da API v3 requerem um parâmetro de consulta da data da versão no formato `version=YYYY-MM-DD`. A versão da API mais recente é `version=2018-05-01`.
- API simplificada:
  - Os métodos **Traduzir** e **Identificar** não oferecem a opção de retornar respostas de texto sem formatação na v3. Os métodos retornam apenas respostas JSON.
  - Os métodos `GET /translate` e `GET /identify` não são suportados na v3. Em vez disso, use os métodos `POST /translate` e `POST /identify`. 
- A customização do corpus monolíngue não é suportada na v3.
- A criação de modelos customizados com um corpus paralelo e um glossário forçado agora precisa ser feita em duas chamadas de API. Primeiro, customize o modelo com um corpus paralelo. Depois que o modelo customizado tiver concluído o treinamento, customize-o novamente com o glossário forçado. Essa mudança permite que você use um modelo customizado treinado com um corpus paralelo como uma base para customização do glossário forçado.
- Os modelos de domínio de patente e de conversação especializados não estão disponíveis na API da v3. A qualidade de tradução fornecida pelos modelos NMT nos domínios de patente e de conversação é geralmente melhor em comparação com os modelos especializados mais antigos.
- As chaves de objeto de erro foram renomeadas para que fiquem consistentes com outras APIs do Watson. `error_code` foi renomeado para `code` e `error_message` foi renomeado para `error`.

### Autenticação IAM

A partir de 12 de junho de 2018, novas instâncias de serviço criadas nas regiões de Sydney e leste dos EUA usam a autenticação [Identity and Access Management (IAM)](#iam-auth-process).

## 12 de janeiro de 2018
{: #12-january-2018}

Os novos modelos do Neural Machine Translation (NMT) estão disponíveis para visualização. É possível experimentar modelos NMT para os pares de idiomas a seguir. 

- Inglês para e de: árabe, chinês, holandês, francês, alemão, italiano, japonês, coreano, polonês, português (do Brasil), russo, espanhol e turco
- Francês para e de: alemão, espanhol
- Alemão para e de: italiano

*Os modelos de NMT e a sintaxe para usá-los estão sujeitos a mudanças durante o período de visualização prévia. Atualmente, os modelos de NMT não suportam a customização do corpus. Somente a customização do glossário forçado é suportada.*

Para usar um modelo de visualização prévia do NMT para traduzir, especifique o cabeçalho `X-Watson-Technology-Preview:2017-07-01` com os códigos de caracteres para os idiomas de origem e de destino do modelo que você deseja usar. O exemplo a seguir mostra como converter do inglês para espanhol com um modelo de visualização do NMT.

```bash
curl -u username:password \
-X POST \
-H "Accept: application/json" \
-H "X-Watson-Technology-Preview:2017-07-01" \
-d '{"text":"Hello!","source":"en","target":"es"}' \
"https://gateway.watsonplatform.net/language-translator/api/v2/translate"
```
{: codeblock}

É possível assistir a um [vídeo passo a passo no YouTube ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://youtu.be/L6ZC0QaUZ2k) que explica como configurar o {{site.data.keyword.languagetranslatorshort}} com a visualização do NMT.


## 15 de dezembro de 2016
{: #15-december-2016}

Os modelos de tradução de notícias adicionais foram incluídos: inglês para e de japonês

## 15 de novembro de 2016
{: #15-november-2016}

O conjunto de ferramentas anteriormente disponível para o serviço {{site.data.keyword.languagetranslatorshort}} não está mais disponível ou não é mais suportado. 

Entre em contato com o representante de vendas ou com o suporte ao cliente para obter informações sobre como usar a API do {{site.data.keyword.languagetranslatorshort}} para realizar as tarefas suportadas pela ferramenta {{site.data.keyword.languagetranslatorshort}}.

## 1 de setembro de 2016
{: #1-september-2016}

O serviço IBM Watson&trade; Language Translation Service foi substituído pelo serviço {{site.data.keyword.languagetranslatorshort}}.

## 22 de março de 2016
{: #22-march-2016}

O suporte para idiomas adicionais foi incluído: inglês para e de italiano e espanhol para e de francês.

## 3 de dezembro de 2015
{: #3-december-2015}

Iniciando em 15 de janeiro de 2016, todos os recursos de customização dentro do Plano Padrão foram descontinuados. Os aplicativos que não usam recursos de customização não precisam mudar, já que o Plano Padrão permanece ativo para todas as chamadas API não relacionadas aos modelos de customização ou modelos customizados. Para usar os recursos de customização do GA (o Plano Treinável) do serviço {{site.data.keyword.languagetranslatorshort}} com um aplicativo {{site.data.keyword.cloud}} que usa uma instância anterior do serviço, conclua as etapas a seguir:

1.  Crie uma nova instância do {{site.data.keyword.languagetranslatorshort}} do Watson e especifique o plano "Treinável" de GA.
2.  Ligue a nova instância "Treinável" do serviço ao seu app em {{site.data.keyword.cloud_notm}}.
3.  Reúna os dados que foram usados para criar inicialmente os modelos customizados. Para obter mais informações, consulte [Estrutura dos dados de treinamento](/docs/services/language-translator?topic=language-translator-customizing#structure).
4.  Faça upload dos dados de treinamento para criar novos modelos customizados na instância "Treinável". Para obter mais informações, consulte [Treinando um modelo de tradução customizado](/docs/services/language-translator?topic=language-translator-customizing#training).
5.  Em seu app, aponte o campo "ModelID" para os novos modelos customizados.
6.  Desvincule o serviço anterior de seu app em {{site.data.keyword.cloud_notm}} e, em seguida, exclua-o.

## 6 de novembro de 2015
{: #6-november-2015}

A ferramenta beta {{site.data.keyword.languagetranslatorshort}} foi liberada. A ferramenta é um aplicativo da web que fornece uma interface gráfica com o usuário para gerenciar e treinar modelos mais precisos para tradução de máquina. É possível criar projetos, fazer upload de dados de treinamento, treinar modelos customizados e traduzir textos.

## 1 de dezembro de 2014
{: #1-december-2014}

As APIs do Machine Tradutor beta e do Language Identification beta foram atualizadas e combinadas na API do {{site.data.keyword.languagetranslatorshort}}. Para começar a usar imediatamente o novo serviço, entenda e atualize seu código para refletir essas mudanças:

- **Novo parâmetro model\_id**: na API beta, você definiu o parâmetro `sid` para selecionar o modelo a ser usado para tradução. Nesta versão, o parâmetro `sid` é renomeado para o parâmetro `model_id`. Para recuperar os valores permitidos `model_id`, use a operação `GET/language  translator/api/v2/models`. Isso retorna uma lista de todos os modelos e seus valores correspondentes `model_id`.
- **Suporte de par de idiomas**: em vez de selecionar um `model_id`, agora é possível especificar um idioma de origem e de destino, e o modelo será padronizado para aquele que está treinado no domínio de notícias gerais.
- **Suporte do corpo da solicitação JSON**: ao fazer uma solicitação de tradução POST, agora é possível fazer a solicitação como uma submissão JSON. A formatação JSON permite enviar vários parágrafos para conversão, em vez de apenas um único pedaço de texto no formato de envio de formulário.
- **Suporte de corpo de resposta JSON**: a solicitação de tradução retorna a formatação de JSON de suporte, bem como a formatação de texto sem formatação. O formato JSON permite o suporte, para que as palavras traduzidas sejam retornadas em vários parágrafos, em vez de um único pedaço de texto.
- **Suporte de cabeçalho de aceitação**: o cabeçalho de aceitação agora pode ser usado para definir o formato da resposta em todas as operações (texto/simples ou aplicativo/json).
- **Suporte de identificação de idioma**: métodos de identificação de idioma foram incluídos nesta API. Isso permite identificar o idioma dos textos de entrada e listar todos os idiomas suportados que podem ser detectados pela API.

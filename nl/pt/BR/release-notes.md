---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-23"

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
1.  Ligue a nova instância "Treinável" do serviço ao seu app em {{site.data.keyword.cloud_notm}}.
1.  Reúna os dados que foram usados para criar inicialmente os modelos customizados. Para obter mais informações, consulte [Estrutura dos dados de treinamento](/docs/services/language-translator/customizing.html#structure).
1.  Faça upload dos dados de treinamento para criar novos modelos customizados na instância "Treinável". Para obter mais informações, consulte [Treinando um modelo de tradução customizado](/docs/services/language-translator/customizing.html#training).
1.  Em seu app, aponte o campo "ModelID" para os novos modelos customizados.
1.  Desvincule o serviço anterior de seu app em {{site.data.keyword.cloud_notm}} e, em seguida, exclua-o.

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


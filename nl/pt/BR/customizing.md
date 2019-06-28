---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-13"

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

# Customizando seu modelo
{: #customizing}

A maioria dos modelos de tradução fornecidos no {{site.data.keyword.languagetranslatorshort}} pode ser estendida para aprender termos e frases customizados ou um estilo geral derivado de seus dados de tradução. Siga estas instruções para criar seu próprio modelo de tradução customizado.
{: shortdesc}

## Antes de Começar
{: #before-you-begin}

1. Certifique-se de que sua instância de serviço do {{site.data.keyword.languagetranslatorshort}} esteja em um plano de precificação Avançado ou Premium. Os planos Lite e Standard não suportam a customização.
1. Localize um modelo base customizável para seu par de idiomas. Será necessário o ID do modelo base para treinar seu modelo customizado.
    - Procure os modelos listados na página [Modelos de tradução](/docs/services/language-translator?topic=language-translator-translation-models). Procure o valor "**true**" na coluna **Customizável** e certifique-se de que os idiomas de **Origem** e de **Destino** do modelo correspondam ao seu par de idiomas.
    - Como alternativa, é possível usar o método de API [Listar modelos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/apidocs/language-translator#list-models) para procurar modelos programaticamente. É possível filtrar os resultados por idioma com os parâmetros `source` e `target`.

## Etapa 1: criar seus dados de treinamento
{: #create-your-training-data}

O serviço requer que os dados de treinamento sejam fornecidos no [formato de arquivo do Translation Memory Exchange (TMX)](#creating-tmx-files). É possível armazenar até 10 customizações para cada par de idiomas em uma instância de serviço. O serviço suporta dois tipos de solicitações de customização. É possível customizar um modelo com um glossário forçado ou com um corpus que contenha sentenças paralelas.

- Use um [glossário forçado](#forced-glossary-customization) para forçar determinados termos e frases a serem traduzidos de uma maneira específica.
- Use um [corpus paralelo](#parallel-corpus-customization) quando desejar que seu modelo customizado aprenda com padrões de tradução gerais em suas amostras. O que seu modelo aprende com um corpus paralelo pode melhorar os resultados da tradução para o texto de entrada no qual o modelo não foi treinado.

Depois de ter criado seus [arquivos do Translation Memory Exchange (TMX)](#creating-tmx-files), você estará pronto para treinar seu modelo.

## Etapa 2: treinar seu modelo
{: #train-your-model}

Use o método [Criar modelo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/apidocs/language-translator#create-model) para treinar seu modelo. Em sua solicitação, especifique o ID de um modelo base customizável e os dados de treinamento nos parâmetros `forced_glossary` ou `parallel_corpus`.

### Solicitação de exemplo
{: #train-model-example-request}

A solicitação de exemplo a seguir usa um arquivo de glossário forçado, _glossary.tmx_ para customizar o modelo base `en-es`. Consulte a seção [Customização do glossário forçado](#forced-glossary) para obter um exemplo de arquivo TMX de glossário forçado.

```bash
curl --user apikey:{apikey} -X POST --form forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v3/models?version=2018-05-01&base_model_id=en-es&name=custom-english-to-spanish"
```
{: pre}

A resposta da API conterá detalhes sobre seu modelo customizado, incluindo seu ID do modelo. Use o ID do modelo para verificar o status de seu modelo e para traduzir sentenças depois que o status do modelo se tornar "disponível".

```json
{
  "model_id": "96221b69-8e46-42e4-a3c1-808e17c787ca",
  "source": "en",
  "target": "es",
  "base_model_id": "en-es",
  "domain": "general",
  "customizable": false,
  "default_model": false,
  "owner": "4937aab7-0f3a-4a75-bee1-0b7a12b6b8",
  "status": "uploaded",
  "name": "custom-english-to-spanish",
  "train_log": null
}
```
{: codeblock}

## Etapa 3: verificar o status de seu modelo
{: #check-model-status}

O treinamento do modelo pode levar de alguns minutos (para glossários forçados) a várias horas (para grandes corpora paralelos), dependendo da quantidade de dados de treinamento envolvida. Para ver se o seu modelo está disponível, use o método [Obter modelo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/apidocs/language-translator#get-model-details) e especifique o ID de modelo recebido na resposta de serviço na Etapa 2. Além disso, é possível verificar o status de todos os seus modelos com o método [Listar modelos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/apidocs/language-translator#list-models).

O atributo de resposta `status` descreve o estado do modelo no processo de treinamento:

- `uploading`
- `uploaded`
- `dispatching`
- `queued`
- `training`
- `trained`
- `publishing`
- `available`

Quando o status do modelo é `available`, seu modelo está pronto para ser usado com sua instância de serviço. Se seu modelo for excluído ou se ele encontrar um erro no processo de treinamento, será possível ver um dos status a seguir:

- `excluir`
- `error`

### Solicitação de exemplo
{: #check-model-example-request}

O exemplo a seguir obtém informações para o modelo identificado pelo ID de modelo `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```bash
curl --user apikey:{apikey_value} "https://gateway.watsonplatform.net/language-translator/api/v3/models/96221b69-8e46-42e4-a3c1-808e17c787ca?version=2018-05-01"
```
{: pre}

## Etapa 4: traduzir texto com seu modelo customizado
{: #translate-text}

Para usar seu modelo customizado, especifique o texto que deseja traduzir e o ID do modelo customizado no método [Traduzir ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/apidocs/language-translator#translate).

### Solicitação de exemplo
{: #translate-text-example-request}

O exemplo a seguir traduz texto com o modelo customizado identificado pelo ID de modelo `96221b69-8e46-42e4-a3c1-808e17c787ca`.

```bash
curl --user apikey:{apikey_value} --request POST --header "Content-Type: application/json" --data '{"text":"Hello","model_id":"96221b69-8e46-42e4-a3c1-808e17c787ca"}' https://gateway.watsonplatform.net/language-translator/api/v3/translate?version=2018-05-01
```
{: pre}


## Customização do glossário forçado
{: #forced-glossary-customization}

Use um **glossário forçado** para configurar traduções obrigatórias para termos e frases específicos. Se desejar controle específico sobre o comportamento da tradução, use um glossário forçado.

- Formato de dados de treinamento: [TMX](#creating-tmx-files) (codificado por UTF-8)
- Tamanho máximo do arquivo: 10 MB
- É possível aplicar um glossário forçado a um modelo base ou a um modelo que tenha sido customizado com um corpus paralelo
- Limite um glossário forçado por modelo

Os exemplos de glossário forçado são sensíveis à capitalização, portanto, certifique-se de que seus dados de treinamento reflitam a capitalização do conteúdo que seu aplicativo encontrará.
{: tip}

### Exemplo de glossário forçado
{: #forced-glossary-example}

O exemplo a seguir mostra um arquivo TMX com dois pares de tradução. O primeiro par força os termos "international business machines" a serem preservados em inglês durante a tradução. Esse tipo de tradução forçada poderá ser útil se você desejar preservar os nomes de empresas capitalizados incorretamente em comunicações informais. O segundo par força o modelo a sempre usar "brevet" ao traduzir "patent".

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="phrase" o-tmf="" adminlang="en"
    srclang="en" datatype="PlainText" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>International Business Machines</seg>
      </tuv>
    </tu>
    <tu>
      <tuv xml:lang="en">
        <seg>patent</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>brevet</seg>
      </tuv>
    </tu>
  </body>
</tmx>
```
{: codeblock}



## Customização de corpus paralelos
{: #parallel-corpus-customization}

Use um **corpus paralelo** para fornecer traduções adicionais para o modelo base do qual aprender. Isso ajuda a adaptar o modelo base a um domínio específico. Como o modelo customizado resultante traduz texto depende do entendimento combinado do modelo do corpus paralelo e do modelo base.

- Formato de dados de treinamento: [TMX](#creating-tmx-files) (codificado por UTF-8)
- Comprimento máximo de pares de tradução: 80 palavras de origem
- Número mínimo de pares de tradução: 5.000
- Tamanho máximo do arquivo: 250 MB
- É possível enviar vários arquivos de corpus paralelos repetindo o parâmetro de formulário de várias partes `parallel_corpus`, desde que o tamanho acumulativo dos arquivos não exceda 250 MB.

### Exemplo de corpus paralelo
{: #parallel-corpus-example}

A seguir está uma pequena parte de um corpus paralelo do inglês para francês que foi transferido por download da [Coleção MultiUN ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://opus.nlpl.eu/MultiUN.php) disponível no website do corpus paralelo aberto do OPUS. É possível fazer download de uma versão compactada de todo o arquivo TMX [aqui ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://opus.nlpl.eu/download.php?f=MultiUN/en-fr.tmx.gz).


```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
<header creationdate="Tue Jan 29 12:49:40 2013"
          srclang="en"
          adminlang="en"
          o-tmf="unknown"
          segtype="sentence"
          creationtool="Uplug"
          creationtoolversion="unknown"
          datatype="PlainText" />
  <body>
    <tu>
      <tuv xml:lang="en"><seg>RESOLUTION 55/100</seg></tuv>
      <tuv xml:lang="fr"><seg>RÉSOLUTION 55/100</seg></tuv>
    </tu>
    <tu>
      <tuv xml:lang="en"><seg>Adopted at the 81st plenary meeting, on 4 December 2000, on the recommendation of the Committee (A/55/602/Add.2 and Corr.1, para. 94),The draft resolution recommended in the report was sponsored in the Committee by: Bolivia, Cuba, El Salvador, Ghana and Honduras. by a recorded vote of 106 to 1, with 67 abstentions, as follows:</seg></tuv>
      <tuv xml:lang="fr"><seg>Adoptée à la 81e séance plénière, le 4 décembre 2000, sur la recommandation de la Commission (A/55/602/Add.2, par. 94)Le projet de résolution recommandé dans le rapport de la Commission avait pour auteurs les pays suivants: Bolivie, Cuba, El Salvador, Ghana et Honduras., par 106 voix contre une, avec 67 abstentions, à la suite d'un vote enregistré, les voix s'étant réparties comme suit:</seg></tuv>
    </tu>
    ...
```
{: codeblock}

As melhorias gerais da customização do corpus paralelo são menos previsíveis do que os resultados obrigatórios obtidos da customização do glossário forçado. Por exemplo, considere a unidade de tradução a seguir do exemplo de corpus paralelo (linhas 172-175).

```xml
<tu>
  <tuv xml:lang="en"><seg>55/102. Globalization and its impact on the full enjoyment of all human rights</seg></tuv>
  <tuv xml:lang="fr"><seg>55/102. La mondialisation et ses effets sur le plein exercice des droits de l'homme</seg></tuv>
</tu>
```
{: codeblock}

Se você traduzir "55/102. Globalization and its impact on the full enjoyment of all human rights" com o modelo base `en-fr`, o serviço responderá com a tradução a seguir.

```
55/102. La mondialisation et ses effets sur la pleine jouissance de tous les droits de l'homme
```
{: codeblock}

Quando a mesma sentença de entrada é traduzida por um modelo customizado treinado com o corpus de exemplo, o serviço responde com uma tradução diferente que não é idêntica à tradução de amostra fornecida nos dados de treinamento.

```
55/102. La mondialisation et ses effets sur le plein exercice de tous les droits de l'homme
```
{: codeblock}

- O modelo customizado traduz "the full enjoyment" como "le plein exercice" em vez de "la pleine jouissance". A explicação provável para esse desvio do comportamento do modelo base é que há muitos exemplos no corpus em que "enjoyment" é traduzido como "exercice".
- O modelo customizado traduz "of all human rights" como "de tous les droits de l'homme" em vez de reproduzir o resultado da unidade de tradução, "des droits de l'homme". Esse comportamento reflete a compreensão coesa do modelo treinado do modelo base e todas as amostras de tradução relacionadas a "of all human rights" do corpus paralelo.

Em alguns casos, pode parecer que um modelo customizado treinado com um corpus paralelo está ignorando um exemplo específico fornecido. Nesses casos, tente procurar em seus dados de treinamento outras sentenças que possam estar influenciando o comportamento da tradução ou considere usar um glossário forçado se desejar controlar uma tradução específica.


## Criando arquivos TMX
{: #creating-tmx-files}

Para fornecer um glossário ou corpus de termos para treinar o serviço {{site.data.keyword.languagetranslatorshort}}, crie um documento que esteja codificado em UTF-8 para a especificação do Translation Memory Exchange (TMX) [versão 1.4 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ttt.org/oscarStandards/tmx/){: new_window}. TMX é uma especificação XML que é projetada para ferramentas de tradução de máquina. O exemplo a seguir é um arquivo de glossário formatado por TMX com duas unidades de conversão (elementos `<tu>`):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>international business machines</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>International Business Machines</seg>
      </tuv>
    </tu>
    <tu>
      <tuv xml:lang="en">
        <seg>patent</seg>
      </tuv>
      <tuv xml:lang="fr">
        <seg>brevet</seg>
      </tuv>
    </tu>
  </body>
</tmx>
```
{: codeblock}

Cada par de termo e tradução deve ser colocado entre as tags `<tu>`:

```xml
<tu>
  <tuv xml:lang="en">
    <seg>international business machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

O atributo `xml:lang` na tag `<tuv>` identifica o idioma no qual um termo é expresso, enquanto a tag `<seg>` contém o termo ou a tradução.

O serviço {{site.data.keyword.languagetranslatorshort}} usa somente os elementos `<tu>`, `<tuv>` e `<seg>`. Todos os outros elementos no exemplo são necessários para fazer um arquivo TMX válido ou são informativos, mas não são usados pelo serviço.



### Usando o exemplo como um modelo
{: #using-the-example-template}

Para usar o exemplo fornecido como um modelo para seu próprio glossário ou corpus, conclua as etapas a seguir:

1. Copie e cole o exemplo em um editor de texto.

2. Mude o atributo `srclang` da `<header>` para o código de idioma [![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} do idioma de origem que seu glossário ou corpus paralelo usa.

3. Mude o atributo `xml:lang` das tags `<tuv>` para o [código de idioma ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} correto de cada termo ou tradução.

4. Salve o documento com a extensão `.tmx` e a codificação UTF-8.

### Mudando um arquivo TMX para a codificação UTF-8
{: #changing-tmx-file-to-utf-8}

É possível usar várias ferramentas para criar ou gerar arquivos TMX. Geralmente, os arquivos TMX gerados são codificados por UTF-16, por padrão. O serviço {{site.data.keyword.languagetranslatorshort}} aceita apenas arquivos TMX codificados por UTF-8. Para mudar a codificação de um arquivo TMX, conclua as seguintes etapas:

1. Abra o arquivo TMX em um editor de texto.

1. Mude o cabeçalho XML (se presente) de `<?xml ... encoding="utf-16"?>` para `<?xml ... encoding="utf-8"?>`.

1. Salve o arquivo com um novo nome e com a saída de codificação UTF-8.

Para mudar mudar a codificação de arquivo, os usuários do Mac podem atualizar o cabeçalho XML do documento, conforme descrito na etapa 2 e, em seguida, executar o comando a seguir no Terminal:

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}


## Excluindo um modelo de tradução customizado
{: #deleting-a-custom-model}

Para excluir um modelo de tradução customizado, use o método [Excluir modelo ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cloud.ibm.com/apidocs/language-translator#delete-model).

O comando a seguir exclui o modelo de tradução com o ID de modelo `3e7dfdbe-f757-4150-afee-458e71eb93fb`.

```curl
curl --user apikey:{apikey_value} --request DELETE "https://gateway.watsonplatform.net/language-translator/api/v3/models/3e7dfdbe-f757-4150-afee-458e71eb93fb?version=2018-05-01"
```
{: codeblock}

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

# Customizando seu modelo
{: #customizing}

Ao criar um tradutor para ser usado pelo suporte ao cliente, você deseja tratar de maneira específica nas conversas um determinado termo da empresa? Ao criar uma forma para os engenheiros em um país consultarem dados de patentes em outro idioma, você costuma arquivar as patentes em uma tecnologia específica? Use seus próprios dados para criar um dicionário customizado e um modelo de conversão customizado na API do {{site.data.keyword.languagetranslatorshort}}.
{: shortdesc}

É possível customizar o modelo do {{site.data.keyword.languagetranslatorshort}} das maneiras a seguir:

- Ensine o serviço sobre os pares de termos ou frases correspondentes em um idioma de origem e de destino. Forneça um *glossário forçado*, que contenha pares de termos ou frases que sejam absolutas, termos definitivos que você deseja que o serviço de tradução trate como obrigatórios. Ou forneça um *corpus paralelo* que contenha pares de termos ou frases que sirvam como sugestões de tradução alternativa que você deseja que o serviço de tradução considere.
- Faça upload de um corpo de texto grande em um idioma de destino (referido como um *corpus monolíngue*) para servir como uma amostra de idioma que o serviço pode avaliar e usar para melhorar a qualidade de tradução geral.

Para ver a lista de modelos que você pode customizar, use o método `GET /v2/models` e procure o parâmetro de resposta `customizable=true` na resposta para cada modelo de linguagem.

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

Cada modelo customizável pode armazenar até 10 customizações por instância de serviço.

## Estrutura dos dados de treinamento
{: #structure}

Para fornecer um glossário ou corpus de termos para treinar o serviço {{site.data.keyword.languagetranslatorshort}}, crie um documento que esteja codificado em UTF-8 para a especificação do Translation Memory Exchange (TMX) [versão 1.4 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ttt.org/oscarstandards/tmx/tmx14.dtd){: new_window}. TMX é uma especificação XML que é projetada para ferramentas de tradução de máquina. O exemplo a seguir é um arquivo de glossário formatado por TMX com dois pares de termos e de traduções:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tmx version="1.4">
  <header creationtool="" creationtoolversion=""
    segtype="sentence" o-tmf="" adminlang="EN"
    srclang="en" datatype="rtf" o-encoding="UTF-8" />
  <body>
    <tu>
      <tuv xml:lang="en">
        <seg>International Business Machines</seg>
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

Cada par de termos e de traduções deve ser colocado em `<tu>` tags:

```xml
<tu>
  <tuv xml:lang="en">
    <seg>International Business Machines</seg>
  </tuv>
  <tuv xml:lang="fr">
    <seg>International Business Machines</seg>
  </tuv>
</tu>
```
{: codeblock}

O atributo `xml:lang` na tag `<tuv>` identifica o idioma no qual um termo é expresso, enquanto a tag `<seg>` contém o termo ou a tradução.

O serviço {{site.data.keyword.languagetranslatorshort}} usa apenas os elementos `<tu>`, `<tuv>`
e `<seg>`. Todos os outros elementos no exemplo são necessários para fazer um arquivo TMX válido ou são informativos, mas não são usados pelo serviço.

O exemplo anterior mostra como padronizar definitivamente a tradução de um termo técnico, como 'patente', e como customizar a tradução de um nome da empresa, como 'International Business Machines'. No modelo padrão, 'International Business Machines' pode ser traduzido como 'Máquinas Internacionais Comerciais', mas isso não deve ser traduzido porque é o nome de uma empresa.

## Usando o exemplo como um modelo

Para usar o exemplo fornecido como um modelo para seu próprio glossário ou corpus, conclua as etapas a seguir:

1.  Copie e cole o exemplo em um editor de texto.

1.  Mude o atributo `srclang` da `<header>` para o código de idioma [![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} do idioma de origem que seu glossário ou corpus paralelo usa.

1.  Mude o atributo `xml:lang` das tags `<tuv>` para o código de idioma [![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www-01.sil.org/iso639-3/codes.asp){: new_window} para cada termo ou tradução.

    O serviço {{site.data.keyword.languagetranslatorshort}} usa códigos de idioma ISO 639-1 para todos os idiomas, exceto árabe egípcio, que usa o código ISO 639-3.

1.  Salve o documento com a extensão `.tmx` e a codificação UTF-8.

### Mudando um arquivo TMX para a codificação UTF-8

É possível usar várias ferramentas para criar ou gerar arquivos TMX. Geralmente, os arquivos TMX gerados são codificados por UTF-16, por padrão. O serviço {{site.data.keyword.languagetranslatorshort}} aceita apenas arquivos TMX codificados por UTF-8. Para mudar a codificação de um arquivo TMX, conclua as seguintes etapas:

1.  Abra o arquivo TMX em um editor de texto.

1.  Mude o cabeçalho XML (se presente) de `<?xml ... encoding="utf-16"?>` para `<?xml ... encoding="utf-8"?>`.

1.  Salve o arquivo com um novo nome e com a saída de codificação UTF-8.

Para mudar mudar a codificação de arquivo, os usuários do Mac podem atualizar o cabeçalho XML do documento, conforme descrito na etapa 2 e, em seguida, executar o comando a seguir no Terminal:

```bash
iconv -f utf-16 -t utf-8 <utf-16_file_name.tmx> <new_utf-8_file_name.tmx>
```
{: pre}

## Treinando um modelo de tradução customizado
{: #training}

Use o método `POST /v2/models` para fazer upload de seu arquivo TMX e treinar seu modelo de tradução. Especifique pelo menos uma das seguintes opções de arquivo para treinar seu modelo customizado:

- `forced_glossary`: um arquivo TMX codificado por UTF-8 que contém os pares de termos correspondentes nos idiomas de origem e de destino que são vistos como absolutos pelo sistema. Esse arquivo sobrescreve completamente os dados do domínio original.

    Glossários forçados são limitados a um tamanho de arquivo de 10 MB. Atualmente é possível fazer upload apenas de um arquivo de glossário forçado por modelo de tradução.
    
- `parallel_corpus`: um arquivo TMX codificado por UTF-8 que contém frases correspondentes nos idiomas de origem e de destino, que servem como exemplos para o Watson. Os corpora paralelos diferem de glossários forçados porque eles não sobrescrevem os dados do domínio original.

    Para treinar com sucesso um modelo customizado, um documento corpus paralelo deve conter um mínimo de 5.000 pares de termos e traduções.
    
- `monolingual_corpus`: um arquivo de texto sem formatação codificado por UTF-8 que contém um corpo de texto no idioma de destino que está relacionado ao que você está traduzindo. Fornecer um corpus monolíngue melhora traduções literais, tornando a tradução mais fluente e natural.

    Para treinar com sucesso um modelo customizado, um documento corpus monolíngue deve conter no mínimo 1.000 sentenças.

O tamanho acumulativo de arquivo de todo o glossário e arquivos de corpus transferidos por upload é limitado a 250 MB. Dependendo do tamanho dos arquivos transferidos por upload, o treinamento pode variar de minutos, para um glossário, até várias horas, para um corpus grande.

O exemplo de curl a seguir usa a opção de arquivo`forced_glossary`.
1. Faça download da amostra de arquivo TMX da seção [Estrutura dos dados de treinamento](#structure)
1. Use o domínio de notícias francesas (en-fr) como o modelo base. Qualquer coisa que é especificada no arquivo TMX sobrescreve completamente os dados do domínio original.

    Para consultar todos os domínios de modelo que o serviço {{site.data.keyword.languagetranslatorshort}} suporta, use o método `GET v2/models`:

```curl
curl -u "{username}":"{password}" -X POST -F base_model_id=en-fr -F name="test_glossary" -F forced_glossary=@glossary.tmx "https://gateway.watsonplatform.net/language-translator/api/v2/models"
```
{: codeblock}

O método `POST/v2/models` responde com um código `200` e um novo `model_id`. Use o `model_id` ao traduzir textos com esse modelo customizado recentemente.

## Monitoramento de treinamento

O tamanho do arquivo de treinamento TMX afeta o tempo de treinamento de uma solicitação `POST /v2/models`. Para monitorar o progresso do treinamento e se o treinamento foi concluído com êxito, use o método `GET /v2/models/<model_id>` e procure o valor do parâmetro `status` na resposta.

Esse exemplo de comando fornece informações sobre o modelo e verifica o status do treinamento que foi iniciado na seção [Treinando o seu modelo de tradução](#training). Esse comando usa uma solicitação de corpo vazio.

```curl
curl -u "{username}":"{password}" "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}

O parâmetro de resposta `STATUS` descreve o estado do modelo no processo de treinamento:

- `uploading`
- `uploaded`
- `dispatching`
- `queued@<#>`
- `training`
- `trained`
- `publishing`
- `available`

Quando o status do modelo é `available`, seu modelo está pronto para ser usado com sua instância de serviço. Se o seu modelo foi excluído ou se ele encontrar um erro no processo de treinamento, será possível ver um dos seguintes erros:

- `excluir`
- `error`

## Usando um modelo de tradução customizado

Depois de treinar um modelo de tradução customizado, especifique o model\_id do modelo de tradução para usá-lo com os métodos `POST /v2/translate` ou `GET /v2/translate`.

O exemplo a seguir chama o modelo inglês para francês, que foi customizado na seção [Treinando um modelo de tradução customizado](#training).

```curl
curl -u "{username}":"{password}" --header "Content-Type: application/json" -X POST --data "{\"model_id\": \"3e7dfdbe-f757-4150-afee-458e71eb93fb\",\"text\": \"Hello, my name is Watson, and I work for International Business Machines. How can I help you today?\"}" https://gateway.watsonplatform.net/language-translator/api/v2/translate 
```
{: codeblock}

O serviço {{site.data.keyword.languagetranslatorshort}} avalia a qualidade da tradução usando os padrões BLEU (subestudo de avaliação bilíngue), bem como padrões desenvolvidos pela IBM. Os resultados podem variar dependendo do par de idiomas, do dialeto usado ou do domínio de seus dados.

## Excluindo um modelo de tradução customizado

Quando um modelo de tradução se torna desatualizado, pode ser que você deseje excluí-lo. Para excluir um modelo de tradução customizado, use o método `DELETE /v2/models/<model_id>`. Para recuperar os IDs de modelo de todos os modelos de tradução, se customizado ou padrão, use o método `GET /v2/models`.

O comando a seguir exclui o modelo de tradução que foi criado nestes exemplos.

```curl
curl -u "{username}":"{password}" -X DELETE "https://gateway.watsonplatform.net/language-translator/api/v2/models/3e7dfdbe-f757-4150-afee-458e71eb93fb"
```
{: codeblock}


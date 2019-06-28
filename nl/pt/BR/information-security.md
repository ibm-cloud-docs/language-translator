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

# Segurança de informações
{: #information-security}

A IBM está comprometida em fornecer aos nossos clientes e parceiros soluções inovadoras de privacidade de dados, segurança e governança.
{: shortdesc}

**Aviso:**
os clientes são responsáveis por assegurar sua própria conformidade com várias leis e regulamentações, incluindo o Regulamento Geral sobre a Proteção de Dados da União Europeia. Os clientes são os únicos responsáveis por obter aconselhamento de consultoria jurídica competente quanto à identificação e interpretação de quaisquer leis e regulamentos relevantes que possam afetar os negócios dos clientes e quaisquer ações que os clientes possam precisar tomar para cumprir tais leis e regulamentações.

Os produtos, serviços e outros recursos descritos aqui não são adequados para todas as situações do cliente e podem ter disponibilidade restrita. A IBM não fornece aviso jurídico, contábil ou de auditoria nem representa ou garante que os seus serviços ou produtos assegurarão que os clientes estejam em conformidade com qualquer lei ou regulamentação.

Se você precisar solicitar suporte do GDPR para recursos do {{site.data.keyword.cloud}} {{site.data.keyword.watson}} que forem criados

-   Na União Europeia (UE), veja [Solicitando suporte para recursos do IBM Cloud Watson criados na União Europeia](/docs/services/watson/getting-started-gdpr-sar.html#request-EU).
-   Fora da UE, veja [Solicitando suporte para recursos fora da União Europeia](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU).

## Regulamento Geral sobre a Proteção de Dados (GDPR) da União Europeia
{: #gdpr}

A IBM está comprometida em fornecer aos nossos clientes e parceiros soluções inovadoras de privacidade de dados, segurança e controle para auxiliá-los em sua jornada para a conformidade com GDPR.

Saiba mais sobre a própria jornada de prontidão GDPR da IBM e nossas capacidades e ofertas de GDPR para suportar sua jornada de conformidade [aqui ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/gdpr){: new_window}.

## Identificando e excluindo dados no Language Translator
{: #gdpr-in-service}

O serviço {{site.data.keyword.languagetranslatorshort}} armazena em cache temporariamente os dados de tradução de solicitações de tradução e armazena os dados de treinamento usados para criar modelos customizados.

### Dados e documentos de tradução
{: #translation-data-and-documents}

Ao enviar texto para o {{site.data.keyword.languagetranslatorshort}} no método **Traduzir**, o serviço armazenará em cache o texto de origem e o resultado da tradução para melhorar o desempenho quando receber o mesmo texto em solicitações subsequentes do método **Traduzir**. O texto de tradução em cache é excluído somente depois de não ser usado por um período de 15 dias.

Os documentos enviados para o serviço para tradução por meio do método **Traduzir documento** são armazenados internamente para fornecer o arquivo traduzido e para suportar solicitações adicionais para **Traduzir documento** por referência ao documento original transferido por upload. O documento original e quaisquer documentos traduzidos associados são excluídos somente depois de não serem usados em solicitações subsequentes de **Traduzir documento** por um período de 15 dias. O método **Excluir documento** pode ser usado para excluir documentos antes do prazo final de exclusão. 

Os dados e os documentos de tradução são criptografados em andamento e em repouso.

### Dados de treinamento do modelo customizado
{: #custom-model-training-data}

Ao treinar um modelo customizado, os dados de treinamento usados para criar o modelo são armazenados para fornecer a você o modelo customizado. Os modelos customizados e os dados de treinamento são criptografados em andamento e em repouso. Os dados de treinamento criptografados persistem no armazenamento até que o modelo seja excluído com o método **Excluir modelo**.

Os modelos customizados podem ser excluídos somente no nível de modelo. Os dados do componente usados para criar um modelo customizado não podem ser excluídos. Se você usar dados pessoais ao criar um modelo customizado, um modelo customizado separado deverá ser criado para cada cliente e o `name` do modelo rotulado para identificar o cliente para que ele possa ser excluído, se solicitado. 

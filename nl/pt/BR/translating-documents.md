---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

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

# Traduzindo documentos (Beta)
{: #document-translator-tutorial}


Traduza arquivos de um idioma para outro e, ao mesmo tempo, preserve o formato original. Mais de 12 formatos de arquivo diferentes podem ser traduzidos, incluindo o MS Office, o Open Office e o PDF.
{:shortdesc}

## Antes de Começar
{: #prerequisites}

- [Introdução](/docs/services/language-translator?topic=language-translator-getting-started) ao {{site.data.keyword.languagetranslatorshort}}. Serão necessárias suas credenciais de serviço do {{site.data.keyword.languagetranslatorshort}} (`apikey` e `url`).
- Certifique-se de que o documento que você deseja traduzir atenda aos requisitos a seguir:
    - Tamanho máximo do arquivo: **20 MB**
    - [Formatos de arquivo suportados](#supported-file-formats)
    - [Modelos de tradução suportados](/docs/services/language-translator?topic=language-translator-translation-models)

## Etapa 1: enviar um documento para tradução
{: #submit-document-to-translate}

A solicitação de exemplo a seguir envia um arquivo de exemplo *curriculum.pdf* para o serviço e o traduz do inglês para francês. Substitua `{apikey}` e `{url}` por suas credenciais de serviço e substitua `curriculum.pdf` por um caminho relativo para seu arquivo.

Solicitação de exemplo:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "source=en" \
--form "target=fr" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Para traduzir um documento com um [modelo customizado](/docs/services/language-translator?topic=language-translator-customizing), use o parâmetro **model_id**. A solicitação a seguir traduz o documento com o modelo customizado identificado pelo ID de modelo `96221b69-8e46-42e4-a3c1-808e17c787ca`.

Solicitação de exemplo:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "file=@curriculum.pdf" \
--form "model_id=96221b69-8e46-42e4-a3c1-808e17c787ca" \
{url}/v3/documents?version=2018-05-01
```
{: pre}


Uma solicitação bem-sucedida retornará um `document_id` na resposta.


Resposta de exemplo:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "processing",
  "created": "2018-10-11T03:31:25"
}
```
{: codeblock}

## Etapa 2: verificar o status da tradução
{: #check-translation-status}

Depois de enviar um documento para tradução, é possível verificar o status da tradução para descobrir quando o documento traduzido está disponível para download. A solicitação de exemplo a seguir verifica o status da tradução do documento com o ID de documento `bae02796-0d28-435c-9115-888359fdde62`. 

Solicitação de exemplo:
```bash
curl -X GET \
--user "apikey:{apikey}" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Resposta de exemplo:
```json
{
  "document_id": "bae02796-0d28-435c-9115-888359fdde62",
  "filename": "curriculum.pdf",
  "model_id": "en-fr",
  "source": "en",
  "target": "fr",
  "status": "available",
  "created": "2018-10-11T03:31:25",
  "completed": "2018-10-11T03:31:38"
}
```
{: codeblock}

Quando o `status` na resposta é `available`, o documento traduzido está pronto para download.

## Etapa 3: fazer download do documento traduzido
{: #download-translated-document}

A solicitação de exemplo a seguir salva o documento traduzido com o ID de documento `bae02796-0d28-435c-9115-888359fdde62` no arquivo *curriculum-fr.pdf*. 

Solicitação de exemplo:
```bash
curl -X GET \
--user "apikey:{apikey}" \
--output "curriculum-fr.pdf" \
{url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62/translated_document?version=2018-05-01
```
{: pre}

## Etapa 4: traduzir um documento enviado anteriormente
{: #translate-document-by-reference}

A solicitação de exemplo a seguir referencia o arquivo *curriculum.pdf* em inglês original com o `document_id` `bae02796-0d28-435c-9115-888359fdde62` e o traduz para o português.

Solicitação de exemplo:
```bash
curl -X POST \
--user "apikey:{apikey}" \
--form "document_id=bae02796-0d28-435c-9115-888359fdde62" \
--form "source=en" \
--form "target=pt" \
{url}/v3/documents?version=2018-05-01
```
{: pre}

Resposta de exemplo:
```json
{
  "document_id": "a0ge2746-ad38-7d5c-7025-4cd3g9f451ab"
}
```
{: codeblock}

A resposta contém um novo `document_id`. Repita as etapas dois e três com seu novo `document_id` para verificar o status da tradução e para fazer download do arquivo traduzido depois que ele estiver disponível.

## Etapa 5: excluir documentos
{: #delete-documents}

Os documentos originais e quaisquer documentos traduzidos associados são excluídos automaticamente depois de não terem sido usados por um determinado período de tempo. Consulte  [ Segurança de informações ](/docs/services/language-translator?topic=language-translator-information-security)  para obter mais detalhes.
{: tip}

Para excluir documentos manualmente, use o método **Excluir documento**. Neste tutorial, o arquivo *curriculum.pdf* em inglês estava envolvido com duas traduções, portanto, são necessárias duas solicitações para excluir todas as cópias do documento original.

Exclua o envio original de *curriculum.pdf* e a tradução em francês:
```bash
curl -X DELETE \ --user "apikey:{apikey}" \ {url}/v3/documents/bae02796-0d28-435c-9115-888359fdde62?version=2018-05-01
```
{: pre}

Exclua a duplicata do arquivo *curriculum.pdf* original e a tradução em português:
```bash
curl -X DELETE \ --user "apikey:{apikey}" \ {url}/v3/documents/a0ge2746-ad38-7d5c-7025-4cd3g9f451ab?version=2018-05-01
```
{: pre}

## Formatos de arquivo suportados
{: #supported-file-formats}

-  Microsoft Office
    - Word: `.doc`, `.docx`
    - PowerPoint: `.ppt`, `.pptx`
    - Excel: `.xls`, `.xlsx`
    - Formato Rich Text: `.rtf`
- Open Office
    - Writer: `.odt`
    - Impress: `.odp`
    - Calc: `.ods`
- Outros formatos
    - PDF: `.pdf`
    - HTML: `.htm`, `.html`
    - XML: `.xml`
    - JSON: `.json` (valores com o tipo `string` ou `string array` são traduzidos)
    - Texto: `.txt`

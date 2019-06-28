---

copyright:
  years: 2019
lastupdated: "2019-03-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Alta disponibilidade e recuperação de desastre
{: #ha-dr}

O {{site.data.keyword.languagetranslatorfull}} é altamente disponível em vários locais do {{site.data.keyword.cloud_notm}} (por exemplo, Dallas e Washington, DC). No entanto, a recuperação de possíveis desastres que afetam todo um local requer planejamento e preparação.
{: shortdesc}

Você é responsável por entender sua configuração, customização e uso do serviço. Você também é responsável por estar pronto para recriar uma instância do serviço em uma nova localização e por restaurar seus dados em qualquer localização. Consulte [Como assegurar tempo de inatividade zero? ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window} para obter mais informações.

## alta disponibilidade
{: #high-availability}

O {{site.data.keyword.languagetranslatorshort}} suporta alta disponibilidade sem nenhum ponto único de falha. O serviço alcança alta disponibilidade de forma automática e transparente usando o recurso multi-zone region (MZR) fornecido pelo {{site.data.keyword.cloud_notm}}.

O{{site.data.keyword.cloud_notm}}permite diversas zonas que não compartilham um único ponto de falha em um único local. Ele também fornece balanceamento de carga automático entre as zonas dentro de uma região.


## Recuperação de desastre
{: #disaster-recovery}

No caso de uma falha catastrófica em uma região, conclua as etapas a seguir.

- Crie uma nova instância de serviço do {{site.data.keyword.languagetranslatorshort}}.
- Ajuste seu software de aplicativo para usar a nova URL da instância de serviço e as credenciais.
- Crie novos modelos customizados para substituir qualquer um que você tenha perdido. Use os mesmos glossários forçados e corpora paralelos usados para criar seus modelos customizados anteriores. Consulte [Customizando seu modelo](/docs/services/language-translator?topic=language-translator-customizing#customizing) para obter mais informações sobre modelos customizados.
  - Para se preparar para uma recuperação rápida, armazene cópias de backup de seus arquivos de treinamento sempre que criar um modelo. É possível usar os campos `name` e `model_id` de seus modelos customizados junto com os nomes de arquivos de seus arquivos de treinamento para manter um registro dos arquivos usados para cada modelo. 
- Ajuste seu software de aplicativo para usar os novos modelos customizados.


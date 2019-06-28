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

# 고가용성 및 재해 복구
{: #ha-dr}

{{site.data.keyword.languagetranslatorfull}}는 여러
{{site.data.keyword.cloud_notm}} 위치(예: 댈러스 및 워싱턴, DC)에서 많이 사용할 수 있습니다. 그러나 전체 위치에 영향을 미치는 잠재적인 재해로부터 복구하려면 계획과 준비가 필요합니다.
{: shortdesc}

사용자가 서비스의 구성, 사용자 정의 및 사용을 파악해야 합니다. 새로운 위치에 서비스의 인스턴스를 다시 작성하고 임의 위치에 데이터를 복원할 준비도 해야 합니다. 자세한 정보는 [작동 중단 시간이 없게 하는 방법![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/overview?topic=overview-zero-downtime#zero-downtime){: new_window}을 참조하십시오.

## 고가용성
{: #high-availability}

{{site.data.keyword.languagetranslatorshort}}에서는 단일 실패 지점과 함께 고가용성을 지원합니다. 이 서비스에서는 {{site.data.keyword.cloud_notm}}에서 제공하는 다중 지역(MZR) 기능을 사용하여 자동으로 투명하게 고가용성을 달성합니다.

{{site.data.keyword.cloud_notm}}에서는 단일 위치에서 단일 실패 지점을 공유하지 않는 여러 구역을 사용할 수 있습니다. 지역에 있는 구역 간의 자동 로드 밸런싱도 제공합니다.


## 재해 복구
{: #disaster-recovery}

지역에서 돌발적으로 고장이 발생하는 경우 다음 단계를 완료하십시오.

- 새로운 {{site.data.keyword.languagetranslatorshort}} 서비스 인스턴스를 작성하십시오.
- 새 서비스 인스턴스 URL과 인증 정보를 사용하도록 애플리케이션 소프트웨어를 조정하십시오.
- 유실한 사용자 정의 모델을 대체할 새로운 사용자 정의 모델을 작성하십시오. 이전 사용자 정의 모델을 작성하는 데 사용한 강제 실행 용어집과 병렬 말뭉치를 동일하게 사용하십시오. 사용자 정의 모델에 관한 자세한 정보는 [모델 사용자 정의](/docs/services/language-translator?topic=language-translator-customizing#customizing)를 참조하십시오.
  - 빠른 복구를 준비하려면 모델을 작성할 때마다 훈련 파일의 백업 사본을 저장하십시오. 사용자 정의 모델의 `name` 및 `model_id` 필드와 학습 파일의 파일 이름을 사용하여 각 모델에 사용하는 파일의 레코드를 보관할 수 있습니다. 
- 새로운 사용자 정의 모델을 사용하도록 애플리케이션 소프트웨어를 조정하십시오.


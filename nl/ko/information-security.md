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

# 정보 보안
{: #information-security}

IBM은 고객과 파트너에게 혁신적인 데이터 개인정보 보호, 보안 및 통제 솔루션을 제공하기 위해 노력하고 있습니다.
{: shortdesc}

**주의사항:**
고객은 유럽 연합 일반 개인정보 보호법률(General Data Protection Regulation, "GDPR")을 포함한 다양한 법령과 규정을 준수해야 할 책임이 있습니다. 고객은 고객의 비즈니스에 영향을 줄 수 있는 관련 법령 및 규정에 대한 확인과 해석,
그러한 법령 및 규정의 준수를 위해 필요한 고객의 모든 조치와 관련하여 적절한 법률 자문을 받아야 할
단독 책임이 있습니다.

여기에서 설명하는 제품, 서비스 및 기타 기능은 일부 고객의 상황에는 해당되지 않을 수 있으며
그 가용성이 제한될 수 있습니다. IBM은 법률, 회계 또는 감사 관련 자문을 제공하지 않으며, IBM의 서비스나 제품 사용이 고객의 관련 법령이나 규정 준수를 보장한다는 진술이나 보증을 제공하지 않습니다.

작성된 {{site.data.keyword.cloud}} {{site.data.keyword.watson}} 리소스에 대해 GDPR 지원을 요청해야 하는 경우

-   유럽 연합(EU)에서는 [유럽 연합에서 작성된 IBM Cloud Watson 리소스 지원 요청](/docs/services/watson/getting-started-gdpr-sar.html#request-EU)을 참조하십시오.
-   EU 외부에서는 [유럽 연합 외부에서 리소스 지원 요청](/docs/services/watson/getting-started-gdpr-sar.html#request-non-EU)을 참조하십시오.

## 일반 개인정보 보호법률(European Union General Data Protection Regulation, "GDPR")
{: #gdpr}

IBM은 고객과 파트너가 GDPR 규제를 준수하는 데 도움을 줄 수 있도록 혁신적인 데이터 개인정보 보호, 보안 및 통제 솔루션을 제공하기 위해 노력하고 있습니다.

사용자가 규제를 준수하도록 지원하기 위한 IBM의 자체 GDPR 준비 과정 및 GDPR 기능과 오퍼링에 대한 자세한 정보는 [여기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://www.ibm.com/gdpr){: new_window}을 클릭하십시오.

## Language Translator에서 레이블 지정 및 데이터 삭제
{: #gdpr-in-service}

{{site.data.keyword.languagetranslatorshort}} 서비스에서는 번역 요청의 번역 데이터를 임시로 캐싱하고 사용자 정의 모델을 작성하는 데 사용하는 훈련 데이터를 저장합니다.

### 번역 데이터 및 문서
{: #translation-data-and-documents}

**번역** 메소드로 {{site.data.keyword.languagetranslatorshort}}에 텍스트를 보내면 서비스에서 소스 텍스트와 번역 결과를 캐싱하여 후속 **번역** 요청에서 동일한 텍스트를 받을 때 성능을 향상시킵니다. 캐싱된 번역 데이터는 15일 동안 사용하지 않은 후에만 삭제됩니다.

**문서 번역** 메소드를 통해 번역하기 위해 서비스에 제출된 문서는 번역된 파일을 제공하고 참조별로 추가 **문서 번역** 요청을 원래 업로드한 문서에 제공하기 위해 내부에 저장됩니다. 원본 문서 및 연관된 모든 번역 문서는 후속 **문서 번역** 요청에서 15일 동안 사용되지 않는 경우에만 삭제됩니다. 삭제 최종 기한 전에 문서를 삭제하려면 **문서 삭제** 메소드를 사용할 수 있습니다. 

번역 데이터 및 문서는 이동 중이나 저장 중에 암호화됩니다.

### 사용자 정의 모델 훈련 데이터
{: #custom-model-training-data}

사용자 정의 모델을 훈련하면, 사용자 정의 모델을 제공하기 위해 사용자가 모델을 작성하는 데 사용하는 훈련 데이터를 저장합니다. 사용자 정의 모델과 훈련 데이터는 이동 중이나 저장 중에 암호화됩니다. 암호화된 훈련 데이터는 **모델 삭제** 메소드를 사용하여 모델을 삭제할 때까지 스토리지에 유지됩니다.

사용자 정의 모델은 모델 레벨에서만 삭제할 수 있습니다. 사용자 정의 모델을 작성하는 데 사용한 컴포넌트 데이터는 삭제할 수 없습니다. 사용자 정의 모델을 작성할 때 개인 데이터를 사용하는 경우 요청 시 삭제할 수 있도록 고객을 식별하는 레이블이 지정된 모델 `name`과 고객별로 개별 사용자 정의 모델을 작성해야 합니다. 

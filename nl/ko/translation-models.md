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

# 번역 모델
{: #translation-models}

{{site.data.keyword.languagetranslatorshort}}는 다음 언어를 번역할 수 있습니다.
아래의 목록에서 언어를 클릭하면 호환 가능한 번역 모델의 목록을 볼 수 있습니다.

**모델 나열** API 메소드를 사용하여 사용자 정의 모델을 포함하여 사용 가능한 번역 모델도 볼 수 있습니다. `source` 및 `target` 매개변수를 사용하여 언어별로 결과를 필터링할 수 있습니다. 다음 예에서는 영어를 스페인어로 번역할 수 있는 모델을 나열합니다.

```bash
curl --user apikey:{apikey_value} https://gateway.watsonplatform.net/language-translator/api/v3/models?source=en&target=es&version=2018-05-01
```
{: pre}

  - [아랍어](#arabic)
  - [카탈로니아어](#catalan)
  - [중국어](#chinese-simplified)
  - [대만어](#chinese-traditional)
  - [     체코어
    ](#czech)
  - [     덴마크어
    ](#danish)
  - [     네덜란드어
    ](#dutch)
  - [영어](#english)
  - [     핀란드어
    ](#finnish)
  - [프랑스어](#french)
  - [독일어](#german)
  - [     그리스어
    ](#greek)
  - [     히브리어
    ](#hebrew)
  - [     힌디어
    ](#hindi)
  - [     헝가리어
    ](#hungarian)
  - [이탈리아어](#italian)
  - [일본어](#japanese)
  - [한국어](#korean)
  - [노르웨이 부크몰어](#norwegian-bokmal)
  - [     폴란드어
    ](#polish)
  - [포르투갈어](#portuguese)
  - [     러시아어
    ](#russian)
  - [스페인어](#spanish)
  - [     스웨덴어
    ](#swedish)
  - [     터키어
    ](#turkish)

## 아랍어
{: #arabic}

다음 모델은 아랍어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>ar-en</code>
    </td>
    <td>
     아랍어(<code>ar</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 카탈로니아어
{: #catalan}

다음 모델은 카탈로니아어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>ca-es</code>
    </td>
    <td>
     카탈로니아어(<code>ca</code>)
    </td>
    <td>
     스페인어(<code>es</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 중국어
{: #chinese-simplified}

다음 모델은 중국어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-en</code>
    </td>
    <td>
     중국어(<code>zh</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 대만어
{: #chinese-traditional}

다음 모델은 대만어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>zh-TW</code>-en
    </td>
    <td>
     대만어(<code>zh-TW</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      체코어
{: #czech}

다음 모델은 체코어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>cs-en</code>
    </td>
    <td>
     체코어(<code>cs</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      덴마크어
{: #danish}

다음 모델은 덴마크어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>da-en</code>
    </td>
    <td>
     덴마크어(<code>da</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      네덜란드어
{: #dutch}

다음 모델은 네델란드어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>nl-en</code>
    </td>
    <td>
     네델란드어(<code>nl</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 영어
{: #english}

다음 모델은 영어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>en-ar</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     아랍어(<code>ar</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-cs</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     체코어(<code>cs</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-da</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     덴마크어(<code>da</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-de</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     독일어(<code>de</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-el</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     그리스어(<code>el</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-es</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     스페인어(<code>es</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-fi</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     핀란드어(<code>fi</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-fr</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     프랑스어(<code>fr</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-he</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     히브리어(<code>he</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-hi</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     힌디어(<code>hi</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-it</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     이탈리아어(<code>it</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-ja</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     일본어(<code>ja</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-ko</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     한국어(<code>ko</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-nb</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     노르웨이 부크몰어(<code>nb</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-nl</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     네델란드어(<code>nl</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-pl</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     폴란드어(<code>pl</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-pt</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     포르투갈어(<code>pt</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-ru</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     러시아어(<code>ru</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-sv</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     스웨덴어(<code>sv</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-tr</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     터키어(<code>tr</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-zh</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     중국어(<code>zh</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>en-zh-TW</code>
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     대만어(<code>zh-TW</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      핀란드어
{: #finnish}

다음 모델은 핀란드어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>fi-en</code>
    </td>
    <td>
     핀란드어(<code>fi</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 프랑스어
{: #french}

다음 모델은 프랑스어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>fr-de</code>
    </td>
    <td>
     프랑스어(<code>fr</code>)
    </td>
    <td>
     독일어(<code>de</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>fr-en</code>
    </td>
    <td>
     프랑스어(<code>fr</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>fr-es</code>
    </td>
    <td>
     프랑스어(<code>fr</code>)
    </td>
    <td>
     스페인어(<code>es</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 독일어
{: #german}

다음 모델은 독일어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>de-en</code>
    </td>
    <td>
     독일어(<code>de</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>de-fr</code>
    </td>
    <td>
     독일어(<code>de</code>)
    </td>
    <td>
     프랑스어(<code>fr</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>de-it</code>
    </td>
    <td>
     독일어(<code>de</code>)
    </td>
    <td>
     이탈리아어(<code>it</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      그리스어
{: #greek}

다음 모델은 그리스어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>el-en</code>
    </td>
    <td>
     그리스어(<code>el</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      히브리어
{: #hebrew}

다음 모델은 히브리어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>he-en</code>
    </td>
    <td>
     히브리어(<code>he</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>


##      힌디어
{: #hindi}

다음 모델은 힌디어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>hi-en</code>
    </td>
    <td>
     힌디어(<code>hi</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      헝가리어
{: #hungarian}

다음 모델은 헝가리어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>hu-en</code>
    </td>
    <td>
     헝가리어(<code>hu</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 이탈리아어
{: #italian}

다음 모델은 이탈리아어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>it-de</code>
    </td>
    <td>
     이탈리아어(<code>it</code>)
    </td>
    <td>
     독일어(<code>de</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>it-en</code>
    </td>
    <td>
     이탈리아어(<code>it</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 일본어
{: #japanese}

다음 모델은 일본어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>ja-en</code>
    </td>
    <td>
     일본어(<code>ja</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 한국어
{: #korean}

다음 모델은 한국어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>ko-en</code>
    </td>
    <td>
     한국어(<code>ko</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 노르웨이 부크몰어
{: #norwegian-bokmal}

다음 모델은 노르웨이 부크몰어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>nb-en</code>
    </td>
    <td>
     노르웨이 부크몰어(<code>nb</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      폴란드어
{: #polish}

다음 모델은 폴란드어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>pl-en</code>
    </td>
    <td>
     폴란드어(<code>pl</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 포르투갈어
{: #portuguese}

다음 모델은 포르투갈어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>pt-en</code>
    </td>
    <td>
     포르투갈어(<code>pt</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      러시아어
{: #russian}

다음 모델은 러시아어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>ru-en</code>
    </td>
    <td>
     러시아어(<code>ru</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

## 스페인어
{: #spanish}

다음 모델은 스페인어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>es-ca</code>
    </td>
    <td>
     스페인어(<code>es</code>)
    </td>
    <td>
     카탈로니아어(<code>ca</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>es-en</code>
    </td>
    <td>
     스페인어(<code>es</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
   <tr>
    <td>
     <code>es-fr</code>
    </td>
    <td>
     스페인어(<code>es</code>)
    </td>
    <td>
     프랑스어(<code>fr</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      스웨덴어
{: #swedish}

다음 모델은 스웨덴어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>sv-en</code>
    </td>
    <td>
     스웨덴어(<code>sv</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

##      터키어
{: #turkish}

다음 모델은 터키어 텍스트를 번역할 수 있습니다.

<table>
 <thead>
  <th>
   모델 ID
  </th>
  <th>
   소스
  </th>
  <th>
   대상
  </th>
  <th>
   도메인
  </th>
  <th>
   사용자 정의 가능
  </th>
  <tbody>
   <tr>
    <td>
     <code>tr-en</code>
    </td>
    <td>
     터키어(<code>tr</code>)
    </td>
    <td>
     영어(<code>en</code>)
    </td>
    <td>
     <code>general</code>
    </td>
    <td>
     <code>true</code>
    </td>
   </tr>
  </tbody>
 </thead>
</table>

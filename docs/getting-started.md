
# 개요

## 도구 소개

EventStorming2Code 도구는 소프트웨어를 통한EventStorming(이벤트스토밍) 수행과 그 결과물인
스티커기반(Sticker-based) 모델을 마이크로서비스형(Microservices Native) 코드로 자동 생성해 주는 툴이다.

> ![](.//media/image2.png)
> <p align="center"> 그림 1 EventStorming2Code 도구 화면 (예시) </p>

이벤트스토밍(Event Storming)은 Event와 BrainStorming의 합성어로서, 이벤트 기반 시스템의 설계와 개발을 빠르게할 수 있는 기법이다. 기존의 UML, BPMN 등의 이해도와 전무성을 갖추지 않더라도 현업, 업무전문가, 도메인전문가 들이 모여 화이트보드 벽면에 주요 이벤트(Event)를 중심으로 업무들간의 상호 연관성을 스티키 노트(Sticker)를 가지고 협업해 나간다.

이벤트를 중심으로 이벤트를 유발시키는 행위(사용자의 의사결정)와 해당 이벤트에 연이어 반응하는 다른 액션들을
<sup>1)</sup>모든 이해 관계자들이, <sup>2)</sup>짧은 시간 내에, <sup>3)</sup>시각적으로
모델링한다. 궁극적으로 마이크로서비스에 요구되는 자율적(Autonomous) 수행을 위한 서비스 경계(Service Boundary) 구분을 그 목적으로 한다.

EventStorming2Code 도구는 이러한 이벤트스토밍에 필요한 공간적인 제약과, 화이트보드 벽면에 부착된 스티커가 외부적 요인으로
쉽게 분리(detach)될 수 있다는 점을 보완하여 브라우저(Browser)의 캔버스 상에서 오프라인에서와 동일한 작업이 가능한
환경을 제공한다.

또한, 이벤트스토밍 결과 모델을 도구가 제공하는 순공학(Forward Engineering) 기능을 통해 단위 마이크로서비스 코드 생성이 가능하고, 
도구를 적용하는 기업이 가진 표준 프레임워크(Framework)에 맞도록 커스터마이징 가능한 템플릿 기능도 내장하고 있다. 

뿐만 아니라 마이크로서비스가 운영될 클라우드 환경에 필요한 도커(Docker)와 CI(Continuous Integration)/CD(Continuous Deployment) 배포 파이프라인(Pipeline) 등 자동화된 환경 구성(Configuration) 파일도 생성해 준다. 

--- 

### 주요 Features

  - **Provide web-based Event Storming environment**
    
      - Support 6 types of Event Sticker  
        (Event, Policy, Command, Aggregate, External System, Read Model)
    
      - Support Bounded Context and Context Mapping (Relation between
        Microservices)
    
      - Support ubiquitous Language (English word suggestion)
    
      - Support various reference type (Request & Response,
        Event-Driven)

  - **Support MSA Resources Generation**
    
      - EventStorming Model based MSA Source Code, Spring-boot (default)
    
      - Docker flie for Immutable Images
    
      - Pipeline YAML file for CI/CD DevOps
    
      - Helm Chart for easy MSA Creation

  - **Support Templates for Microservice’s Polyglot language**
    
      - Template customizing support (Any language is available)
    
      - Local and remote(Github) template add-in support

  - **Support Code Preview & Download Archive function**

  - **Support Canvas Zoom In-Out function**

---

### 도구의 목적

#### 시공간 제약없는 이벤트스토밍 환경

 온라인 서비스를 제공하는 회사들은 주로 야간에 업무 시스템 개선에 대한 서버 반영이 이루어지고 있으며, 한 팀의 개선 서비스
 반영을 위해 연관된 다른 모든 팀들이 혹시 발생할 수 있는 Side Effect 모니터링을 위해 대기하는 상황을 흔히 볼 수 있다.
   
 조직 구조가 에자일(Agile)해 지지 않으면 온라인 서비스 기업의 낮은 행복 지수를 유발하는 Pain-Point는 항상
 존재하게 된다. 허나, 우리의 경쟁사 중 앞서가는 기업은 실패에도 관대하고 고객이 원하는 Features를 탐색해
 볼 수 있는 요구사항 수집 방법과 소프트웨어 엔지니어링 방법, Loosely Coupled한 개발/운영 전략,
 DevOps와 같은 프로세스적인 아키텍처들을 겸비하고 있다.
 
 아마존과 같은 고도의 경쟁체제에 있는 글로벌 기업은 하루에도 23,000여 번의 배포를 하면서도 서비스의 안정성과 고객의
 신뢰도가 높으며, 배포(deploy) 시간도 짧게 가져가고 있다.

<table>
<thead>
<tr class="header">
<th>
<p><strong>Company</strong></p>
</th>
<th><strong>Deploy Frequency</strong></th>
<th>
<p><strong>Deploy Lead Time</strong></p>
</th>
<th>
<p><strong>Reliability</strong></p>
</th>
<th>
<p><strong>Customer Responsiveness</strong></p>
</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>
<p>Amazon</p>
</td>
<td>23,000 / day</td>
<td>
<p>Minutes</p>
</td>
<td>
<p>High</p>
</td>
<td>
<p>High</p>
</td>
</tr>
<tr class="even">
<td>
<p>Google</p>
</td>
<td>5,500 / day</td>
<td>
<p>Minutes</p>
</td>
<td>
<p>High</p>
</td>
<td>
<p>High</p>
</td>
</tr>
<tr class="odd">
<td>
<p>Netflix</p>
</td>
<td>500 / day</td>
<td>
<p>Minutes</p>
</td>
<td>
<p>High</p>
</td>
<td>
<p>High</p>
</td>
</tr>
<tr class="even">
<td>
<p>Facebook</p>
</td>
<td>1 / day</td>
<td>
<p>Hours</p>
</td>
<td>
<p>High</p>
</td>
<td>
<p>High</p>
</td>
</tr>
<tr class="odd">
<td>
<p>Twitter</p>
</td>
<td>3 / week</td>
<td>
<p>Hours</p>
</td>
<td>
<p>High</p>
</td>
<td>
<p>High</p>
</td>
</tr>
<tr class="even">
<td>
<p>Typical enterprise</p>
</td>
<td>Once every 9 months</td>
<td>
<p>Monthsor quarters</p>
</td>
<td>
<p>Low / Medium</p>
</td>
<td>
<p>Low / Medium</p>
</td>
</tr>
</tbody>
</table>
<p align="center">  표 1 출처 – 도서 The Phoenix Project </p>

  규모가 상당한 기업이지만, 하루에도 수천 번의 배포가 가능한 이유는 이러한 배포가 상호 간섭없이 이루어 지고 있는 만큼 서비스 간의 격리(Isolation)가 잘 되어 있다는데 집중해야 한다.
 
 기존의 모노리식 아키텍처는 큰 배포 단위 속에 상호 모듈들의 의존도가 높을 뿐만 아니라 단일 DB를 사용함으로 인해, 사소한
 개선 사항의 적용에도 표준 가이드라인 준수, 복잡한 결재 라인을 통한 승인 획득 등 지속적인 딜리버리에 많은 시간을
 요구하고 있는게 현실이다.

 그래서 등장한 것이 마이크로서비스 아키텍처이다. 마이크로서비스는 서비스를 함축적(Implementation Hiding)으로
 제공하자는 측면에서는SOA 사상과 유사하나, 서비스레벨 뿐만 아니라 데이터베이스 레벨까지 철저하게 분리하자는 것이 SOA와
 크게 구분되는 점이다. 기존에는 생산성을 극대화하기 위해 표준화를 목표로 하나의 정해진 언어, 잘 짜여진 개발 표준을
 준수하면서 공통 모듈을 도출하고 이를 재사용하면서 공유해 왔으나, 빠르고 기민하게 요구사항을 받아들이고
 반영하는 전체 라이프사이클 상에서 이러한 SOA사상인 표준화(Standardization)는 오히려 생산성을
 저해하는 커다란 걸림돌이 되고 있다. 즉 개발 표준을 준수하기 위해, 예를 들어 MDM(Master Data
 Management)에 필드 하나 추가하기 위해 담당자에게 요청 후, 평균 일주일을 기다려야 한다는 것이다.

 기존의 approach는 빅(big) 플래닝을 통해 빅뱅(Big Bang)의 성공을 이루려는 프로세스 적용으로 실패에 대한 리스크 또한 높았으나,
 아마존을 비롯한 글로벌 기업들은 고객이 실제 우리 제품에 대해 관심이 있는지를 빠른 시장 출시를 통해 파악한 후,
 관심과 호응도가 높을 시에 제대로 구현해 보자는 “Fail Fast”, “Fail Cheap”의 에자일한 접근법을 선호하고 있는데
 이러한 approach가 바로 마이크로서비스 전략인 것이다. 

> ![](.//media/image3.png)
> <p align="center"> 그림 2 마이크로서비스 아키텍처 </p>

 위 그림과 같은 직접 호출 기반의 마이크로서비스 아키텍처가 서비스 레벨의 자율성과 독립성, 서비스에 최적화된
 저장소(Polyglot Persistence)을 보장해 주지만, 한가지 큰 맹점이 존재하는데 그게 바로 서비스의
 동기 호출에 따른 타임 커플링(Time Coupling)은 해결해 주고 있지 못하다.

 아래 그림의 쇼핑몰 서비스간 흐름을 보면, 직접 호출 대신 Publish, Subscribe 방식으로 상호 커뮤니케이션하고 있음을
 나타내고 있다.

> ![](.//media/image4.png)
> <p align="center"> 그림 3 타임 커플링이 배제된 이벤트드리븐 아키텍처 </p>


 위 그림에서 주문팀에서 주문이 발생하였을 때, 직접 배송팀에다 ‘’배송을 준비하세요.’라고 전달하는 것은 주문팀의 입장에서는
 그다지 중요한 것이 아니다. 즉, 다시 말해 주문팀은 배송팀이 배송을 하던 말던 관심이 없다는 것이다.
 
 REST방식(직접 호출)으로 서로 통신할 경우, 호출하는 링크가 깨질 수 있고, 요청을 보냈을 때 요청자는 다음 액션을
  수행하기 위해 응답이 도착할 때까지 기다려야 하는 블로킹(Blocking) 상황이 일어난다. 그러나 타임
 커플링이 배제된 환경에서 주문팀은 발생한 사실에 대해 비동기 기반 큐(single Source Of
 Truth)에 “주문이 발생하였습니다.” 라고 신고만 함으로써 그 의무를 다하게 되고 다음 액션을 수행하면 된다. 이처럼
 “발생한 사실을 신고”하는 패턴의 아키텍처를 이벤트드리븐(Event Driven), 또는 화이트보드 패턴이라고 한다.
 
 그렇게 되면 마이크로서비스 직접 호출 패턴에선, 배송팀의 비즈니스 프로세스가 주문팀이 호출해 실행되던 방식에서, 배송팀이 직접
 이벤트에 반응하여 실행하는 방식으로 실행 주체가 바뀌게 된다. 마케팅팀 또한, 주문팀의 주문 발생으로 수행해야 할 비즈니스
 프로세스가 있다면, 단순하게 주문팀의 “주문이 발송하였습니다.” 라는 이벤트에 대해 마케팅팀도 반응하여 수행하면 된다는
 것이다.
 
 이러한 <span class="underline">이벤트 기반 마이크로서비스(Event-Driven Microservice) 구축에 앞서, 단순 스티커(Sticker) 색상으로 화이트보드 벽면에 모델링하는 기법을 이벤트스토밍(EventStorming)이라 하며, EventStorming2Code 툴은 이를 소프트웨어적으로 수행될 수 있는 환경을 제공하는 것이 그 목적</span>이다.

#### MSA 코드 자동 생성

EventStorming2Code(이하, ES2Cd) 도구를 통해 수행된 이벤트스토밍 결과는 도구의 순공학(Forward
Engineering) 코드 생성 모듈을 통해 MSA 소스코드로 자동 생성되며, 각 마이크로서비스마다 서비스에 최적화된
Language(Python, Node JS, Go 등)를 위한 사용자 정의 가능한 확장 템플릿을 지원한다.

> ![](.//media/image5.png)
> <p align="center"> 그림 4 이벤트스토밍 결과와 소스코드 구현체의 상관관계 </p>


또한, ES2Cd 도구는 워크로드 분산 엔진(Workload Distribution Engine) 기반의 클라우드 배포를 위한
Dockerfile과 CI/CD 파이프라인, 심지어 Helm Chart 스크립트까지도 자동으로 생성해 준다. 즉, ES2Cd
도구를 사용함으로써 MSA 소스코드는 물론, DevOps에 필요한 모든 메타 정보(Configuration)도 아카이브
파일에 포함되어 다운로드 된다.

#### Polyglot MSA를 위한 User-defined 템플릿

과거 모노리식 어플리케이션은 간단한 경우, 어플리케이션 서버와 DB서버 두개만 관리하면 되지만, MSA에서는 기본적으로 한 서버에
하나의 서비스만 실행되므로, 서비스 수만큼의 이기종 인스턴스 서버와 각 서비스에 최적화된 데이터베이스 적용이 가능하다. 즉 모든
서비스마다 반드시 동일한 개발 언어, 동일한 프레임워크로 구성될 필요가 없는 것이다.

예를 들어 TPS(시간당 트랜잭션)가 높고, 읽기 작업이 많은 MSA서비스는 Node, Redis 기반으로 구현하고, 트랜잭션 및
안정성이 중요한 MSA 서비스에는 Spring, RDB를 적용할 수 있는데 이를 ‘Polyglot Architecture(폴리글랏
아키텍처)’ 라고 한다.

ES2Cd 도구는 이러한 폴리글랏 아키텍처를 지원하기 위해 팀플릿 기반 MSA 코드 생성을 지원한다. ES2Cd의 커스텀 템플릿
기능을 활용하여 기본 제공 템플릿 외에 개발자가 템플릿을 추가하여 EventStorming결과가 원하는 템플릿에 맞추어 코드가
생성될 수 있도록 한다.

커스텀 템플릿의 자세한 내용은 [4.3 커스텀 템플릿 (Custom Template)](/EventStorming2Code?id=커스텀-템플릿-custom-template)</span>에서 설명한다.

---

### 도입 효과

ES2Cd 도구는 이벤트스토밍(EventStorming)이라는 DDD 구현 방법론이 가지는 장점들을 그대로 가지면서 이벤트스토밍에
필요한 충분한 공간적인 요소가 요구되지 않고, 벽면에 부착되는 다양한 스티커 노트들의 분실 및 훼손의 우려가
없다.

| **구 분**           | **오프라인 EventStorming**        | **ES2Cd**              |
| ----------------- | ----------------------------- | ---------------------- |
| Support Lifecycle | 분석, 설계                        | 분석, 설계, 개발, 운영         |
| 시공간적 제약           | 충분한 화이트보드 공간 필요               | 제약 없음                  |
| MSA 코드 구현         | MSA 구현 스킬을 보유한 개발자에 의한 수작업 개발 | 도구에서 초기 소스코드 자동생성      |
| Ployglot MSA      | 팀별 자체 구현                      | 사용자정의 확장 템플릿으로 자동생성 지원 |
| DevOps 지원         | 없음                            | CI/CD 파이프라인 자동생성       |
| 결과물 관리 용이성        | 분실 및 훼손 우려 높음                 | 결과물 버전관리 및 전자적 보관      |

<p align="center"> 표 2 이벤트스토밍 도구 도입효과 </p>

오프라인 이벤트스토밍으로 DDD기반 도메인 분석 및 설계가 가능하지만, ES2Cd는 분석에서부터 운영에 이르는 MSA 전 주기를
지원한다. 기존 MSA 스킬을 보유한 개발자가 직접 수작업으로 개발하던 소스코드는 도구에서 초기 소스코드를 자동으로 생성해
주며, 오프라인 이벤트스토밍에서는 불가능한 결과물 버전관리와 수행 결과물의 전자적 보관은 소프트웨어 기반의 이벤트스토밍
툴인 ES2Cd가 제공하는 당연한 이점이다.

---

### 실행 환경

<table>
<thead>
<tr class="header">
<th>지원 OS</th>
<th>Windows, Linux, Mac OS 지원</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>지원 Cloud</td>
<td><p>All Cloud Platform 지원</p>
<p>(AWS, GCP, MS Azure, IBM/Oracle Cloud, OpenShift)</p></td>
</tr>
<tr class="even">
<td>서비스 유형</td>
<td>On-Premise, or SaaS</td>
</tr>
<tr class="odd">
<td>필요 사양</td>
<td>Memory 512MB 이상</td>
</tr>
<tr class="even">
<td>지원 Browser</td>
<td>크로스 브라우저 지원 (IE, Edge 등 MS계열 제외)</td>
</tr>
<tr class="odd">
<td>설치 모듈</td>
<td>없음</td>
</tr>
</tbody>
</table>
<p align="center"> 표 3 EventStorming2Code 실행 환경 </p>



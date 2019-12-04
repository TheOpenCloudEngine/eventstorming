# EventStorming2Code 기반 MSA 개발

## 예제 프로젝트

예제 프로젝트는 주문 서비스와 배송 서비스 2개의 서비스를 EventStorming하여 Spring-boot로 실행되는 Java
Project를 생성한다.

## UI 소개

### 도구 레이아웃

EventStorming2Code 도구의 전체 화면 레이아웃은 다음과 같다.

> ![](.//media/image30.png)
> <p align="center"> 그림 1 도구 전체 레이아웃 </p>

| 번호 | 이름               | 기능 설명                                           |
| -- | ---------------- | ----------------------------------------------- |
| 1  | Zoom Panel       | 캔버스에 작성된 화면을 확대 및 축소 기능                         |
| 2  | Code Preview     | Code를 생성 및 확인 가능한 기능                            |
| 3  | Download Archive | Code를 생성 및 다운로드 가능한 기능                          |
| 4  | Project Name     | 프로젝트 명 입력 (Java의 경우 Package명)                   |
| 5  | Upload           | 저장된 Json형태의 EventStorming파일을 불러오는 기능            |
| 6  | Save             | Draw된 EventStorming파일을 Json파일로 저장함              |
| 7  | Sticker Palette  | EventStorming을 위한 Sticky note를 선택할 수 있는 Palette |
| 8  | Canvas           | Sticky note를 붙이는 Canvas                         |

### Event

Event는 스티커 팔레트에서 주황색 아이콘이 지칭한다.

#### Event 추가하기

스티커 팔레트에서 주황색 아이콘을 캔버스로 Drag & Drop하여 Event를 추가한다.

> ![](.//media/image31.png)
> <p align="center">그림 2 Event Drag</p>

> ![](.//media/image32.png)
> <p align="center">그림 3 Event Drop</p>

#### Event 속성 설정

추가된 Event 스티커를 더블 클릭하게 되면, 오른쪽에 아래와 같이 속성 창이 나타나며, 각 속성 설정에 대한 값은 아래와
같다.

> ![](.//media/image33.png)
> <p align="center">그림 4 Event Property Panel</p>

| 번호 | 이름                   | 기능 설명                     |
| -- | -------------------- | ------------------------- |
| 1  | Event Name           | Event Sticky note에 작성될 이름 |
| 2  | Trigger              | Event가 발생할 때 발생할 Trigger  |
| 3  | Attribute            | Event의 Attribute들 등록      |
| 4  | Associated Aggregate | Event와 연결 될 Aggregate 선택  |

주문팀의 주문 시나리오에 따라 아래와 같이 기입한다.

1.  Event Name에 “**OrderPlaced**” 라고 기입한다.

2.  Trigger는 PrePersist를 선택한다.

3.  Attribute는 Event에서 사용할 Entity를 등록한다.  
    기본적으로는 아래의 4. 에서 Aggregate가 연결된다면 해당 Aggregate의 Entity정보를 참조한다.

4.  연결될 Aggregate를 선택한다. (이후에, Aggregate를 추가한 후에 선택하여 준다.)

배송팀은 배송 시나리오에 따라 Event를 생성하여 준다.

1.  Event Name에 “**DeliveryStarted**” 라고 기입한다.

2.  Trigger는 PostUpdate를 선택한다.

3.  Attribute는 Event에서 사용할 Entity를 등록한다.  
    기본적으로는 아래의 4. 에서 Aggregate가 연결된다면 해당 Aggregate의 Entity정보를 참조한다.

4.  연결될 Aggregate를 선택한다. (이후에, Aggregate를 추가한 후에 선택하여 준다.)

### Policy

Policy는 스티커 팔레트에서 라일락색 아이콘이 지칭한다.

#### Policy 추가하기

스티커 팔레트에서 라일락색 아이콘을 캔버스로 Drag & Drop하여 Policy를 추가한다

> ![](.//media/image35.png)
> <p align="center">그림 5 Policy Drag</p>


> [](.//media/image36.png)
> <p align="center">그림 6 Policy Drop</p>

#### Policy 속성 설정

추가된 Policy 스티커를 더블 클릭하게 되면, 오른쪽에 아래와 같이 속성 창이 나타나며, 각 속성 설정에 대한 값은 아래와
같다.

> ![](.//media/image37.png)
> <p align="center">그림 7 Policy Property Panel</p>

| 번호 | 이름                   | 기능 설명                      |
| -- | -------------------- | -------------------------- |
| 1  | Policy Name          | Policy Sticky note에 작성될 이름 |
| 2  | Associated Aggregate | Policy와 연결 될 Aggregate 선택  |

해당 이벤트가 발생될 때의 업무에 따라서, 아래와 같이 기입한다.

1.  Policy Name에 “**StartDeilvery**” 라고 기입한다.

2.  연결될 Aggregate를 선택한다. (이후에, Aggregate를 추가한 후에 선택하여 준다.)

### Command

Command는 스티커 팔레트에서 파란색 아이콘이 지칭한다.

#### Command 추가하기

스티커 팔레트에서 파란색 아이콘을 캔버스로 Drag & Drop하여 Command를 추가한다

> ![](.//media/image38.png)
> <p align="center">그림 8 Command Drag</p>

> ![](.//media/image39.png)
> <p align="center">그림 9 Command Drop</p>

#### Command 속성 설정

추가된 Command 스티커를 더블 클릭하게 되면, 오른쪽에 아래와 같이 속성 창이 나타나며, 각 속성 설정에 대한 값은 아래와
같다.

> ![](.//media/image40.png)
> <p align="center">그림 10 Command Property Panel</p>

| 번호 | 이름                   | 기능 설명                       |
| -- | -------------------- | --------------------------- |
| 1  | Command Name         | Command Sticky note에 작성될 이름 |
| 2  | Restful Type         | Restful API 의 CRUD Type을 선택 |
| 3  | Associated Aggregate | Command와 연결 될 Aggregate 선택  |

해당 이벤트가 발생될 때의 업무에 따라서, 아래와 같이 기입한다.

1.  Command Name에 “**CreateOrder**” 라고 기입한다.

2.  Restful Type은 POST로 설정한다.

3.  연결될 Aggregate를 선택한다. (이후에, Aggregate를 추가한 후에 선택하여 준다.)

### 어그리게잇 (Aggregate)

Aggregate는 스티커 팔레트에서 노란색 아이콘이 지칭한다.

#### 어그리게잇 추가하기

스티커 팔레트에서 노란색 아이콘을 캔버스로 Drag & Drop하여 Aggregate를 추가한다

> ![](.//media/image41.png)
> <p align="center"> 그림 10 Aggregate Drag</p>

> ![](.//media/image42.png)
> <p align="center">그림 11 Aggregate Drop</p>

#### 어그리게잇 속성 설정

추가된 Aggregate 스티커를 더블 클릭하게 되면, 오른쪽에 아래와 같이 속성 창이 나타나며, 각 속성 설정에 대한 값은
아래와 같다.

> ![](.//media/image43.png)
> <p align="center">그림 12 Aggregate Property Panel</p>

| 번호 | 이름             | 기능 설명                                   |
| -- | -------------- | --------------------------------------- |
| 1  | Aggregate Name | Aggregate Sticky note에 작성될 이름           |
| 2  | Attributes     | Aggregate Entity (Domain Entity)를 정의한다. |

주문 서비스의 Aggregate(Domain Entity)를 정의하기 위해, 아래와 같이 기입한다.

1.  Aggregate Name에 “**Order**” 라고 기입한다.

2.  Aggregate의 Entity(Domain Entity)를 정의하여 준다.  
    해당 서비스에서는 Type은 String인 Name이라는 Entity를 추가하여 준다.

배송 서비스의 Aggregate(Domain Entity)를 정의하기 위해, 아래와 같이 기입한다.

1.  Aggregate Name에 “**Delivery**” 라고 기입한다.

2.  Aggregate의 Entity(Domain Entity)를 정의하여 준다.  
    해당 서비스에서는 Type은 String인 Address라는 Entity를 추가하여 준다.

Aggregate를 추가 하였다면 각 Event, Command, Policy들의 Associate Aggregate를 설정하여,
Aggregate를 지정하여 준다.

### Bounded Context 

Bounded Context는 스티커 팔레트에서 점선 모양의 아이콘이 지칭한다.

#### Bounded Context 추가하기

스티커 팔레트에서 점선 모양의 아이콘을 캔버스로 Drag & Drop하여 Bounded Context를 추가한다

> ![](.//media/image44.png)
> <p align="center">그림 13 Bounded Context Drag</p>


> ![](.//media/image45.png)
> <p align="center">그림 14 Bounded Context Drop</p>

#### Bounded Context 속성 설정

> ![](.//media/image46.png)
> <p align="center">그림 15 Bounded Context Property Panel</p>

| 번호 | 이름                   | 기능 설명                   |
| -- | -------------------- | ----------------------- |
| 1  | Bounded Context Name | Bounded Context에 작성될 이름 |

주문 서비스의 Bounded Context와 배송 서비스의 Bounded Context를 그린 후, 각각의 서비스에 맞게
EventStorming의 Sticky Note들을 각 Bounded Context에 Drag & Drop으로 넣어준다.

상기 작성된 4.2.2부터 4.2.6까지의 작업을 완료하면 아래와 같은 형태의 EventStorming 결과물이 나온다.

### Relation

Relation은Event 스티커에서 Policy 스티커로 연결되는 선을 지칭한다.

#### Relation 추가

Event 스티커에서 화살표 모양 아이콘을 선택, 또는 Drag 하여 연결될 Policy 스티커를 선택 또는 Drop하면
연결된다.

> ![](.//media/image47.png)
> <p align="center">그림  16 Relation 선택 또는 Drag</p>

> ![](.//media/image2.png)
> <p align="center">그림 17 Policy 선택 또는 Drop</p>

#### Relation 속성 설정

> ![](.//media/image48.png)
> <p align="center">그림 18 Relation Property Panel</p>

| 번호 | 이름           | 기능 설명                                                                                     |
| -- | ------------ | ----------------------------------------------------------------------------------------- |
| 1  | Type         | Event-Driven형식의 Pub/Sub 방식을 사용할 것인지, 또는 Request & Response 방식의 Restful API 방식을 사용할 것인지 설정 |
| 2  | Restful Type | 1번의 Type이 Request & Response 방식일 경우 CRUD중 어떠한 것을 사용할 것인지 설정                               |

주문 서비스의 OrderPlaced의 이벤트가 발생할 경우 StartDelivery가 시작되도록 연결하는데, 어떠한 방식으로
StartDelivery를 시작하게 할 것인지를 설정하여 준다.

1.  Event-Driven 방식의 Pub/Sub 방식으로 설정하여 준다.

### EventStorming 결과

위의 이벤트 스토밍이 완료되면 아래 그림과 같이 나온다.

> ![](.//media/image49.png)
> <p align="center">그림 19 EventStorming 결과</p>

### 코드 프리뷰

Code Preview를 선택하면 EventStorming 된 결과를 Code Preview를 통하여 Code로 변환된 결과를
확인 할 수 있다.

#### 코드 프리뷰 레이아웃

> ![](.//media/image50.png)
> <p align="center">그림 20 코드 프리뷰 레이아웃</p>

| 번호 | 이름              | 기능 설명                                                  |
| -- | --------------- | ------------------------------------------------------ |
| 1  | Select Template | Template 중에서 어떤 Template을 사용하여 코드 생성 및 코드 확인 할 것인지 선택. |
| 2  | Code List       | 선택된 Template에 따라서 생성된 폴더 구조와 파일들을 보여줌.                 |
| 3  | Code View       | 선택된 파일의 Code를 표시해 줌.                                   |

### 다운로드 아카이브

Download Archive를 선택하면 Template을 선택할 수 있으며, EventStroming 된 결과를 Zip파일로
다운로드 받을 수 있다.

> ![](.//media/image51.png)
> <p align="center">그림 21 Download Archive 템플릿 선택</p>

| 번호 | 이름              | 기능 설명                                                  |
| -- | --------------- | ------------------------------------------------------ |
| 1  | Select Template | Template 중에서 어떤 Template을 사용하여 코드 생성 및 다운로드 받을 것인지 선택. |

### 빌드

#### 다운로드 파일 구조 설명

  - Bounded Context 에 설정한 이름별(Order, Delivery)로 프로젝트가 생성이 되었고, 압축을 풀었을 시
    아래와 같은 구조를 가진다.

  - ![스크린샷%202019-11-28%20오전%2011](.//media/image52.png)

  - gateway 는 기본 제공되는 템플릿으로 spring-cloud-gateway 를 설정하는 방법을 나타내고있다.
    정상적으로 사용시에는 gateway/src/main/resource 의 application.yaml
    파일에서 routes 부분을 수정하여 사용하여야 한다.

  - 파일 구조는 아래와 같이 스티커별로 기본 템플릿에 의하여 생성이 되었다.  
    spring-boot 기반의 프로젝트 이며, maven 으로 리소스 관리를 한다.  
    파일 생성 위치나, 파일 안의 기본 내용을 생성시마다 변경을 하려면 다음 장의 커스텀 템플릿을 활용하면 된다.

> ![스크린샷%202019-11-28%20오후%2012](.//media/image53.png)

  - application.yaml
    
      - spring-boot 의 설정 파일이며, local 환경 변수와 Docker용 환경변수를 profile 설정으로
        분리하였다.
    
      - 이벤트 기반이기 때문에 메시지 처리를 위하여 spring-cloud-stream 라이브러리를 사용한다. 그 중에서
        브로커를 kafka 를 사용하여 설정되어있다.

  - Dockerfile
    
      - Docker image 를 생성할 때 필요한 파일이다.
    
      - Docker 로 build 시 "--spring.profiles.active=docker" 로 설정되어 있어서
        application.yaml 파일에서 설정한 프로파일을 읽게 된다.

  - cloudbuild.yaml
    
      - Google Cloud Build 에서 사용하는 pipeline 파일이다.
    
      - 기본설정으로 test-build-docker build-publish-deploy 단계가 설정되어있다.
    
      - Docker publish 단계에서는 GCR (Google Container Registry) 에 이미지를
        배포한다.
    
      - Deploy 단계에서는 GKE 에 배포를 하게 되는데 이때 주의사항은 클러스터 이름과 Zone 을 설정해 줘야한다.
        아래 3가지 항목을 사용자에 맞추어 필수적으로 변경을 해줘야 한다.
        
          - substitutions._PROJECT_NAME: 항목에서 어떤 service 와 deploy 명으로
            배포를 할지 정해지는데, 해당 부분을 변경해 줘야한다.
        
          - CLOUDSDK_COMPUTE_ZONE: 설정되어있는 Zone 은 도쿄(asia-northeast1-a)
            로 설정이 되어있다.
        
          - CLOUDSDK_CONTAINER_CLUSTER: 클러스터 이름은 standard-cluster-1 으로
            default 클러스터 이름이다.

#### 선행사항

  - maven 설치

  - local kafka 실행 – localhost:9092

#### 실행

  - 메이븐 프로젝트이기 때문에 mvn spring-boot:run 으로 실행을 한다.

  - 정상적으로 실행이 되었다면 브라우저에 localhost:8081 (port 는 프로젝트별로 다르기 때문에 설정파일 참조)
    을 적어보면 Aggregate 에 설정하였던 속성값들이 HATEOAS 수준으로 정상적으로 나오는지를 확인한다.

  - Command 에 작성하였던 get, post 등의 메서드가 정상적으로 호출되는지 확인한다.

### 클라우드 배포

이번 가이드항목은 작동하는 소스코드를 github 에 올리고 GCB 트리거를 생성하여 자동 빌드되고 배포되는 방법을 guide
한다.

####  Git 연동

  - GCB 는 git repository 를 현재까지 github, google code, bitbucket 을 지원한다. 본
    가이드는 이중에서 github 에 코드를 넣는 방법을
    설명한다.

  - [<span class="underline">https://github.com/</span>](https://github.com/)
    에서 레파지토리를 생성한다.

  - 레파지토리를 생성 하고 git 주소가 생성이 된다

  - github 에 올리려는 프로젝트에서 아래와 같은 스크립트를 실행하여 github 에 source 를 push 한다.

  - git init

  - git commit –m ‘commit message’ .

  - git push \<github 주소\>

#### GCB Trigger 생성

GCB 트리거 생성은 아래와 같은 순서대로 진행을
한다.

1. GCP 의 GCB 메뉴로 들어가서 트리거 메뉴를 클릭한다.  
> ![](.//media/image54.png)
2. 상단의 저장소 연결 버튼을 클릭한다.
> ![](.//media/image55.png)
3. 저장소 선택에서 github을 선택한다.
> ![](.//media/image56.png)
4. 깃헙 인증을 하여 진행한다.
> ![](.//media/image57.png)
5. 연결할 프로젝트를 선택하여 저장소 연결을 마무리 한다.
> ![](.//media/image58.png)
6. 상단의 트리거 생성 버튼을 클릭하여 트리거를 생성한다.
> ![](.//media/image59.png)
7. 트리거 생성 화면의 하단에 빌드 구성을 CloudBuild 로 선택한다.
>![](.//media/image60.png)
8. 트리거 만들기 버튼을 클릭하여 트리거생성을 완료한다. 오른쪽의 트리거 실행버튼으로 바로 트리거 실행을 할 수 있다. 
> ![](.//media/image61.png)

위와 같이 트리거를 생성하였으면, github 에 push 명령을 실행할 때마다, 트리거가 작동하는 것을 확인 할 수 있다.

#### 쿠버네티스 배포

##### 쿠버네티스 배포 확인

  - 트리거가 정상적으로 실행을 하였으면 기록 메뉴에서 빌드 성공/실패 여부를 확인 할 수있다.

> ![](.//media/image62.png)

  - 빌드 기록에 녹색으로 성공화면이 떠있으면 GKE 에 성공적으로 배포가 된 것이다. GKE 메뉴의 작업 부하 항목에서 현재
    동작하는 서비스를 확인 할 수
있다.

> ![](.//media/image63.png)

##### 배포 실패시 해결방법

###### 빌드 실패시 기록 항목에서 아래와 같이 빨간색으로 빌드 실패가 나타나고, 클릭시 어떤 step 에서 에러가 났는지 확인이 가능하다. 로그 다운로드 버튼을 눌러서 상세 로그를 확인하면서 해결이 가능하다.

> ![](.//media/image64.png)

> ![](.//media/image65.png)

###### deploy 단계에서 에러가 났을 경우 첫번째로 GCB 에서 GKE 로 배포를 하는 권한이 있는지 체크해 보고, 없을 때 권한 설정을 해준다.

> Cloud빌드 – 설정 메뉴에서 Kubernetes Engine 개발자가 사용설정됨 으로 상태가 보이는지 확인하고,
> 안되어있을시 사용 설정한다.

> ![](.//media/image66.png)

###### cloudBuild.yaml 파일의 option 부분에 클러스터 Zone 과 이름이 일치하는지 확인 한다.

<pre class="yaml">
yaml
options :  
    env:  
    ## location/name of GKE cluster (used by all kubectl commands)  
    - CLOUDSDK_COMPUTE_ZONE=asia-northeast1-a  
    - CLOUDSDK_CONTAINER_CLUSTER=standard-cluster-1
</pre>

## 커스텀 템플릿 (Custom Template)

### 개념

커스텀 템플릿은 기본 제공하는 템플릿 외에 원하는 템플릿을 추가하여 EventStorming결과를 원하는 템플릿에 맞추어 코드가
생성될 수 있도록 한다.

### 템플릿 추가

#### 템플릿 설명

EventStorming 된 결과를 원하는 Template으로 이용하기 위해서는, 커스텀 템플릿을 작성 하여야 한다.
Template파일은 크게 생성관련 메타데이터, 소스코드부분 두가지로 나뉘어져 있으며, 메타데이터 부분과 소스코드 부분은
“---“ 로 나누어져 있다.

템플릿 생성은 기본적으로 {{ Mustache }} 엔진을 사용하며, Mustache는 {{ }} 안의 값을 Key 값으로 해당
Value값을 가지고 오는 엔진이다.

#### 템플릿 생성

목적: 예제로 HelloWorld.py파일을 생성하여 EventStoming 한 결과들을 print함수를 이용하여 각각 작성된
이름을 표시하여 준다.

1.  HelloWorld.py 파일을 아래와 같이 생성한다.

```python
forEach: BoundedContext ----- 1

fileName: HelloWorld.py ----- 2

path: {{boundedContext}}/{{{options.packagePath}}} ----- 3

---

print("BoundedContext: {{name}}");

{{#aggregates}}

print("Aggregate: {{name}}");

{{#events}}

print("event: {{name}}");

{{/events}}

{{#commands}}

print("command: {{name}}");

{{/commands}}

{{#policies}}

print("policy: {{name}}");

{{/policies}}

{{/aggregates}}
```

각 메타데이터에 대한 값은 아래를 참고하여 작성하면 된다.

| 번호 | 이름       | 기능 설명            |
| -- | -------- | ---------------- |
| 1  | forEach  | 해당 파일의 생성 단위 객체. |
| 2  | filename | 해당 파일의 생성 파일 명   |
| 3  | path     | 해당 파일의 생성 경로     |

2.  작성된 HelloWorld.py 파일을 ./public/static/template/helloWorld 폴더 안에
    넣어준다.

3.  해당 Template을 넣어 준 뒤, 코드 프리뷰에서 템플릿 선택 부분을 확인하면 아래 그림과 같이 HelloWorld
    템플릿이 추가된 것을 확인 할 수 있다.

> ![](.//media/image67.png)
> <p align="center">그림 HelloWorld 템플릿 선택</p>

4.  각 Bounded Context 이름으로 된 폴더 안에 HelloWorld.py라는 파일이 생성 된 것을 확인 할 수
    있다.

5.  2개의 HelloWorld.py를 각각 확인 해본다.

> ![](.//media/image68.png)
> <p align="center"> 그림 Order 폴더 하위의 HelloWorld.py </p>

> ![](.//media/image69.png)
> <p align="center"> 그림 Delivery 폴더 하위의 HelloWorld.py </p>

각각의 Bounded Context에 입력된 요소들의 이름을 정상적으로 print함수 안에 입력이 된 것을 확인 할 수 있다.

6.  해당 Template으로 작업된 내용을 다운로드 받아 실행해본다.

> ![](.//media/image70.png)
> <p align="center"> 그림 Delivery 폴더 하위의 HelloWorld 실행 결과</p>

> ![](.//media/image71.png)
> <p align="center"> 그림 Order 폴더 하위의 HelloWorld.py 실행 결과</p>

7.  작성된 EventStorming을 통해, 각각의 Bounded Context 별로 HelloWorld.py가 생성되며,
    HelloWorld.py안에 각각의 BoundedContext, Aggreagte, Event, Command,
    Policy들의 이름이 출력 되는 것을 확인 할 수 있다.

#### 템플릿 작성 변수

##### 공통 변수 (BoundedContext 제외)

| 변수명                 | 변수 역할                                               |
| ------------------- | --------------------------------------------------- |
| name                | Sticky note에 작성된 이름                                 |
| nameCamelCase       | Sticky note에 작성된 이름의 CamelCase 변환 결과                |
| namePascalCase      | Sticky note에 작성된 이름의 PascalCase 변환 결과               |
| boundedContext      | 자신이 속해있는 BoundedContext 이름                          |
| options.package     | 패키지 명 (ProjectName)                                 |
| options.packagePath | 패키지 경로 ( java의 경우 src/main/java/{{ projectName }} ) |

##### BoundedContext 변수

<table>
<thead>
<tr class="header">
<th>변수명</th>
<th>변수 역할</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>name</td>
<td>BoundedContext 이름</td>
</tr>
<tr class="even">
<td>aggregates</td>
<td><p>해당 BoundedContext 안에 속해있는 Aggregate 목록</p>
<p>(하단에 작성되는 Aggregate의 변수 사용 가능)</p></td>
</tr>
<tr class="odd">
<td>portGenerated</td>
<td>생성된 포트번호 (8081부터 시작됨)</td>
</tr>
</tbody>
</table>

##### Aggregate 변수

<table>
<thead>
<tr class="header">
<th>변수명</th>
<th>변수 역할</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>aggregateRoot. fieldDescriptors</td>
<td>Aggregate의 Entity 목록</td>
</tr>
<tr class="even">
<td>aggregateRoot. keyFieldDescriptors</td>
<td>Aggregate의 Key값</td>
</tr>
<tr class="odd">
<td>events</td>
<td><p>Aggregate에 속해있는 event 목록</p>
<p>하단에 작성되는 Event의 변수 사용 가능)</p></td>
</tr>
<tr class="even">
<td>commands</td>
<td><p>Aggregate에 속해있는 command 목록</p>
<p>하단에 작성되는 Command의 변수 사용 가능)</p></td>
</tr>
<tr class="odd">
<td>policies</td>
<td><p>Aggregate에 속해있는 policy 목록</p>
<p>하단에 작성되는 Policy의 변수 사용 가능)</p></td>
</tr>
</tbody>
</table>

##### Event 변수

| 변수명              | 변수 역할                  |
| ---------------- | ---------------------- |
| aggregate        | 자신이 속해있는 Aggregate 정보  |
| fieldDescriptors | Event Entity 목록        |
| eventToPolicy    | Policy에 Event를 전달할 방식  |
| trigger          | Event 전달방식에 관한 Trigger |

##### Command 변수

| 변수명         | 변수 역할                 |
| ----------- | --------------------- |
| aggregate   | 자신이 속해있는 Aggregate 정보 |
| restfulType | RestAPI 중 어떠한 방식인지.   |

##### Policy 변수

| 변수명               | 변수 역할                  |
| ----------------- | ---------------------- |
| aggregate         | 자신이 속해있는 Aggregate 정보  |
| eventToPolicy     | Policy가 Event를 전달받는 방식 |
| relationEventInfo | 연결된 Event에 대한 정보       |

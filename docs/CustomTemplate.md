# 커스텀 템플릿 (Custom Template)

## 개념

커스텀 템플릿은 기본 제공하는 템플릿 외에 원하는 템플릿을 추가하여 EventStorming결과를 원하는 템플릿에 맞추어 코드가
생성될 수 있도록 한다.

## 템플릿 추가

### 템플릿 설명

EventStorming 된 결과를 원하는 Template으로 이용하기 위해서는, 커스텀 템플릿을 작성 하여야 한다.
Template파일은 크게 생성관련 메타데이터, 소스코드부분 두가지로 나뉘어져 있으며, 메타데이터 부분과 소스코드 부분은
“---“ 로 나누어져 있다.

템플릿 생성은 기본적으로 {{ Mustache }} 엔진을 사용하며, Mustache는 {{ }} 안의 값을 Key 값으로 해당
Value값을 가지고 오는 엔진이다.

### 템플릿 생성

목적: 예제로 HelloWorld.py파일을 생성하여 EventStoming 한 결과들을 print함수를 이용하여 각각 작성된
이름을 표시하여 준다.

1.  HelloWorld.py 파일을 아래와 같이 생성한다.


<pre class=" language-python">

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

</pre>

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

### 템플릿 작성 변수

#### 공통 변수 (BoundedContext 제외)

| 변수명                 | 변수 역할                                               |
| ------------------- | --------------------------------------------------- |
| name                | Sticky note에 작성된 이름                                 |
| nameCamelCase       | Sticky note에 작성된 이름의 CamelCase 변환 결과                |
| namePascalCase      | Sticky note에 작성된 이름의 PascalCase 변환 결과               |
| boundedContext      | 자신이 속해있는 BoundedContext 이름                          |
| options.package     | 패키지 명 (ProjectName)                                 |
| options.packagePath | 패키지 경로 ( java의 경우 src/main/java/{{ projectName }} ) |

#### BoundedContext 변수

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

#### Aggregate 변수

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

#### Event 변수

| 변수명              | 변수 역할                  |
| ---------------- | ---------------------- |
| aggregate        | 자신이 속해있는 Aggregate 정보  |
| fieldDescriptors | Event Entity 목록        |
| eventToPolicy    | Policy에 Event를 전달할 방식  |
| trigger          | Event 전달방식에 관한 Trigger |

#### Command 변수

| 변수명         | 변수 역할                 |
| ----------- | --------------------- |
| aggregate   | 자신이 속해있는 Aggregate 정보 |
| restfulType | RestAPI 중 어떠한 방식인지.   |

#### Policy 변수

| 변수명               | 변수 역할                  |
| ----------------- | ---------------------- |
| aggregate         | 자신이 속해있는 Aggregate 정보  |
| eventToPolicy     | Policy가 Event를 전달받는 방식 |
| relationEventInfo | 연결된 Event에 대한 정보       |

#### View 변수

| 변수명               | 변수 역할                  |
| ----------------- | ---------------------- |
| aggregate         | 자신이 속해있는 Aggregate 정보  |
| dataProjection    | view의 데이터 구조 방식 변수 |
| viewFieldDescriptors | 데이터 구조에 따른 테이블 정보|
| aggregateEvents   | 자신이 속해있는 Aggregate의 Events 정보 |

#### fieldDescriptors
| 변수명               | 변수 역할                  |
| ----------------- | ---------------------- |
| name         |  변수 명 |
| className    | 변수의 데이터 타입 |
| isKey | 테이블에 대한 Key 값 (Defalut: false) |


#### viewFieldDescriptors
##### CQRS
| 변수명               | 변수 역할                  |
| ----------------- | ---------------------- |
| isKey         | Key 값 (default: false)  |
| className   | 변수의 데이터 타입 |
| columnName    | 변수 명 |
| sourceEvent | 해당 변수의 Event의 정보에서 변수 |
| eventDirectValue   | sourceEvent발생시 eventDirectValue값을 columnName 값에 매핑 |
| viewColumnName   | 자신이 속해있는 Aggregate의 정보에서 변수 매핑 |
| sourceEventColumn   | 자신이 속해있는 Aggregate의 Events 정보 |

##### UI Mashup
| 변수명               | 변수 역할                  |
| ----------------- | ---------------------- |
| isKey         | Key 값 (default: false)  |
| className   | 변수의 데이터 타입 |
| columnName    | 변수 명 |
| sourceRepository   | -업데이트 예정- |
| repositoryDirectValue   | -업데이트 예정- |
| hateoas   | -업데이트 예정- |
| link   | -업데이트 예정- |



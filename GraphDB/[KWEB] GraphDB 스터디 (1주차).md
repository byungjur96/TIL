## [KWEB] GraphDB 스터디 (1주차)

### GraphDB란?

---

GraphDB란 RDF4J 프레임워크 기반의 RDF 데이터베이스입니다. RDF4J는 RDF 데이터를 저장하고, 쿼리를 날리고, 추리하는 Java 기반의 프레임워크입니다.  GraphDB *linked data cloud*를 다루는 데에 큰 장점이 있습니다. GraphDB는 W3C SPARQL Protocol을 준수하며, RDF 포멧을 지원합니다. 

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/starting_img.png)

GraphDB를 통해서 데이터셋 내의 데이터 간의 관계를 다음과 같이 표시할 수 있습니다.

<br>

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/domain-range%20graph.png)

<br>

참고 자료: [GraphDB란](<https://novemberde.github.io/database/2018/04/12/Neo4j.html>), [GraphDB Document](<http://graphdb.ontotext.com/documentation/free/about-graphdb.html>)

<br>

### RDF란?

---

**RDF**(Resource Description Framework)란 웹 상의 정보를 표현하기 위한 규격 중 하나입니다. 여기서 Resource는 URI를 갖는 모든 것들을 의미합니다. 즉, RDF란 *'URI를 갖는 데이터들을 간의 관계를 표현하는 모델'* 이라고 할 수 있습니다. RDF는 메타 데이터 간의 효율적인 교환 및 상호호환을 목적으로 합니다. 메타 데이터 교환을 위해서 XML(eXtensible Markup Language)을 사용하기도 합니다. 하지만 RDF는 XML과는 약간은 차이점이 있습니다. 아래는 RDF 구문의 한 예시입니다.

```xml
<?xml version="1.0"?>
<Description about="https://www.w3.org/test/page">
  <s:Author="https://www.w3.org/staff/Ora"/>
</Description>
```

<br>

참고 자료: [자원 기술 프레임워크](<https://ko.wikipedia.org/wiki/%EC%9E%90%EC%9B%90_%EA%B8%B0%EC%88%A0_%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC>), [RDF 개념 및 소개](<https://www.slideshare.net/barambi/rdf>)

<br>

### SPARQL이란?

---

**SPARQL**(Simple Protocol And RDF Query Language)이란 W3C에서 만든, RDF 질의어입니다. RDB에서 SQL이 하는 역할을 RDF에서는 SPARQL이 합니다. RDF는 웹 상에서 표현될 수 있는 개념들의 관계를 기술하는 역할을 한다면, SPARQL은 그 개념들 간의 질의(query) 처리가 가능할 수 있도록 해줍니다. SPARQL은 Semantic Web(Web 3.0)의 주요 기술 중 하나로 지목되고 있습니다.

<br>

참고자료: [SPARQL](<https://ko.wikipedia.org/wiki/SPARQL>), [Semantic Web SPARQL](<https://www.slideshare.net/mrumx/semantic-webweb-30-sparql>)

<br>

### GraphDB 설치 과정

---

GraphDB는 홈페이지에서 설치 파일을 다운 받아서 실행할 수 있습니다.

설치 파일을 받아서 설치하면 프로그램 아이콘이 생성되고, `localhost: 7200` 에 GUI가 구현됩니다.

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/intro%20page.png)

<br>

#### 1. repository 만들기

1) 좌측 탭에서 'setup'을 클릭한 후 'Repository'를 선택합니다.

<br>

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/repositories.png)

2) 'Create New Repository' 버튼을 클릭합니다.

<br>![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/Create%20Repository.png)

3) Repository 정보를 채워줍니다.

<br>

#### 2. SPARQL 실행하기

좌측 탭에서 'SPARQL' 탭을 클릭한 후, 화면 가운데 코드 에디터 부분에 SPARQL 문을 입력해서 실행해 줍니다.

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/sparql.png")

<br>

#### 3. dataset 불러오기

dataset을 불러오는 방법에는 2가지가 있습니다. 우선 RDF 파일을 직접 import하는 방법이 있습니다. 또 다른 방법으로는 OntoRefine 탭을 통해서 데이터를 RDF 파일로 변환하는 방법이 있습니다. TSV, CSV, *SV, Excel, JSON, XML, Google Sheet 등의 포멧을 RDF 파일로 변환해줍니다.

<br>

### GraphDB GUI Interface

---

GraphDB를 실행시켰을 때 초기 화면은 다음과 같습니다.

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/program%20page.png)

<br>

또한 `http://localhost:7200` 로 접속하면 다음과 같은 화면을 볼 수 있습니다.

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/intro%20page.png)

<br>

페이지는 크게 6개의 탭으로 구분할 수 있습니다.

<br>

#### 1) import

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/import%20rdf.png")

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/import%20tabular.png)

데이터를 GraphDB에 넣는 탭입니다. RDF 파일을 직접 넣어주거나, Tabular라고 다른 포멧의 파일을 변환해서 넣어줄 수 있습니다.

<br>

#### 2) Explore

데이터를 다양한 방법으로 보여주는 탭입니다. 하위 메뉴로는 'Graphs Overview', 'Class Hierarchy', 'Class Relationships', 'Visual Graph', 'Similarity' 5개가 있습니다. GRaphDB의 메인 기능들이 모두 포함되어 있습니다.

<br>

#### 3) SPARQL

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/sparql.png)

SPARQL query문을 입력하는 탭입니다. SPARQL query문을 입력하여 원하는 결과만을 확인해 볼 수 있습니다.

<br>

#### 4) Monitor

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/monitor.png)

새로 추가된 Qeury나 실행 중인 Query를 확인하는 탭입니다. 추가로 Memory 사용량, Threads, CPU 로드량 등을 확인할 수 있습니다.

<br>

#### 5) Setup

![](https://github.com/byungjur96/TIL/blob/master/GraphDB/img/setup.png)

Repository를 새로 만들거나, Repository의 설정을 변경할 때 이용하는 탭입니다. 그 외에도 Repository에 대한 접근 권한 등을 수정 및 추가할 수 있습니다.

<br>

### 활동계획

---

#### 목표: 메뉴와 위치를 기반으로 맛집 리스트를 구조화하기

<br>

#### <~중간 고사>

- [ ] RDF 구조 공부

- [ ] SPARQL 구문 공부
- [ ] GraphDB GUI Interface 공부

참고: [Apache Jena 문서](<http://jena.apache.org/tutorials/>)

<br>

#### <~기말 고사>

- [ ] 기존에 가지고 있던 정보 RDF 구조로 만들기
- [ ] GraphDB를 이용해서 다양한 Visual Graph 그려보기 및 SPARQL 구문 심화 공부
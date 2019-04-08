## [KWEB] GraphDB 스터디 (2주차)

#### RDF(Resource Data Framework)

---

**RDF**는 정보의 semantic, 즉 의미를 표현하는 model입니다. 그렇기 때문에 메타데이터를 표현하는 데에도 많이 사용됩니다. 또한 RDF는 주로 triples로 표현합니다. 이것은 **Entity-Attribute Value Model**(EAV Model)에 기반한 것인데, EAV Model이란 triples에 포함된 정보를 각각 주어(Entity), 술어(Attribute), 목적어(Value)에 매칭하는 것입니다. 각각의 triple은 고유의 식별자인 URI를 갖고 있으며, 이는 RDF 사이의 관계를 나타냅니다. 예를 들어, 'Fred는 Wilma와 결혼했다.'라는 문장은 Fred라는 주어, '결혼했다'는 술어, 'Wilma'은 목적어에 매칭할 수 있다는 것을 확인할 수 있습니다.



참고자료: [공식 Youtube 채널](<https://www.youtube.com/watch?v=iuQrBf2Oq-E&list=PLSEiuYkICmDm5jgVZGCSk68Xg-U38duhc>)



#### RDFS(RDF Schema)

---

RDFS는 쉽게 말해서 RDF에 schema[^1]를 더한 것입니다. 주로 triple의 관계나 자료형을 정의하는 데에 사용됩니다. 예를 들어 위에서 들었던 예시인 'Fred는 Wilma와 결혼했다.'라는 문장에서 주어와 목적어는 사람이 들어가야 한다고 정의할 수 있습니다. 또한 '사람은 포유류이다.'라는 관계를 사전에 정의했다면, 'Fred는 포유류이다.'라는 새로운 정보를 도출해낼 수 있습니다.



참고자료: [RDF Schema](<https://en.wikipedia.org/wiki/RDF_Schema>)



#### SPARQL

---

SPARQL은 RDF 그래프를 위한 Query Language입니다. SPARQL에서 사용되는 문법은 아래와 같습니다.

`PREFIX`: URI의 prefix를 정의합니다. (SQL에서 table을 호출하는 것과 비슷한 것 같음)

`SELECT`: tabular 결과를 return합니다.

```SPARQL
PREFIX: <http://bedrock/>
SELECT ?grandChild
WHERE {
  :fred :hasChild ?child .
  ?child :hasChild ?grandChild
}
```



`WHERE`: SQL의 `WHERE` 과 거의 동일합니다. 조건, 제약, 필터링을 정의합니다. 아래의 예시와 같은 방법으로 사용할 수 있습니다.

```SPARQL
WHERE {?subject ?predicate ?object}
```

위의 예시의 경우 tabular 내의 모든 정보를 return합니다.

`CONSTRUCT`: query 결과를 바탕으로 새로운 RDF Graph를 만듭니다.

`ASK`: query 결과가 존재하는 지 여부를 return합니다. 'yes' 또는 'no'를 반환합니다.

```SPARQL
PREFIX: <http://bedrock/>
ASK
WHERE {
  :fred :hasChild ?child .
  ?child :hasChild ?grandChild
}
```

`DESCRIBE`: resource에 대한 RDF 그래프의 데이터를 return합니다.

`INSERT`: 그래프에 triple을 추가합니다. 아래는 가족 관계에 대한 정보를 추가하는 query입니다.

```SPARQL
PREFIX: <http://bedrock/>
INSERT DATA {
  :fred :hasSpouse :wilma .
  :fred :hasChild :pebbles .
  :wilma :hasChild :pebbles .
  :pebbles :hasSpouse :bamm-bamm ;
           :hasChild :roxy, :chip .
}
```

하나의 triple 정보를 넣으면 뒤에 `.`을 찍어줍니다. `,` 를 이용해서 주어/술어가 동일한 query 문을 동시에 여러 개 입력해 줄 수 있습니다. `;` 를 이용하면 주어만 동일한 query 문을 여러 개 입력해 줄 수 있습니다.

`DELETE`: 그래프에서 triple을 삭제합니다.



SPARQL은 SQL과 다르게 schema[^1]가 반드시 필요하지는 않습니다.



#### Ontology

---

Ontology는 공유 가능하고, 재사용이 가능한 지식을 표현하는 방법입니다. 그 예로는 분류, 사전, 유의어 등이 포함되어 있습니다. Ontology는 domain 내의 concept과 property, concept 간의 relationship이 사용되는 제약, concept의 맴버 등을 포함합니다. Ontology를 이용하면 주어진 정보를 이해하는 데  용이하며, domain에 대한 가정을 용이하게 해줍니다. 또한 분석을 위한 데이터 통합을 도와주며, domain의 정보를 데이터에 적용할 수 있도록 도와줍니다.



#### Web Ontology Language (OWL)

---

OWL은 RDF와 RDFS에 강력한 Ontology Modeling 방법을 제공해주는 언어입니다. OWL은 Consistency Check(논리적 일관성 확인), Satisfiability Check(instance가 없는 class가 있는지), Classification(instance의 type)을 체크해줍니다. class에 대한 동치/비교를 도와주며, class 간의 연산(intersection, union, complement, disjointness)을 제공해줍니다.



참고 자료: [공식 Youtube 채널](<https://www.youtube.com/watch?v=V27-f0KzIB0&list=PLSEiuYkICmDm5jgVZGCSk68Xg-U38duhc&index=3>)



[^1]: Schema란 데이터 베이스의 구조와 제약 조건에 관한 전반적인 명세를 기술한 메타데이터의 집합입니다.




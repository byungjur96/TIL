## Primary Key

#### primary key 선언하기

---

*table_name* 이란 이름의 table에 *attribute_name* 란 속성을 `primary key` 로 선언할 경우 아래와 같은 명령어로 선언할 수 있습니다.

```sql
alter table "table_name" add primary key (attribute_name);
```



#### 여러 개의 primary key 선언하기

---

하나의 table에 여러 개의 attribute를 `primary key` 로 선언할 경우 아래와 같이 콤마를 이용해서 선언할 수 있습니다.

```sql
alter table "table_name" add primary key (attr1, attr2, ...);
```



#### table의 primary key 제거하기

----

`primary key` 를 제거할 경우 아래와 같은 명령어를 사용합니다.

```sql
alter table "table_name" drop constraint table_name_pkey;
```



##### <참고 자료>

- https://blog.naver.com/soul3532/100029064455
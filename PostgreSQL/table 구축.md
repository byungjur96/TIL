## table 구축

#### table 만들기

---

```sql
create table table_name (
	fixed_text char(5) /*고정된 길이의 문자열*/,
  variable_text varchar(8) /* 최대 8자리의 가변적인 문자열 */,
  fixed_integer int /* integer(DBMS마다 길이가 다름) */,
  fixed_num numeric(4,2) /* 실수 (정수는 4자리, 소수는 2자리) */
)
```

`create table`  이라는 명령어를 통해서 PostgreSQL 내에서 table을 만들 수 있습니다.

SQL문 중에는 다양한 data type이 있습니다.

- `char(n)`: 고정된 길이의 문자열입니다. *n* 길이만큼 받습니다.
- `varchar(n)`: 최대 n까지 길이가 가변적으로 변하는 문자열입니다.
- `int`: machine-dependent한 정수입니다.
- `numeric(p, d)`: 정수 부분에서는 p 자리수만큼, 소수점 아래에서는 d 자리수만큼의 정확도를 가지는 실수입니다.

이 외에도 사용자가 직접 data type을 정의할 수도 있습니다.



#### table 확인하기

---

```shell
\d "table_name"
```

`\d` 명령어를 통해서 table을 확인할 수 있습니다.

뒤에 table 이름없이 `\d` 만을 입력한다면 모든 table을 확인할 수 있습니다.

이를 *'List of relations'*를 나타냈다고 합니다.
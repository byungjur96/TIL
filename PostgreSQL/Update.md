## Update

#### Update의 역할

---

기존의 데이터를 수정할 경우, PostgreSQL 내에서 UPDATE 기능을 사용합니다. UPDATE의 경우 아래와 같은 명령어로 사용할 수 있습니다.

```sql
UPDATE <table_name>
SET column_name = new_value
WHERE condition;
```

위의 명령어를 이용하면 *<table_name>* 이란 테이블에서, *condition* 을 만족하는 row들에 대해서 column_name이란 attribute의 값을 new_value로 수정합니다.
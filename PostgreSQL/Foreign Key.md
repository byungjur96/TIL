## Foreign Key

#### 하나의 table에 여러 개의 foreign key를 선언하는 경우

---

이미 foreign key가 선언되어 있는 table에 `foreign key`를 선언하는 경우 아래와 같은 오류가 발생합니다.

```shell
ERROR:  there is no unique constraint matching given keys for referenced table "table_name"
```

두 개의 table 사이에서는 `foreign key` 를 한 번만 선언해야 합니다.

그렇기 때문에 여러 개의 attribute를 `foreign key` 로 선언하는 방법은 아래와 같습니다.

```sql
alter table "table_name" add foreign key (attr1, attr2);
```

여러 개의 table과의 `foreign key` 를 선언하기 위해서는 각 table마다 명령어를 입력해주면 됩니다.



#### foreign key를 삭제하는 경우

---

`foreign key` 를 삭제하는 방법은 아래와 같습니다.

```sql
alter table "table_name" drop constraint table_name_fkey;
```


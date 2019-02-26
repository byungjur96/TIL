## List

#### List가 특정 원소를 포함하는지 확인하는 방법

---

- ***in* 문법 사용하기**

  ```Python
  a = [4,2,3,1,5,6]
  if 7 in a:
      a.index(7)
  ```

  ***<원소> in <List 이름>*** 을 이용하면, 해당 원소가 List 내에 있을 땐 `True`, 없을 땐 `False` 를 return한다. List가 특정 원소를 포함하는지 확인하는 방법 중에서 속도가 가장 빠른 방법이라고 한다.



#### 띄어쓰기로 연속된 정수 입력받는 방법

---

* ***map* 함수 사용하기**

```Python
int_array = list(map(int, input().split(" ")))
```


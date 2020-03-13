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



####List 합치기

---

- `extend()` 함수를 사용하면 두 개의 리스트를 합칠 수 있다.

```python
arr1 = [1,2,3]
arr1.extend([4, 5])  # arr1 = [1, 2, 3, 4, 5]
```



#### List 안의 tuple들 정렬하기

---

```python
example_tuples = [ ('A', 3, 'a'), ('B', 1, 'b'), ('C', 2, 'c') ]

# 두 번째 원소를 기준으로 정렬하기
example_tuples.sort(key = lambda element : element[1])

# 두 번째 원소를 기준으로 정렬한 후, 두 번째 원소가 같을 때 첫 번째 원소로 추가 정렬하기
# 위의 방법으로 한다면 두 번째 원소가 같다면 먼저 나온 원소가 먼저 나온다.
example_tuples.sort(key=lambda element: [element[1], element[0]])
```



#### String 길이를 기준으로 정렬하기

---

```python
# 일반 Sorting
example = ["abc", "aa", "abcde", "dd", "abd", "abb"]
example.sort()  # ['aa', 'abb', 'abc', 'abcde', 'abd', 'dd'] (첫번째 문자의 순서부터 하나씩 정렬)

# len으로 Sorting
example = ['aa', 'abc', 'abcde', 'dd']
example.sort(key=len)  # ['aa', 'dd', 'abc', 'abcde'] (길이 순으로 정렬, 같으면 첫번째 문자부터 비교)
```


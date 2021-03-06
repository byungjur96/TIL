## 유용한 Python 함수 모음

#### strip()

---

`strip()` 함수는 문자열의 앞과 뒤의 공백을 없애주는 함수이다.

문자열 뒤에 직접 붙이거나, 문자열 변수의 뒤에 붙여서 사용할 수 있다.

비슷한 함수로 `lstrip()` 과 `rstrip()` 함수가 있다.

`lstrip()` 함수의 경우 문자열의 왼쪽, 즉 시작하는 부분에 있는 공백을 없애준다.

`rstrip()`  함수의 경우 문자열의 오른쪽, 즉 끝나는 부분에 있는 공백을 없애준다.

`strip()` 함수는 `lstrip()` 함수와 `rstrip()` 함수를 동시에 적용한 함수라고 보면 된다.

```python
string = '  example  '
print(string.strip())  # 'example'이 출력된다.
```

 추가로 `strip()` 함수는 1개의 *string argument* 를 받을 수 있다.

argument를 넣어준 경우, 문자열의 앞과 뒤에 해당 substring이 존재하는 경우 해당 substring을 제거해준다.

```python
print('abkdlfjwkelab'.strip('ab'))  # 'kdlfjwkel'이 출력된다.
```



#### format()

---

`format()` 은 변수와 string이 섞여 있을 때 매우 유용한 함수이다.

'test1234'라는 string을 출력할 때 test라는 값이 변수 `a` 에 저장되어 있는 경우, 보통 아래와 같은 방법을 이용해왔다.

```python
a = 'test'
print(a+'1234')
```

이때 변수와 string이 여러개 나올 경우 굉장히 식이 길고 복잡해진다.

이 때 `format()`  을 이용하면 한 줄로 쉽게 표현할 수 있다.

```python
a = 'test'
print('{0}1234'.format(a))
```

변수가 들어갈 자리를 {}로 감싸주고, 안에 숫자를 0부터 넣어준다.

그리고 숫자의 위치에 대입할 변수의 이름을 `format` 뒤의 괄호 안에 넣어준다.

이 함수를 이용하면 하나의 변수가 여러 번 나올 때나, 변수와 string이 여러 개 반복되어 나올 때 유용하게 사용할 수 있다.



참고자료: https://stackoverflow.com/questions/2960772/how-do-i-put-a-variable-inside-a-string



#### readline()

------

알고리즘 문제 풀이 중에 `input()` 함수를 사용했는데 시간 초과가 발생해서 찾아보다가 알게 된 함수이다.

`import sys` 를 한 후에 아래의 함수를 `input()` 대신 사용하면 시간 초과 없이 문제를 풀 수 있었다.

```
sys.stdin.readline().rstrip()
```



참고자료: https://www.acmicpc.net/board/view/10853



#### 소수점 출력

---

```
print('%.3f' % var)
```



#### String으로 함수 호출하기

---

`eval()` 함수를 사용하면 `eval()` 의 parameter와 같은 이름의 함수를 호출할 수 있다.



#### Deep Copy

---

 일반적으로 파이썬에서 `a=b` 와 같은 식으로 list를 할당해주었을 때, `b` 가 mutable한 객체라면, `a` 의 값을 변경해주면 `b` 의 값도 변경됩니다. 이런 방법을 얕은 복사( *Shallow Copy* )라고 합니다. `a` 와 `b` 는 다른 주소를 가리키지만, 그 내부의 객체(ex. `a[0]`, `b[0]`) 는 같은 주소를 바라보고 있습니다. `a=b[:]` 와 같은 할당 역시 Shallow Copy 입니다. `copy` 모듈의 `copy` 메소드 또한 얕은 복사입니다.

```python
import copy
a = [[1, 2], [3, 4]]

b1 = a
b2 = a[:]
b3 = copy.copy(a)

a[1].append(5)

print(a)  # [[1, 2], [3, 4, 5]]
print(b1)  # [[1, 2], [3, 4, 5]]
print(b2)  # [[1, 2], [3, 4, 5]]
print(b3)  # [[1, 2], [3, 4, 5]]

print(a is b1)  # True
print(a is b2)  # False
print(a is b3)  # False

print(a[0] is b1[0])  # True
print(a[0] is b2[0])  # True
print(a[0] is b3[0])  # True
```



 깊은 복사( *deep copy* )를 사용하기 위해서는 `copy` 모듈의 `deepcopy` 메소드를 사용해야 합니다.

```python
import copy
a = [[1, 2], [3, 4]]
b = copy.deepcopy(a)
a[1].append(5)

print(a)  # [[1, 2], [3, 4, 5]]
print(b)  # [[1, 2], [3, 4]]
```




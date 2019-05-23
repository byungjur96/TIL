## 유용한 Python 함수 모음

#### strip() 함수

---

`strip()` 함수는 문자열의 앞과 뒤의 공백을 없애주는 함수이다.

문자열 뒤에 직접 붙이거나, 문자열 변수의 뒤에 붙여서 사용할 수 있다.

비슷한 함수로 `lstrip()` 과 `rstrip()` 함수가 있다.

`lstrip()` 함수의 경우 문자열의 왼쪽, 즉 시작하는 부분에 있는 공백을 없애준다.

`rstrip()`  함수의 경우 문자열의 오른쪽, 즉 끝나는 부분에 있는 공백을 없애준다.

`strip()` 함수는 `lstrip()` 함수와 `rstrip()` 함수를 동시에 적용한 함수라고 보면 된다.

```python
string = '  example  '
print(string.strip()) # 'example'이 출력된다.
```

 추가로 `strip()` 함수는 1개의 *string argument* 를 받을 수 있다.

argument를 넣어준 경우, 문자열의 앞과 뒤에 해당 substring이 존재하는 경우 해당 substring을 제거해준다.
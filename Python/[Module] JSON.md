## [Module] JSON

#### Intro

---

'**JSON**'은 '**J**ava**S**cript **O**bject **N**otation'의 줄임말로, 'key와 value의 pair'로 이루어진 데이터 포멧이다. JSON에는 몇 가지 규칙이 있다.

- JSON 객체는 중괄호 블록(**{}**)으로 표기한다.
- JSON 배열은 대괄호 블록(**[]**)으로 표기한다.
- 문자열은 항상 큰 따옴표로 묶는다.



참고자료: [JSON이란? JSON 규칙](https://dololak.tistory.com/256)



#### dictionary 타입을 JSON 파일로 저장하기

---

Python에서 JSON 파일을 다루기 위해서는 내장 모듈 `json` 을 import 해줘야 한다. 만약 Python의 dictionary 자료형을 JSON으로 만들고 싶은 경우 `collections` 라는 내장 모듈에서 `OrderedDict` 을 import 해주면 된다.

```python
import json
from collections import OrderedDict

json_data = OrderedDict()
```



참고자료: [파이썬으로 JSON 파일 만들기]("http://parkjuwan.dothome.co.kr/wordpress/2017/03/22/make-json-py/")



#### `dump()` 와 `dumps()` 차이

---

`dump()` 와 `dumps()` 는 언뜻 보기에 큰 차이가 없어 보인다.

실제로도 큰 차이는 없지만, 두 method의 정의를 보면 그 목적의 차이를 알 수 있다.

##### 1) `dump()`

> Serialize obj as a JSON formatted stream to fp (a .write()-supporting file-like object<br>If ensure_ascii is False, some chunks written to fp may be unicode instances

##### 2) `dumps()`

>Serialize obj to a JSON formatted str<br>If ensure_ascii is False, the result may contain non-ASCII characters and the return value may be a unicode instance

가장 큰 차이점은 `dumps()` 는 '**JSON formatted str**'이라는 것이다. 즉, `dumps()` method는 JSON을 반환하는 것이 아니라 JSON 형태의 'string' 을 반환한다. 따라서 JSON 파일을 저장하기 위해서는 `dump()` method를 사용해야 한다. 

뿐만 아니라 `dump()` 와 `dumps()` 는 argument의 개수도 다르다. 

```python
# Optional Arguments: skipkeys, ensure_ascii, check_circular, allow_nan, cls, indent, separators, encoding, default, sort_keys
json.dump(obj, fp)
json.dumps(obj)
```

`dumps()` 의 경우 *obj*를 JSON 포멧의 string으로 만든다. 반면, `dumps()` 의 경우 *obj*를 JSON으로 만들어서 *fp*에 저장한다. 

추가로, `indent='\t'` 를 argument로 주면 JSON을 출력할 때 indentation이 이쁘게 되는 것을 확인할 수 있다.



참고자료: https://stackoverflow.com/questions/36059194/what-is-the-difference-between-json-dump-and-json-dumps-in-python, [공식 문서](https://docs.python.org/2/library/json.html), https://m.blog.naver.com/PostView.nhn?blogId=townpharm&logNo=220966378226&proxyReferer=https%3A%2F%2Fwww.google.com%2F
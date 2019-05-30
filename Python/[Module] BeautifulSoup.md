## [Module] BeautifulSoup

#### html 파일 열기

---

```python
with open('index.html') as url:
	file = BeautifulSoup(url, 'html.parser')
```

위의 코드를 실행하면 `file` 이라는 변수 안에 해당 HTML 페이지가 파싱이 된다.



#### lxml

---

`BeautifulSoup()` method는 2개의 argument를 받는다. 앞에는 `open()` 을 통해 받아온 페이지 주소가 들어가고, 뒤에는 해당 페이지의 HTML 파싱을 하는 방법이 들어간다. 위의 'html 파일 열기'에서처럼 '`html.parser`' 를 이용해서 html 파싱을 할 수도 있지만, '`lxml`' 파서로 파싱하는 것이 훨씬 속도가 빠르다고 한다. (공식 document에도 그렇게 언급되어 있다.) 따라서 '`lxml`' 파서로 파싱을 하는 것이 속도 측면에서 훨씬 유리하다. 대신 이를 위해서는 `lxml` 모듈이 필요하다. `pip install lxml` 을 통해서 설치하면 된다.



참고 자료: http://throughkim.kr/2016/04/01/beautifulsoup/, https://m.blog.naver.com/PostView.nhn?blogId=shino1025&logNo=221343885040&categoryNo=21&proxyReferer=https%3A%2F%2Fwww.google.com%2F



#### html elment 찾기

---

`find()` : 해당 조건에 맞는 하나의 태그를 가져온다. 해당 조건에 맞는 태그가 여러 개 있는 경우 가장 첫번째 태그를 가져온다.

`find_all()` : 해당 조건에 맞는 태그를 모두 가져온다.

위의 두 함수의 경우 argument가 1개일 수도 있고, 2개일 수도 있다.

##### 1) argument가 1개인 경우

```python
element.find_all('div')
```

위의 코드는 element 내의 모든 `div` 태그를 가져온다.

##### 2) argument가 2개인 경우

```python
element.find_all('div', {'속성': '속성값'})
```

위의 코드를 이용하면 조금 더 세밀하게 원하는 element를 크롤링할 수 있다.

특정 속성값을 가지고 있는 태그들만을 가져온다.

이때 주로 `class` 또는  `id` 값을 이용하여 태그를 가져온다.



참고 자료: https://twpower.github.io/84-how-to-use-beautiful-soup



#### 인접 element 찾기

---

##### 1) 형제 element 찾기

```python
element.previous_sibling
```

을 이용하면 특정 element의 형제 element 중 코드 상에서 element보다 먼저 나온 tag를 가져온다.

```python
element.next_sibling
```

을 이용하면 특정 element의 형제 element 중 코드 상에서 element 다음에 나온 tag를 가져온다.

유사하게 `next_siblings`, `previous_siblings` 함수도 있다.

##### 2) 자식 element 찾기

```python
element.children
```

을 이용하면 특정 element의 모든 자식 element를 배열로 가져온다.

##### 3) 부모 element 찾기

```python
element.parent
```

을 이용하면 특정 element의 부모 element를 가져온다.



참고 자료: https://kite.com/python/examples/1731/beautifulsoup-find-the-previous-sibling-of-a-tag, [http://www.hanbit.co.kr/media/channel/view.html?cms_code=CMS2068924870](http://www.hanbit.co.kr/media/channel/view.html?cms_code=CMS2068924870)



#### AttributeError: 'NavigableString' object has no attribute '`method`'

------

`element.children` 를 통해 특정 element의 자식 element를 크롤링한 후에 `for…in` 문을 사용하면,

> AttributeError: 'NavigableString' obejct has no attribute '`method`'

와 같은 에러가 발생한다. 여기서 `method` 에는 `name`, `get_text()`, `find()` 와 같은 BeautifulSoup에서 사용하는 모든 메소드가 들어갈 수 있다.

`NavigableString` 는 원래 태그 안에 있는 text를 의미하는 객체로, 태그 뒤에 `.string` 을 붙여줌으로서 접근할 수 있다. 하지만 html 파일을 parsing할 때, node들 사이에 space가 있으면 BeautifulSoup는 `NavigableString` 을 return한다. 즉, `Tag` 들 사이에 `NavigableString` 이 포함되어 있는 것이다.

그렇다면 `for`  문을 사용하려면 어떻게 해야 할까?

바로 `ininstance()` 함수를 사용하면 된다. 사용 예시는 아래와 같다.

```python
for child in element.children:
  if isinstance(child, NavigableString):
    continue
  elif isinstance(child, Tag):
    print(child.get_text())
```

`isinstance()` 라는 함수를 이용하여 iteration을 돌 때마다 확인을 해주면 된다.

하지만 그냥 위와 같은 함수를 사용하면 또 다른 에러가 발생한다.

> AttributeError: type object 'BeautifulSoup' has no attribute 'NavigableString'

이 에러는 NavigableString이란 `instance` 가 존재하지 않아서 발생하는 문제이다.

이 문제의 경우에는 처음에 BeautifulSoup를 `import` 해줄 때 아래와 같이 추가로 선언해주면 해결할 수 있다.

```python
from bs4 import Tag, NavigableString, BeautifulSoup
```



참고로 개인적으로는 `if`, `elif` 를 다 쓰지 않고, 필요한 element의 경우는 Tag 객체이므로 아래와 같이 Tag 객체의 경우에만 다음 스텝으로 넘어가도록 했다.

```python
from bs4 import Tag, NavigableString, BeautifulSoup

for child in element.children:
  if isinstance(child, Tag):
    print(child.get_text())
```



참고 자료: https://stackoverflow.com/questions/7591535/beautifulsoup-attributeerror-navigablestring-object-has-no-attribute-name, https://stackoverflow.com/questions/41758715/how-to-check-whether-or-not-a-iterating-variable-navigablestring-or-tag-type
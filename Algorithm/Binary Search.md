# Binary(Parametric) Search

## 1. 개념

- Parametric Search의 핵심은 ***'최적화 문제'*** 를 ***'결정 문제'*** 로 바꾸어 푸는 것!

- 조건을 만족하는 값의 '범위'는 존재하지만, 그 중 최대/최소를 구해야 하는 경우.

- 최솟값이나 최댓값을 찾을 때 유용하게 쓸 수 있는 테크닉이다.

- **기본 로직**

  1. 이진 탐색을 이용해 특정 값 설정
  2. 값이 조건을 만족하면 일시 저장
  3. 이후 범위를 좁혀가면서 최적화된 값에 도달

  ❗️ 값이 조건을 만족해도 '최적해'는 따로 존재할 수 있다는 게 핵심!

  ​		( `mid` 값이랑 `ans` 값이랑 별도로 저장하기! → `mid` 값을 제외한 범위에서 탐색이 가능해진다)



⚠️ 조건을 만족할 때 어디로 이동해야 할지 고민하기!

- [랜선 자르기]("https://www.acmicpc.net/problem/1654") : 랜선 조각의 길이를 탐색해보자!

- [공유기 설치]("https://www.acmicpc/net/problem/2110") : 공유기 간의 최소 거리를 탐색해보자!
- ❗️[숫자 구슬]("https://www.acmicpc/net/problem/2613")





참고자료: [Parametric Search]("https://romanceboong.tistory.com/entry/Parametric-Search파라메트릭-서치"), 
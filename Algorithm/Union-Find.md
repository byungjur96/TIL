# Union-Find

## 1. 개념

합집합을 찾는 대표적인 그래프 알고리즘 중에 하나로, '상호 배타적 집합(Disjoint-set)'이라고도 한다.

여러 노드가 존재할 때 두 노트가 서로 같은 그래프에 속하는지 판별하는 알고리즘이다.

*find* 와 *union* 두가지의 연산으로 이루어져 있다.

- **Find**: x가 어떤 집합에 포함되어 있는지 찾는 연산

  ```python
  def find_parent(x):
    if parent[x] == x:
      return x
    return find_parent(parent[x])
  ```

- **Union**: x와 y가 포함되어 있는 집합을 합치는 연산

  ```python
  def union(x, y):
    a = find_parent[x]
    b = find_parent[y]
    parent[max(a, b)] = min(a, b)
  ```

각 node에 대해 자기 자신을 `root` 로 하는 tree를 만든다. 두 node를 union할 때, 둘 중 `root` 가 더 작은 값으로 통일한다.

⚠️ 합집합이라고 꼭 `parent[x] == parent[y]]` 일 필요 없다! `root` 가 같은지만 비교하는 알고리즘!



## 2. 출제 유형

- [집합의 표현]("https://www.acmicpc.net/problem/1717"): Find와 Union를 섞어서 진행하기.

- [여행 가자]("https://www.acmicpc.net/problem/1976"): Union 실행 이후 Find 진행. node의 union을 **matrix**로 제공.
- [공항]("https://www.acmicpc.net/problem/10775"):  Union 진행에 규칙이 있는 문제. `root` 가 1인 합집합을 찾는 문제.
- [친구 네트워크]("https://www.acmicpc.net/problem/4195"): Union 실행 후 root node가 동일한 node들 count. 합집합의 모든 node들의 parent 값을 통일시킴.
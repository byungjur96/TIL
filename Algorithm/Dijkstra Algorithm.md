# Dijkstra Algorithm

## 1. 개념

- Single Source Shortest Path Problem: 그래프에서, ***하나의 정점에서 다른 모든 정점들의 최단 경로*** 를 구하는 알고리즘
- 모든 edge들이 양의 값을 가져야 한다.
- 기본 로직
  1. 시작 node를 제외한 모든 node과의 거리는 `INF` 에서 시작한다.
  2. 시작 node에서 edge가 가장 작은 node부터 탐색한다.
  3. B node까지의 최단 거리는 A node까지의 최단 거리 + A node에서 B node 사이의 edge의 거리와 기존의 최단 거리 중 작은 값이다.
- 우선순위 큐(Min-Heap)를 이용하여 알고리즘을 구현할 수 있다.
  1. 우선 시작 node를 제외한 모든 node까지의 거리를 INF로 초기화한 배열 `dist` 를 만든다.(시작 node까지의 거리는 0)
  2. `dist` 의 모든 node들과 node까지의 거리를 `Priority Queue` 에 추가한다.
  3. node까지의 거리가 `dist(node)` 보다 작고 방문하지 않은 node가 나올 때까지 ` pop` 한다.
  4. `pop` 한 node와 연결된 node들까지의 거리를 업데이트한다.
     1. 이전 노드까지의 거리+가중치가 `dist` 보다 작다면 `dist` 값을 갱신한다.
     2. `Priority Queue` 에 node와 갱신된 거리를 넣어준다.
  5. INF가 `pop`될 때까지 위의 2~4번을 반복한다.



참고자료: https://wondy1128.tistory.com/95
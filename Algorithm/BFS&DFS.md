# BFS  / DFS

#### 1) BFS (Breadth-First Search)

```python
def bfs(graphe, start):
    queue = [start]
    order = []
    while queue:
        val = queue[0]
        if val not in order:
            order.append(val)
        adj = []
        for i in range(n):
            if graph[val-1][i] == 1 and (i+1) not in order and (i+1) not in queue:
                adj.append(i+1)
        if not adj:
            del queue[0]
        else:
            queue += adj
    return order
```

- 두 노드 사이의 **최단 경로**를 찾고 싶을 때 사용
- **Queue**를 활용해서 구현
- 탐색 과정
  1. 탐색 시작 node를 queue에 `enqueue` 하고 방문 리스트에 추가한다.
  2. 인접 node 중 방문하지 않은 node를 모두 queue에 `enqueue` 하고 방문 리스트에 추가한다.
  3. 인접한 node가 없다면 Queue를 `dequeue` 한다.
  4. `dequeue` 된 node의 인접 노트를 차례로 방문한다.
  5. Queue가 빌 때까지 반복한다.

#### 2) DFS (Depth-First Search)

```python
def dfs(graph, start):
    stack = [start]
    order = []
    while stack:
        val = stack[-1]
        if val not in order:
            order.append(val)
        adj = []
        for i in range(n-1, -1, -1):
            if graph[val-1][i] == 1 and (i+1) not in order:
                adj.append(i+1)
        if not adj:
            del stack[-1]
        else:
            stack += adj
    return order
```

- 탐색 시에 깊은 것을 우선적으로 탐색하는 알고리즘
- 빠르게 **모든 경우의 수**를 탐색하고자 할 때 사용
- **Stack**을 활용해서 구현
- 탐색 과정
  1. 탐색 시작 node를 stack에 `push` 하고 방문 리스트에 추가한다.
  2. 인접 node가 없을 때까지 첫 번째 인접 노드를 stack에 `push` 하고 방문 리스트에 추가한다.
  3. 인접 node가 없다면 stack을 `pop` 하고 `pop` 한 node의 인접 노드를 탐색한다.
  4. stack이 빌 때까지 반복한다.



- **기본 유형** (DFS/BFS의 구현을 묻는 문제)
  - [BFS와 DFS]("https://www.acmicpc.net/problem/1260"): 가장 기본적인 BFS/DFS 문제.
  - [바이러스]("https://www.acmicpc.net/problem/2606"): 연결된 모든 node의 개수를 세는 문제.

- **주어진 지도 탐색하기**
  - ❗️[유기농 배추]("https://www.acmicpc.net/problem/1012") 
  - [연구소]("https://www.acmicpc.net/problem/14502"): 브루트 포스를 이용하여 모든 케이스에 대해 BFS 진행
# Heap

## 1. 개념

#### a) 기본 개념

- 완전 이진 트리의 일종
- Priority Queue를 위하여 만들어진 자료구조

- 최댓값이나 최솟값을 빠르게 찾아내도록 만들어짐
- 일종의 *반 정렬 상태* 를 유지한다. (큰 값이 상위 레벨에 있고 작은 값이 하위 레벨에 있다는 정도)
- 최대 힙 (Max Heap): 부모 노드의 키 값이 자식 노드의 키 값보다 크거나 같은 완전 이진 트리
  - key[parent] >= key[child]
- 최소 힙 (Min Heap): 부모 노드의 키 값이 자식 노드의 키 값보다 작거나 같은 완전 이진 트리
  - key[parent] <= key[child]



#### b) Heap의 구현

- 배열을 사용하여 저장

- 첫번째 인덱스(0)는 사용되지 않는다.

- 부모 노드 - 자식 노드의 관계

  - `left = parent*2`
  - `right = parent*2`
  - `parent = int(child/2)`

- Max-Heapify: 최대 힙의 특성을 유지하기 위한 과정

  ```python
  # A는 배열, i는 index
  def max_heapify(A, i):
    l = 2 * i  # Left
    r = 2 * i + 1  # Right
    if l <= len(A) and A[l] > A[i]:
      largest = l
    else:
      largest = i
    
    if r <= len(A) and A[r] > A[largest]:
      largest = r
    
    if largest != i:
      temp = A[i]
      A[i] = A[largest]
      A[largest] = temp
      max_heapify(A, largest)
  ```

  

- 연산

  - 삽입 (Insert)

 
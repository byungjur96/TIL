# Queue

## 1. 개념

#### a. Queue

<img src="https://github.com/byungjur96/TIL/blob/master/Algorithm/img/Queue.png" style="zoom:50%;" />

- FIFO: First In, First Out

- ENQUEUE: Queue에 데이터를 하나 추가하는 작업

  ```python
  def enqueue(Q, x):
    Q[Q.tail] = x
    if Q.tail == Q.length:
      q.tail == 1
    else:
      Q.tail = Q.tail + 1
  ```

- DEQUEUE: Queue에 데이터를 하나 삭제하는 작업

  ```python
  def dequeue(Q):
    x = Q[Q.head]
    if Q.head == Q.length:
      Q.head = 1
    else:
      Q.head = Q.head + 1
    return x
  ```

  

- Head: 다음 번에 Dequeue 될 데이터의 index

- Tail: 다음 번에 추가될 데이터의 index



#### b) Priority Queue

- 



#### c) Deque

- *"Double-ended Queue"* 의 약자
- 양쪽 끝에서 삽입/삭제가 모두 가능


# Stack

## 1. 개념

![](https://github.com/byungjur96/TIL/blob/master/Algorithm/img/Stack.png)

- LIFO: Last in, first out.

- **Push**: 데이터를 하나 추가하는 작업

  ```python
  def push(S, x):
    S.top = S.top + 1
    S[S.top] = x
  ```

- **Pop**: 데이터를 하나 삭제하는 작업

  ```python
  def stack_empty(S):
    if S.top == -1:
      return True
    else:
      return False
  
  def stack_full(S):
    if (S.top + 1) == len(S):
      return True
    else:
      return False
    
  def pop(S):
    // Underflow
    if stack_empty(S):
      raise UnderflowError()
    // Overflow
    elif stack_full(S):
      raise OverflowError()
    else:
      S.top = S.top - 1
      return S[S.top + 1]
  ```

- Top: 가장 최근에 추가된 데이터의 index



## 2. 문제 유형


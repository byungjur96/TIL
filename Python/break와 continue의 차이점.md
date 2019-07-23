## break와 continue의 차이점

#### break 문

---

전체 반복문에서 빠져 나와야 하는 경우 break문을 사용한다.



```python
num = 0
while 1:
    print(num)
    if num == 10:
        break
    num += 1
```

위와 같은 예제 코드의 결과는 다음과 같다.

```
0
1
2
3
4
5
6
7
8
9
10
```

즉, **반복문이 종료되는 시점**을 정하는 것이 break 문이라고 할 수 있다.



#### continue 문

---

continue 문은 반복되는 중에 특정한 상황에 반복문을 실행하지 않는 경우 사용한다.

```Python
num = 0
while num < 10:
    num += 1
    if num == 5:
        continue
    print(num)
```

위의 코드의 실행 결과는 다음과 같다.

```
1
2
3
4
6
7
8
9
10
```

실행 결과를 보면, num이 5인 경우 반복문이 실행되지 않고 다음 반복문이 실행된 것을 알 수 있다.

즉, 반복문 내의 코드에서 *continue* 가 실행된 경우  ***continue* 그 이후의 모든 코드를 건너뛴다**는 것을 알 수 있다.



참고 자료: [파이썬으로 배우는 알고리즘 트레이딩(4쇄)](https://wikidocs.net/3093)


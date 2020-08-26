# Dynamic Programming

문제를 소문제로 나눠서 해결하는 문제.

이전에 계산된 값을 저장하여 그 값이 필요할 때 불러온다.

브루트 포스로 해결하고자 할 때 동일한 재귀 함수를 여러 번 호출하거나, 이미 계산된 값을 반복해서 사용할 때 고민해보기

가장 핵심은 **시간 복잡도**와 **공간 복잡도**! (브루트 포스로 풀 크기인가?)

어떤 값을 memoization할 지 생각하자! 잘못하면 단순히 재귀함수를 이용한 브루트 포스가 된다!



- **기본 유형**

  - [가장 증가하는 부분 수열]("https://www.acmicpc.net/problem/11053") (LIS):  a[i]를 수열의 마지막 숫자로 가지고 있는 배열의 최대 길이
  - ❗️[평범한 배낭]("https://www.acmicpc.net/problem/12865") (냅색 문제): `D[i][j] = max(D[i] [j], D[i-1][j-w[i]] + v[i])`
  - ❗️[LCS]("https://www.acmicpc.net/problem/9251") (Longest Common Subsequence): 두 수열에 대해 가장 긴 공통 부분수열을 찾는 문제

- **각 step에서 memoization하는 값이 여러개인 경우** 

  (다음 step에서 이용하는 이전 step의 값이 조건에 따라 다른 경우)

  - [정수 삼각형]("https://www.acmicpc.net/problem/1932"): 이전 step의 특정 index만 사용.
  - [계단 오르기]("https://www.acmicpc.net/problem/2579"): 1계단 씩 2번 이상 연속 안됨. (0번, 1번 구분해서 저장)
  - [쉬운 계단 수]("https://www.acmicpc.net/problem/10844"): 2차원 DP 문제. 뭉뚱그려서 계산하지 말기!

- **Bottom-Up 방식으로 바꿔 풀기**

  (`for` 문을 이용하여 처음 값부터 다음 값을 계산해 나가는 방식)

  - [1로 만들기]("https://www.acmicpc.net/problem/1463"): 1에서부터 n까지 올라가면서 최소 횟수를 계산.
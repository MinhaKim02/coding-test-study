# Python 한 장 요약

## 1. 틀리기 쉬운 기본 문법
- `if / elif / else / for / while / def` 뒤에는 콜론 `:`
- 불리언은 `True` / `False` / `None` (대문자)
- 정수 나눗셈 `//`, 나머지 `%`, 거듭제곱 `**`, `divmod(17, 5)` → `(3, 2)`
- 변수 이름으로 `set`, `list`, `dict`, `sum`, `max`, `min` 쓰지 않기
- 들여쓰기 = 소속. 바깥 if가 거짓이면 안쪽은 통째로 건너뜀
- `"..."`와 `'...'`는 똑같음
- `A if 조건 else B` = if/else 4줄

## 2. range · len · 슬라이싱 (시작 포함, 끝 미포함)
```python
range(5)          # 0 1 2 3 4
range(1, 5)       # 1 2 3 4
range(5, 0, -1)   # 5 4 3 2 1
range(len(a))     # 인덱스 전체

s = '119552'
s[:3]    # '119'   앞에서 3글자
s[2:5]   # '955'
s[3:]    # '552'
s[-2:]   # '52'    뒤에서 2글자
s[::-1]  # 뒤집기
```
- 문제의 "i번째"(1부터) → 인덱스 `i-1`, "i번째부터 j번째까지" → `a[i-1:j]`

## 3. 리스트 · 문자열
```python
len(a)  sum(a)  max(a)  min(a)
a.append(x)  a.pop()  a[-1]  a.index(x)  a.count(x)
a.sort()                 # 원본 정렬, None 반환
sorted(a)                # 새 리스트
sorted(a, reverse=True)
sorted(a, key=lambda x: (-x[1], x[0]))   # 1순위 내림, 2순위 오름

s.split()  ' '.join(lst)  s.replace('a', 'b')
s.startswith('ab')  s.isdigit()  s.upper()  s.lower()
str(5)  int('5')  list('abc')
```
- 문자열 만들기: `answer = ''` + `answer += 글자` (`answer[i] = …` ❌)
- `lambda x: 기준` = "x를 이 값 기준으로" 정렬해 달라는 쪽지

## 4. 반복문
```python
for i in range(n):
for x in a:
for x in a[1:]:            # 두 번째부터
for i, x in enumerate(a):  # 인덱스와 값
for a, b in [[1, 2], [3, 4]]:   # 2칸짜리 나눠 받기
for x, y in zip(s1, s2):   # 두 개를 같이
```

## 5. dict · set (해시)
```python
d = {}
d[k] = d.get(k, 0) + 1     # 개수 세기 (없으면 0)
k in d                     # 키 있나? (즉시)
d.keys()  d.values()  d.items()
for k, v in d.items():
sorted(d, key=lambda k: -d[k])   # 값 큰 순으로 키 정렬

s = set(a)                 # 중복 제거, 빠른 in
len(set(a))                # 종류 수
empty = set()              # 빈 set ({}는 빈 dict)

from collections import Counter
Counter(a)                 # 자동 개수 세기, Counter끼리 빼기 가능
```
- 리스트 `in` / `remove`를 반복하면 느림 → dict/set

## 6. 스택 · 큐 · 힙
```python
stack = []; stack.append(x); stack.pop(); stack[-1]

from collections import deque
q = deque(a); q.append(x); q.popleft()

import heapq
heapq.heapify(a); heapq.heappop(a); heapq.heappush(a, y); a[0]   # 최솟값
```

## 7. 어려운 문제용 템플릿

**완전탐색**
```python
from itertools import permutations, combinations, product
permutations(a, 2)     # 순서 O
combinations(a, 2)     # 순서 X
product(a, repeat=2)   # 중복 허용
```

**DFS (재귀)** — 끝 조건 → 갈래 두 개 더하기
```python
def dfs(idx, total):
    if idx == len(nums):
        return 1 if total == target else 0
    return dfs(idx + 1, total + nums[idx]) + dfs(idx + 1, total - nums[idx])
```

**BFS (격자 최단거리)**
```python
from collections import deque
def bfs(maps):
    n, m = len(maps), len(maps[0])
    dist = [[-1] * m for _ in range(n)]
    dist[0][0] = 1
    q = deque([(0, 0)])
    while q:
        x, y = q.popleft()
        for dx, dy in [(1, 0), (-1, 0), (0, 1), (0, -1)]:
            nx, ny = x + dx, y + dy
            if 0 <= nx < n and 0 <= ny < m and maps[nx][ny] == 1 and dist[nx][ny] == -1:
                dist[nx][ny] = dist[x][y] + 1
                q.append((nx, ny))
    return dist[n-1][m-1]
```

## 8. 막혔을 때 떠올릴 질문
- 개수를 세야 하나? → dict / Counter
- 있나 없나를 반복 확인? → set
- 순서대로 처리 / 짝 맞추기? → 스택 / 큐
- 크기 순서가 중요? → 정렬
- 규칙대로 한 줄씩 처리? → 시뮬레이션 (상태 변수 하나 + for)
- 경우의 수가 적다? → 전부 다 해보기

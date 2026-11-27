# 자주 하는 실수 모음

실제로 틀렸던 것만 모았다. 새로 틀리면 여기에 추가.

## SQL

| 실수 | 바르게 | 문제 |
|---|---|---|
| `DATE(2022-10-16)` | `'2022-10-16'` (날짜는 따옴표) | 157340 |
| `BETWEEN (A, B)` | `BETWEEN A AND B` | 157340 |
| `WITH cte (SELECT …)` | `WITH cte AS (SELECT …)` | 131116 |
| `WITH cte AS { … }` | 소괄호 `( )` | 151139 |
| 서브쿼리 안의 `;` | `;`는 맨 끝에 한 번 | 151139 |
| `with a as (…), recursive b as (…)` | `WITH RECURSIVE a AS (…), b AS (…)` | 59413 |
| `ORDER BY '별칭'` | 집계식 그대로 또는 `` `별칭` `` | 132202 |
| `GROUP BY dept_id` (두 테이블에 다 있음) | `GROUP BY t1.DEPT_ID` | 284529 |
| `COUNT(DISTINCT user_id)` (두 테이블에 다 있음) | `COUNT(DISTINCT t1.USER_ID)` | 131532 |
| `cast(x, string) + 'km'` | `CONCAT(x, 'km')` | 284531 |
| 단위 붙인 문자열로 ORDER BY | 원래 숫자 식으로 정렬 | 284531 |
| `unsign(price / 10000)` | `FLOOR(PRICE / 10000)` | 131530 |
| `1 - discount_rate` (저장값 5) | `1 - discount_rate / 100` | 157339 |
| 제외용 테이블을 JOIN | `NOT IN` 서브쿼리 | 157339 |
| LEFT JOIN으로 직원 없는 부서까지 출력 | 조건 없으면 INNER JOIN | 284529 |
| 월별 그룹에 `HAVING COUNT(*) >= 5` | 기간 전체 기준은 IN 서브쿼리로 | 151139 |
| IN 서브쿼리만 쓰고 바깥 기간 조건 누락 | 바깥에도 기간 조건 | 151139 |
| LEFT JOIN 후 오른쪽 컬럼으로 SELECT/GROUP BY | 왼쪽(기준) 테이블 컬럼으로 | 59413 |
| 셀프 조인 `p.parent_id = c.id` (방향 반대) | `자식.PARENT_ID = 부모.ID` | 301647 |
| 비트 '모두 포함'을 `=`로 비교 | `(A & B) = B` | 301647 |

## Python

| 실수 | 바르게 | 문제 |
|---|---|---|
| `d.key` | `k in d` | 42576 |
| `if …` / `else` 뒤 콜론 누락 | `if …:` / `else:` | 42576 |
| `return false` | `return False` | 42577 |
| `set = {}` | `s = set()` | 1845 |
| `answer[i] = …` (빈 문자열) | `answer += …` | kt ds 코테 |
| 입력 모양 확인 없이 인덱스 접근 → IndexError | 시작 전에 `print(a, type(a), len(a))` | kt ds 코테 |

## Java

| 실수 | 바르게 | 문제 |
|---|---|---|
| 파이썬처럼 `str * n` | `str.repeat(n)` 또는 for문 | 181950 |
| `for (i = 0; …)` | `for (int i = 0; …)` | 181949 |
| `str[i]` | `str.charAt(i)` | 181949 |
| `Chracter` 오타 | `Character` | 181949 |
| 선언 안 한 변수 이름 사용 | 입력받은 변수 이름 그대로 | 181949 |

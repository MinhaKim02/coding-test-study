# SQL 한 장 요약 (MySQL)

## 1. 실행 순서 — 프 웨 그 해 셀 오 리
`FROM/JOIN → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT`

- WHERE: **행** 필터 (집계 ❌, SELECT 별칭 ❌)
- HAVING: **그룹** 필터 (COUNT, SUM, AVG 조건)
- ORDER BY: 별칭 ⭕
- 두 테이블에 같은 이름 컬럼이 있으면 SELECT·함수 안·GROUP BY 어디서든 `별칭.컬럼`
  - GROUP BY/HAVING은 FROM 컬럼을 먼저 찾아서 ambiguous 에러, ORDER BY는 별칭 우선이라 통과

## 2. 따옴표 · 출력
- 문자열은 `'작은따옴표'`, 이름(별칭)은 `` `백틱` ``
- `ORDER BY '별칭'` ❌ — 문자열 상수라 정렬 안 됨, 에러도 없음
- 출력 문자열·별칭은 문제에 적힌 그대로 (띄어쓰기까지)
- 계산 컬럼은 반드시 `AS 문제_이름` (안 붙이면 헤더가 식 그대로)
- 문자열 붙이기 `CONCAT(a, 'km')` (`+`는 숫자 덧셈) → 정렬은 원래 숫자 식으로
- 키워드·함수·컬럼명은 대소문자 무관 / 테이블명·별칭·출력 문자열은 그대로

## 3. NULL
- `IS NULL` / `IS NOT NULL` (`= NULL` ❌)
- `IFNULL(a, b)` (2개), `COALESCE(a, b, c)` (여러 개, NULL 아닌 첫 값), NVL은 Oracle 전용
- 모두 행 단위 함수 (집계 아님)
- `NULL + 숫자 = NULL` → LEFT JOIN 후 계산은 IFNULL
- `AVG(col)`은 NULL 제외 / "NULL은 X로 취급"이 있을 때만 `AVG(IFNULL(col, X))`
- `NULLIF(a, b)`: 같으면 NULL → 0 나누기 방지 `x / NULLIF(y, 0)`

## 4. 날짜
- 월 필터(어떤 타입이든 안전): `col >= '2022-01-01' AND col < '2022-02-01'`
- `'2022-10-16'`은 문자열. 날짜 컬럼과 비교할 때만 자동 변환 (형식은 YYYY-MM-DD)
- BETWEEN은 양 끝 포함: 정수·DATE는 OK / DATETIME은 끝날 오후가 빠짐 → `DATE(col) BETWEEN …`
- `YEAR() MONTH() DAY() HOUR()`, `DATE(col)` 시간 자르기, `TIME(col)`
- `DATE_FORMAT(col, '%Y-%m-%d')` → "날짜 포맷 예시와 동일"이면 무조건
  - `%Y` 4자리 `%y` 2자리 `%m` 월 `%d` 일 `%H` 시 `%i` 분 `%s` 초
- `DATEDIFF(끝, 시작) + 1` = 대여 기간 (양 끝 포함, 시간 무시)
- `TIMEDIFF`, `ADDTIME`, `DATE_ADD(d, INTERVAL 3 DAY)`, `TIME_TO_SEC` / `SEC_TO_TIME` (시간 평균)
- 하루가 기간 안에 있나: `'2022-10-16' BETWEEN START_DATE AND END_DATE`
- **기간 겹침: `START_DATE <= 조회끝 AND END_DATE >= 조회시작`**
  - "내 시작은 상대 끝보다 앞, 내 끝은 상대 시작보다 뒤"
  - 안 겹치는 건 완전히 앞이거나 완전히 뒤, 그 두 경우를 뒤집은 것

## 5. 숫자
- `ROUND(x)` = `ROUND(x, 0)` / "첫째 자리**에서** 반올림" → 0, "첫째 자리**까지**" → 1, 음수는 정수 쪽
- 구간 묶기 `FLOOR(x / 10000) * 10000` 또는 `TRUNCATE(x, -4)` (CAST는 반올림이라 ❌)
- `FLOOR` 내림 / `CEIL` 올림 / `TRUNCATE(x, n)` 버림
- MySQL 정수 CAST는 `SIGNED` / `UNSIGNED`, 문자는 `CHAR`
- 퍼센트가 INTEGER(5)면 `× (1 - rate/100)` — 예시 표의 `%`는 표시일 뿐, 컬럼 타입 표가 진실
- 매출 = `SUM(가격 * 수량)` (곱셈을 SUM 안에)

## 6. CASE WHEN
```sql
CASE WHEN 조건1 THEN 값1
     WHEN 조건2 THEN 값2
     ELSE 값3 END AS 별칭
```
- 위에서부터 검사 → 큰 조건부터, END 빼먹지 않기, ELSE 없으면 NULL
- 그룹 안에 하나라도 조건 만족? `MAX(CASE WHEN 조건 THEN 1 ELSE 0 END) = 1`
- 원하는 순서 정렬 `ORDER BY FIELD(col, 'Dog', 'Cat')`

## 7. JOIN
- INNER JOIN: 양쪽 다 있는 것만 → 기본
- LEFT JOIN: 왼쪽 전부 + 짝 없으면 NULL → "없는 것도 출력/0건도 출력"일 때만
  - LEFT JOIN 결과의 SELECT/GROUP BY 기준은 왼쪽 테이블에서
  - 없는 것을 0으로 세기: `COUNT(오른쪽.컬럼)` (`COUNT(*)`는 1이 됨)
- A에만 있고 B에는 없는 것: `LEFT JOIN … WHERE B.키 IS NULL` 또는 `NOT IN (서브쿼리)`
  - NOT IN 서브쿼리에 NULL이 하나라도 있으면 0건
- 두 테이블 날짜 비교: `WHERE A.날짜 > B.날짜`
- **외래 키** "A의 X는 B의 X의 외래 키" = A→B 참조. B(부모, 기본 키)는 1줄 / A(자식)는 여러 줄 (1:N)
- 1:N 합계는 **N쪽 먼저 GROUP BY → JOIN** (안 하면 1쪽 값이 복제돼 뻥튀기)
- 제외용 테이블(대여 기록 등)은 JOIN ❌, NOT IN 서브쿼리 ⭕
- 한 키에 여러 줄인 테이블(할인 정책 7/30/90일)은 JOIN 조건에 구분 컬럼까지
- GROUP BY로 중복을 덮고 있다 = JOIN이 잘못된 신호
- `FROM a, b`는 조인이 아니라 전부 곱하기(카테시안 곱)

## 8. 서브쿼리 · CTE
```sql
WITH cte AS ( SELECT … ),      -- 소괄호! AS 필수! 여러 개는 쉼표
     cte2 AS ( … )
SELECT … FROM cte JOIN cte2 ON …;
```
- CTE = 이름 붙인 임시 테이블. 단계가 필요할 때만 (행 필터만이면 WHERE)
- FROM 서브쿼리는 별칭 필수 `FROM ( … ) r`
- 서브쿼리 안에 `;` ❌
- "Only SELECT statements are allowed" = 문법 오타(AS, 괄호, 쉼표)부터 의심
- "기간 전체 N회 이상인 것의 월별 집계" = `IN (… GROUP BY … HAVING COUNT(*) >= N)` + 바깥에도 기간 조건
- 그룹별 최댓값 행
  - `WHERE (그룹, 값) IN (SELECT 그룹, MAX(값) … GROUP BY 그룹)`
  - `MAX() OVER (PARTITION BY 그룹)` → CTE → `WHERE 값 = 최댓값`
- 윈도우 함수 결과로 거르려면 CTE로 감싸고 바깥 WHERE에서

## 9. 자주 쓰는 함수
- `COUNT(DISTINCT id)` = "회원 수" (구매 건수 아님)
- `LIKE '%abc%'`, `REGEXP 'A|B|C'`, AND/OR 섞으면 괄호
- `ROW_NUMBER` 1-2-3 / `RANK` 1-1-3 / `DENSE_RANK` 1-1-2
- 0~23 숫자 테이블
```sql
WITH RECURSIVE h AS (SELECT 0 AS n UNION ALL SELECT n + 1 FROM h WHERE n < 23)
```
  - `RECURSIVE`는 WITH 바로 뒤 한 번만. 시작 부분 UNION ALL 반복 부분 + 멈춤 조건
- 비트 코드: `값 & 코드 != 0` 이면 보유 (스킬 코드 = 2의 거듭제곱)

## 10. 제출 전 30초 체크
- [ ] 중복 행 없나? (GROUP BY / DISTINCT)
- [ ] 출력 컬럼 순서·별칭·문자열이 문제와 똑같나?
- [ ] ORDER BY 방향(ASC/DESC), 2차 정렬까지 했나?
- [ ] 날짜 포맷, 반올림 자릿수 맞나?
- [ ] 같은 이름 컬럼에 별칭 붙였나?
- [ ] 조건이 애매하면 예시 출력으로 역산해봤나?

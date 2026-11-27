# coding-test-study

프로그래머스로 코딩테스트를 공부하면서 **틀린 이유와 정리한 풀이**를 모아두는 저장소입니다.
각 문제는 `핵심 아이디어 → 내 풀이 → 실수 / 배운 점 → 정리한 풀이` 순서로 기록합니다.

- 메인 언어: **Python**, **MySQL**
- 시작: 2026.11.19

## 진행 현황

| 언어 | 문제 수 |
|---|---|
| SQL | 32 |
| Python | 8 |
| Java | 5 |

## 노트

- [SQL 한 장 요약](notes/sql-cheatsheet.md)
- [Python 한 장 요약 + 템플릿](notes/python-cheatsheet.md)
- [자주 하는 실수 모음](notes/mistakes.md)

## 폴더 구조

```
sql/      select · group-by · join · string-date
python/   hash · stack-queue · sort · greedy · brute-force · dfs-bfs
java/     basics · Python으로 푼 문제를 Java로 다시 풀기
notes/    요약 · 실수 모음
```

## SQL

| 유형 | 문제 | 레벨 | 정리 |
|---|---|---|---|
| SELECT | [평균 일일 대여 요금 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/151136) | Lv.1 | [보기](sql/select/151136_평균-일일-대여-요금-구하기.md) |
| GROUP BY | [고양이와 개는 몇 마리 있을까](https://school.programmers.co.kr/learn/courses/30/lessons/59040) | Lv.2 | [보기](sql/group-by/59040_고양이와-개는-몇-마리-있을까.md) |
| GROUP BY | [동명 동물 수 찾기](https://school.programmers.co.kr/learn/courses/30/lessons/59041) | Lv.2 | [보기](sql/group-by/59041_동명-동물-수-찾기.md) |
| GROUP BY | [입양 시각 구하기(1)](https://school.programmers.co.kr/learn/courses/30/lessons/59412) | Lv.2 | [보기](sql/group-by/59412_입양-시각-구하기1.md) |
| GROUP BY | [가격대 별 상품 개수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/131530) | Lv.2 | [보기](sql/group-by/131530_가격대-별-상품-개수-구하기.md) |
| GROUP BY | [진료과별 총 예약 횟수 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/132202) | Lv.2 | [보기](sql/group-by/132202_진료과별-총-예약-횟수-출력하기.md) |
| GROUP BY | [성분으로 구분한 아이스크림 총 주문량](https://school.programmers.co.kr/learn/courses/30/lessons/133026) | Lv.2 | [보기](sql/group-by/133026_성분으로-구분한-아이스크림-총-주문량.md) |
| GROUP BY | [자동차 종류 별 특정 옵션이 포함된 자동차 수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/151137) | Lv.2 | [보기](sql/group-by/151137_자동차-종류-별-특정-옵션이-포함된-자동차-수-구하기.md) |
| GROUP BY | [물고기 종류 별 잡은 수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/293257) | Lv.2 | [보기](sql/group-by/293257_물고기-종류-별-잡은-수-구하기.md) |
| GROUP BY | [월별 잡은 물고기 수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/293260) | Lv.2 | [보기](sql/group-by/293260_월별-잡은-물고기-수-구하기.md) |
| GROUP BY | [즐겨찾기가 가장 많은 식당 정보 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/131123) | Lv.3 | [보기](sql/group-by/131123_즐겨찾기가-가장-많은-식당-정보-출력하기.md) |
| GROUP BY | [카테고리 별 도서 판매량 집계하기](https://school.programmers.co.kr/learn/courses/30/lessons/144855) | Lv.3 | [보기](sql/group-by/144855_카테고리-별-도서-판매량-집계하기.md) |
| GROUP BY | [저자 별 카테고리 별 매출액 집계하기](https://school.programmers.co.kr/learn/courses/30/lessons/144856) | Lv.3 | [보기](sql/group-by/144856_저자-별-카테고리-별-매출액-집계하기.md) |
| GROUP BY | [대여 횟수가 많은 자동차들의 월별 대여 횟수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/151139) | Lv.3 | [보기](sql/group-by/151139_대여-횟수가-많은-자동차들의-월별-대여-횟수-구하기.md) |
| GROUP BY | [자동차 대여 기록에서 대여중 / 대여 가능 여부 구분하기](https://school.programmers.co.kr/learn/courses/30/lessons/157340) | Lv.3 | [보기](sql/group-by/157340_자동차-대여-기록에서-대여중-대여-가능-여부-구분하기.md) |
| GROUP BY | [조건에 맞는 사용자와 총 거래금액 조회하기](https://school.programmers.co.kr/learn/courses/30/lessons/164668) | Lv.3 | [보기](sql/group-by/164668_조건에-맞는-사용자와-총-거래금액-조회하기.md) |
| GROUP BY | [노선별 평균 역 사이 거리 조회하기](https://school.programmers.co.kr/learn/courses/30/lessons/284531) | Lv.3 | [보기](sql/group-by/284531_노선별-평균-역-사이-거리-조회하기.md) |
| GROUP BY | [특정 조건을 만족하는 물고기별 수와 최대 길이 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/298519) | Lv.3 | [보기](sql/group-by/298519_특정-조건을-만족하는-물고기별-수와-최대-길이-구하기.md) |
| GROUP BY | [입양 시각 구하기(2)](https://school.programmers.co.kr/learn/courses/30/lessons/59413) | Lv.4 | [보기](sql/group-by/59413_입양-시각-구하기2.md) |
| GROUP BY | [식품분류별 가장 비싼 식품의 정보 조회하기](https://school.programmers.co.kr/learn/courses/30/lessons/131116) | Lv.4 | [보기](sql/group-by/131116_식품분류별-가장-비싼-식품의-정보-조회하기.md) |
| GROUP BY | [년, 월, 성별 별 상품 구매 회원 수 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/131532) | Lv.4 | [보기](sql/group-by/131532_년-월-성별-별-상품-구매-회원-수-구하기.md) |
| GROUP BY | [연간 평가점수에 해당하는 평가 등급 및 성과금 조회하기](https://school.programmers.co.kr/learn/courses/30/lessons/284528) | Lv.4 | [보기](sql/group-by/284528_연간-평가점수에-해당하는-평가-등급-및-성과금-조회하기.md) |
| GROUP BY | [부서별 평균 연봉 조회하기](https://school.programmers.co.kr/learn/courses/30/lessons/284529) | Lv.4 | [보기](sql/group-by/284529_부서별-평균-연봉-조회하기.md) |
| JOIN | [상품 별 오프라인 매출 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/131533) | Lv.2 | [보기](sql/join/131533_상품-별-오프라인-매출-구하기.md) |
| JOIN | [없어진 기록 찾기](https://school.programmers.co.kr/learn/courses/30/lessons/59042) | Lv.3 | [보기](sql/join/59042_없어진-기록-찾기.md) |
| JOIN | [있었는데요 없었습니다](https://school.programmers.co.kr/learn/courses/30/lessons/59043) | Lv.3 | [보기](sql/join/59043_있었는데요-없었습니다.md) |
| JOIN | [오랜 기간 보호한 동물(1)](https://school.programmers.co.kr/learn/courses/30/lessons/59044) | Lv.3 | [보기](sql/join/59044_오랜-기간-보호한-동물1.md) |
| JOIN | [조건에 맞는 사원 정보 조회하기](https://school.programmers.co.kr/learn/courses/30/lessons/284527) | Lv.3 | [보기](sql/join/284527_조건에-맞는-사원-정보-조회하기.md) |
| JOIN | [주문량이 많은 아이스크림들 조회하기](https://school.programmers.co.kr/learn/courses/30/lessons/133027) | Lv.4 | [보기](sql/join/133027_주문량이-많은-아이스크림들-조회하기.md) |
| JOIN | [특정 기간동안 대여 가능한 자동차들의 대여비용 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/157339) | Lv.4 | [보기](sql/join/157339_특정-기간동안-대여-가능한-자동차들의-대여비용-구하기.md) |
| String, Date | [특정 옵션이 포함된 자동차 리스트 구하기](https://school.programmers.co.kr/learn/courses/30/lessons/157343) | Lv.1 | [보기](sql/string-date/157343_특정-옵션이-포함된-자동차-리스트-구하기.md) |
| String, Date | [조건에 맞는 도서와 저자 리스트 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/144854) | Lv.2 | [보기](sql/string-date/144854_조건에-맞는-도서와-저자-리스트-출력하기.md) |

## Python

| 유형 | 문제 | 레벨 | 정리 |
|---|---|---|---|
| 해시 | [폰켓몬](https://school.programmers.co.kr/learn/courses/30/lessons/1845) | Lv.1 | [보기](python/hash/1845_폰켓몬.md) |
| 해시 | [완주하지 못한 선수](https://school.programmers.co.kr/learn/courses/30/lessons/42576) | Lv.1 | [보기](python/hash/42576_완주하지-못한-선수.md) |
| 해시 | [전화번호 목록](https://school.programmers.co.kr/learn/courses/30/lessons/42577) | Lv.2 | [보기](python/hash/42577_전화번호-목록.md) |
| 해시 | [의상](https://school.programmers.co.kr/learn/courses/30/lessons/42578) | Lv.2 | [보기](python/hash/42578_의상.md) |
| 해시 | [베스트앨범](https://school.programmers.co.kr/learn/courses/30/lessons/42579) | Lv.3 | [보기](python/hash/42579_베스트앨범.md) |
| 스택/큐 | [같은 숫자는 싫어](https://school.programmers.co.kr/learn/courses/30/lessons/12906) | Lv.1 | [보기](python/stack-queue/12906_같은-숫자는-싫어.md) |
| 정렬 | [K번째수](https://school.programmers.co.kr/learn/courses/30/lessons/42748) | Lv.1 | [보기](python/sort/42748_K번째수.md) |
| DFS/BFS | [타겟 넘버](https://school.programmers.co.kr/learn/courses/30/lessons/43165) | Lv.2 | [보기](python/dfs-bfs/43165_타겟-넘버.md) |

## Java

| 유형 | 문제 | 레벨 | 정리 |
|---|---|---|---|
| 기초 | [홀짝 구분하기](https://school.programmers.co.kr/learn/courses/30/lessons/181944) | Lv.0 | [보기](java/basics/181944_홀짝-구분하기.md) |
| 기초 | [문자열 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/181952) | Lv.0 | [보기](java/basics/181952_문자열-출력하기.md) |
| 기초 | [a와 b 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/181951) | Lv.0 | [보기](java/basics/181951_a와-b-출력하기.md) |
| 기초 | [문자열 반복해서 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/181950) | Lv.0 | [보기](java/basics/181950_문자열-반복해서-출력하기.md) |
| 기초 | [대소문자 바꿔서 출력하기](https://school.programmers.co.kr/learn/courses/30/lessons/181949) | Lv.0 | [보기](java/basics/181949_대소문자-바꿔서-출력하기.md) |

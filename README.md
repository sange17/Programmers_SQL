# Programmers_SQL
프로그래머스 스쿨 SQL Kit 풀이
* 틀린 부분 지적해주시면 감사하겠습니다.

# 1. SELECT

## 🧩3월에 태어난 여성 회원 목록 출력하기

```
SELECT MEMBER_ID
       , MEMBER_NAME
       , GENDER
       , TO_CHAR(DATE_OF_BIRTH, 'YYYY-MM-DD') DATE_OF_BIRTH
  FROM MEMBER_PROFILE 
 WHERE 1=1
   AND TO_CHAR(DATE_OF_BIRTH, 'MM') = '03'
   AND GENDER = 'W'
   AND TLNO IS NOT NULL
 ORDER BY MEMBER_ID ASC
 ;
```
### 주의할 점
* DATE 형식의 데이터를 LIKE로 조회할 때 주의해야한다.
  *  LIKE를 사용하겠다면 TO_CHAR로 형변환후 LIKE로 조회가능하다.
  *  그렇지 않다면 TO_CHAR(DATE, 'MM')으로 해당 월만 조회가능하다.
* NULL 비교 시 NOT IN을 사용하면 조회되지 않는다.
  * NULL 비교는 NOT IN 대신 IS NOT NULL을 사용하여 조회한다.


## 🧩과일로 만든 아이스크림 고르기

```
SELECT A.FLAVOR
  FROM FIRST_HALF A
       , ICECREAM_INFO B
 WHERE A.FLAVOR = B.FLAVOR
   AND A.TOTAL_ORDER > 3000
   AND B.INGREDIENT_TYPE = 'fruit_based'
 ORDER BY TOTAL_ORDER DESC
 ;
```
### 주의할 점
* ORDER BY 정렬 기본 조건은 ASC(오름차순)이다.
  *  문제는 높은 수부터 첫 행부터 출력하는 것이므로 DESC(내림차순)으로 조회가능하다.

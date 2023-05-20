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


## 🧩조건에 부합하는 중고거래 댓글 조회하기
```
SELECT A.TITLE
       , A.BOARD_ID
       , B.REPLY_ID
       , B.WRITER_ID
       , B.CONTENTS
       , TO_CHAR(B.CREATED_DATE, 'YYYY-MM-DD')
  FROM USED_GOODS_BOARD A
       , USED_GOODS_REPLY B
 WHERE A.BOARD_ID = B.BOARD_ID
   AND TO_CHAR(A.CREATED_DATE, 'YYYY') = '2022'
   AND TO_CHAR(A.CREATED_DATE, 'MM') = '10'
 ORDER BY B.CREATED_DATE ASC
          , A.TITLE ASC
;
```
### 주의할 점
* TO_CHAR를 활용하여 문제의 결과에 맞는 DATE 형식의 데이터를 출력해야한다.


## 🧩강원도에 위치한 생산공장 목록 출력하기
```
SELECT FACTORY_ID
       , FACTORY_NAME
       , ADDRESS
  FROM FOOD_FACTORY
 WHERE ADDRESS LIKE '강원도%'
 ORDER BY FACTORY_ID ASC
;
```
### 주의할 점
* LIKE 문을 활용하여 원하는 주소의 결과만 출력해야한다.
  * '(단어)%' : 단어로 시작되는 데이터 출력
  * '%(단어)%' : 단어가 포함되는 데이터 출력
  * '%(단어)' : 단어로 끝나는 데이터 출력


## 🧩흉부외과 또는 일반외과 의사 목록 출력하기
```
SELECT DR_NAME
       , DR_ID
       , MCDP_CD
       , TO_CHAR(HIRE_YMD, 'YYYY-MM-DD')
  FROM DOCTOR
 WHERE MCDP_CD IN ('CS', 'GS')
 ORDER BY HIRE_YMD DESC
          , DR_NAME ASC
;
```
### 주의할 점
* TO_CHAR를 활용하여 문제의 결과에 맞는 DATE 형식의 데이터를 출력해야한다.

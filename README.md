# Programmers_SQL
프로그래머스 스쿨 SQL Kit 풀이

# 3월에 태어난 여성 회원 목록 출력하기
* 틀린 부분 지적해주시면 감사하겠습니다.
---

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
* DATE 포맷의 데이터를 LIKE '%%'를 사용하면 조회되지 않는다.
  *  굳이 LIKE를 사용하겠다면 TO_CHAR로 형변환후 LIKE로 조회가능하다.
  *  그렇지 않다면 TO_CHAR(DATE, 'MM')으로 해당 월만 조회가능하다.
* NULL 비교 시 NOT IN을 사용하면 조회되지 않는다.
  * NULL 비교는 NOT IN 대신 IS NOT NULL을 사용하여 조회한다.

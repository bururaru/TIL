### Oracle 설치

설치 이후 cmd 에서 (최초접속)

` sqlplus / as sysdba`

` alter user hr identified by hr account unlock;`

`conn hr/hr`

(이후 부터는)`sqlplus hr/hr` 로 접속 가능



## SQL (Structure Query Language)

### CRUD

C - insert

R - select

U - update

D - delete



### SELECT 구문

```sql
SELECT 특정 column 이름 | *(전체 column) | 표현식 | DISTINCT | AS column 별칭
FROM 테이블 이름 ;
```

- 별칭은 반드시 문자로 시작해야 함
- 특수문자(공백) 들어갈 경우에는 단어 전체를 `" "` 로 감싸주어야 함 .예시:  `"급여(원)" ` 

전체 column 가져오는 경우에는 예시

```sql
SELECT *
FROM EMPLOYEE;
```

#### DISTINCT 키워드

중복된 값을 제거하고 한번만 출력할 때 사용하는 키워드

```sql
SELECT DISTINCT JOB_ID
FROM EMPLOYEE;
```

#### 더미 column

` SELECT AS '셀의 내용' AS 열이름` : ' '로 감싸면 셀에 해당 내용이 들어간 더미 column 생성됨



#### WHERE

조건을 넣어 표시할 행을 제한 할 수 있음

```sql
SELECT *
FROM EMPLOYEE
WHERE DEPT_ID = 90
```



#### 연결 연산자 ||

하나의 셀 안에 내용이 연결되어 들어감

```sql
SELECT ID || '의 월급은' || NAME || SALARY || '입니다'
```

#### 비교 연산자

- `BETWEEN AND` : 값이 지정한 범위(경계 포함)에 포함되면 TRUE 반환 : `BETWEEN 하한값 AND 상한값` 
- `LIKE / NOT LIKE` : 비교하려는 값이 특정한 pattern 을 만족하면 TRUE 반환 : wild card 사용
  - % : 0개 이상의 문자열 ( 예 : 김씨 성 가진 이름 -> `NAME LIKE '김%'` )
  - _ : 문자 1개 ( 예: 9로 시작하는 3자리 수 -> `NUM LIKE '9__'`)
  - `ESCAPE ''` ' ' 안에 넣는 특수문자(%, _)를 특수문자로 입력 받음 -> [ ] 에 넣는것과 동일
- `IS NULL / IS NOT NULL`
- `IN` : OR와 비슷 : ( 예 : `DEPT IN ('20', '90')`) : 안에 들어가는 변수의 타입을 맞춰야 함








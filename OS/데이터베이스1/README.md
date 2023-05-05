## 데이터베이스의 종류와 특징

#### 데이터 베이스를 사용하는 이유

#### 성능(좋게하는 법)

#### 특징

#### 데이터 베이스 언어

#### DDL, DML, DCL

#### RDMS 설명

#### NoSQL 설명

#### CAP 이론

#### 저장 방식에 따른 NoSQL 분류

#### RDBMS와 NoSQL의 차이에 대해 설명해주세요.

#### 그렇다면 RDBMS와 NoSQL은 어느 경우에 적합한가요?

---

## 키

#### 키란
- 키는 데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 튜플들을 서로 구분할 수 있는 "기준이 되는 속성(Attribute)"을 말한다.

#### 키종류

#### Candidate Key (후보키)
- 후보키는 릴레이션을 구성하는 속성들 중에서 튜플을 유일하게 식별하기 위해 사용하는 속성들의 부분집합, 즉 기본키로 사용할 수 있는 속성들을 말한다.
- 하나의 릴레이션내에서는 중복된 튜플들이 있을 수 없으므로 모든 릴레이션에는 반드시 하나 이상의 후보키가 존재한다.
- 후보키는 릴레이션에 있는 모든 튜플에 대해서 유일성과 최소성을 만족시켜야 한다.
- 위 테이블에서 학생번호, 휴대폰 등이 후보키이다. 이름은 동명이인이 있으므로 유일성을 만족하지 않는다. 나이도 마찬가지로 같은 나이가 있으므로 유일성을 만족하지 않는다.
- NULL 값 불가능
- 유일성 : 하나의 키 값으로 하나의 튜플만을 유일하게 식별할 수 있다.
- 최소성 : 모든 레코드들을 유일하게 식별하는데 꼭 필요한 속성만으로 구성되어 있어야 한다.

#### Primary Key (기본키)
- 기본키는 후보키 중에서 선택한 주 키(Main Key)이다.
- 한 릴레이션에서 특정 튜플을 유일하게 구별할 수 있는 속성이다.
- NULL 값 불가능
- 기본키로 정의된 속성에는 동일한 값이 중복되어 저장될 수 없다.
- 위 테이블에서 기본키는 후보키 중에서 고르면 된다. 학생번호나 휴대폰 중 고르면 된다.

#### Alternate Key (대체키)
- 후보키가 둘 이상일때 기본키를 제외한 나머지 후보키들을 말한다. 보조키라고도 한다.
- 만약 학생번호를 기본키로 골랐다면 휴대폰이 대체키가 된다.
-NULL 값 불가능

#### Super Key (슈퍼키)
- 슈퍼키는 한 릴레이션 내에 있는 속성들의 집합으로 구성된 키로서 릴레이션을 구성하는 모든 튜플들 중 슈퍼키로 구성된 속성의 집합과 동일한 값을 나타나지 않는다.
- 슈퍼키는 릴레이션을 구성하는 모든 튜플에 대해 유일성은 만족시키지만, 최소성은 만족시키지 못한다.
- 만약 (학생번호, 이름) 을 묶어서 키로 사용하면, 동명이인이 있어도 튜플을 구분할 수 있다. 예를 들어 2번 제니는 3번 제니와 다른 제니임을 알 수 있다. 따라서 유일성은 만족시키지만, 학생번호 하나만으로도 구분할 수 있다는 최소성을 만족시키지 못한다. 따라서 (학생번호,
이름), (학생번호, 나이), (휴대폰, 나이) 등등은 슈퍼키가 될 수 있다.
- 여러개의 속성으로 슈퍼키를 만들 때 반드시 1개 이상의 후보키가 포함되어야 한다.
- NULL 값 가능.

#### Foreign Key (외래키)
- 관계를 맺고 있는 릴레이션 R1, R2 에서 릴레이션 R1이 참조하고 있는 릴레이션 R2의 기본키와 같은 R1 릴레이션의 속성을 외래키라고 한다.
- 외래키는 참조되는 릴레이션의 기본키와 대응되어 릴레이션 간에 참조 관계를 표현하는데 중요한 도구이다.
- NULL 값 가능.

---

## 인덱스

#### Index에 대해 설명

#### 장/단점

#### DBMS는 Index를 어떻게 관리하고 있나요? (Index 자료구조에 대해 설명해주세요)

#### B+Tree 인덱스 자료구조

#### 해시 테이블

#### 왜 index 를 생성하는데 b-tree 를 사용하는가?

#### Primary Index vs Secondary Index

#### Composite Index

#### Index 의 성능과 고려해야할 사항

---

## 정규화

#### 정규화는 어떤 배경에서 생겨났는가?

#### 이상 현상의 종류에 대해 설명해주세요.

#### 삽입 이상

#### 갱신 이상

#### 삭제 이상

#### 정규화에 대해 설명해주세요.

#### ‘나쁜' 릴레이션은 어떻게 파악하는가?

#### 함수적 종속성이란 무엇인가?

#### 정규화 종류

#### 제 1 정규형 만족 조건

#### 제 2 정규형 만족 조건

#### 제 3 정규형 만족 조건

#### BCNF 정규형 만족 조건

#### 정규화 장/단점

#### 역정규화를 하는 이유에 대해 아는대로 설명해주세요.

---

## DB Query & JOIN

#### JOIN의 필요성
- 관계형 데이터베이스의 구조적 특징으로 정규화를 수행하면 의미 있는 데이터의 집합으로 테이블이 구성되고 각 테이블끼리는 관계(Relationship)을 갖게 된다.
- 이와 같은 특징으로 관계형 데이터베이스는 저장 공간의 효율성과 확장성이 향상되게 된다.
- 다른 한편으로는 서로 관계있는 데이터가 여러 테이블로 나뉘어 저장되므로 각 테이블에 저장된 데이터를 효과적으로 검색하기 위해 조인이 필요하다.

#### JOIN의 종류 각각 설명
내부조인(INNER JOIN)
- 여러 애플리케이션에서 사용되는 가장 흔한 결합 방식이며 기본 조인 형식으로 간주된다.
-내부 조인은 조인 구문에 기반한 2개의 테이블(A, B)의 컬럼 값을 결합함으로써 새로운 결과 테이블을 생성한다.
- 명시적 조인 표현(explicit)과 암시적 조인 표현(implicit) 2개의 다른 조인식 구문이 있다.

명시적 조인 표현
- 테이블에 조인 하는 것을 지정하기 위해 J이IN 키워드를 사용하며 그리고 나서 다음의 예제와 같이 0N 키워드를 조인에 대한 구문을 지정하는데 사용한다.
- SELECT * FROM employee INNER JOIN department ON employee.DepartmentID = department.DepartmentID;

암시적 조인 표현
- SELECT 구문의 FROM 절에서 그것들을 분리하는 콤마를 사용해서 단순히 조인을 위한 여러 테이블을 나열하기만 한다.
- SELECT * FROM employee, department WHERE employee.DepartmentID = department.DepartmentID;

교차 조인(CROSS JOIN)
- 조인되는 두 테이블에서 곱집합을 반환한다.
- 즉, 두 번째 테이블로부터 각 행과 첫 번째 테이블에서 각 행이 한번씩 결합된 열을 만들 것이다.
- 예를 들어 m행을 가진 테이블과 n행을 가진 테이블이 교차 조인되면 m*n 개의 행을 생성한다.
- 명시적 조인 표현
- SELECT * FROM employee CROSS JOIN department;
- 암시적 조인 표현
- SELECT * FROM employee, department;

외부 조인(OUTER JOIN)
- 조인 대상 테이블에서 특정 테이블의 데이터가 모두 필요한 상황에서 외부 조인을 활용하여 효과적으로 결과 집합을 생성할 수 있다.

왼쪽 외부 조인(LEFT OUTER JOIN)
- 우측 테이블에 조인할 컬럼의 값이 없는 경우 사용한다.
즉, 좌측 테이블의 모든 데이터를 포함하는 결과 집합을 생성한다.
- SELECT * FROM employee LEFT OUTER JOIN department ON employee.DepartmentID = department.DepartmentID;

오른쪽 외부 조인(RIGHT OUTER JOIN)
- 좌측 테이블에 조인할 컬럼의 값이 없는 경우 사용한다.
즉, 우측 테이블의 모든 데이터를 포함하는 결과 집합을 생성한다.
- SELECT * FROM employee RIGHT OUTER JOIN department ON employee.DepartmentID = department.DepartmentID

완전 외부 조인(FULL OUTER JOIN)
- 양쪽 테이블 모두 OUTER JOIN이 필요할 때 사용한다.
- SELECT * FROM employee FULL OUTER JOIN department ON employee.DepartmentID = department.DepartmentID;

#### JOIN에서 ON과 WHERE의 차이를 설명해주세요.
- ON : JOIN 을 하기 전 필터링을 한다. (=ON 조건으로 필터링이 된 레코들간 J이N이 이뤄진다)
- WHERE : JOIN 을 한 후 필터링을 한다. (JOIN을 한 결과에서 WHERE 조건절로 필터링이 이뤄진다)

#### 주의사항
- NOSQL 문장의 의미를 제대로 파악 : SQL을 어떻게 작성하느냐에 따라 성능이 크게 좌우된다. 어떤 질의를 수행할 것인지를 명확하게 정의한 후, 비효율을 제거하여 최적의 SQL을 작성해야 한다.
- 명확한 조인 조건 제공 : 조인 조건을 명확하게 제공하지 않을 경우, 의도치 않게 CROSS JOIN이 수행될 수 있다.

#### 쿼리 수행 순서 설명(select -> from -> where -> group by -> having -> column -> order by -> limit)
1. FROM : SELECT 문에 필요한 테이블 선택
2. WHERE : WHERE 조건절을 이용하여 행(row) 데이터 필터링
3. GROUP BY : GROUP BY 절을 이용하여 특정 컬럼의 그룹화를 수행
4. HAVING : HAVING 절을 이용하여 그룹화된 결과에 대한 조건 필터링
5. SELECT : SELECT 절에서 사용할 컬럼 선택
6. ORDER BY : ORDER BY 절을 이용하여 결과 데이터 정렬
7. LIMIT : LMIT 절을 이용하여 출력할 데이터의 개수 제한

#### HAVING과 WHERE의 차이를 설명해주세요.
- Having절은 WHERE절과 비슷하지만 그룹 전체 즉, 그룹을 나타내는 결과 집합의 행에만 적용된다.
- 반면 WHERE절은 개별 행에 적용이 된다.

- having은 SQL select문이 집계 값이 지정된 조건을 충족하는 행만 반환하도록 지정하는 SQL절이다.
- where은 단일 테이블에서 데이터를 가져 오거나 여러 테이블과 결합하여 조건을 지정하는데 사용되는 SQL절이다.

- having절은 그룹을 필터링하는 데 사용된다.
- where절을 행을 필터링 하는데 사용된다.

- 집계 함수는 having 절과 함께 사용할 수 있다.
- where절을 having절에 포함된 하위 쿼리에 있지않으면 집계함수와 함께 사용할 수 없다.
-(집계함수란, COUNT, MIN, MAX, SUM, AVG등등이 있다.)

- having 절은 Group By 절 뒤에 사용한다.
- Where 절은 Group By 절 앞에 사용한다.

#### group by의 역할에 대해 설명해주세요.
- 데이터를 '그룹화'하는 데 사용되는 절이다. 이 절은 특정 열(Colum)의 값을 기준으로 행(Row)을 그룹화하거나 각 그룹에 대한 집계 함수로 계산한다.

#### DELETE, TRUNCATE, DROP의 차이를 설명해주세요.
- 모두 삭제하는 명령어이지만 중요한 차이점이 있다.
- DELETE 명령어는 데이터는 지워지지만 테이블 용량은 줄어 들지 않는다. 원하는 데이터만 지울 수 있다. 삭제 후 잘못 삭제한 것을 되돌릴 수 있다.
- TRUNCATE 명령어는 용량이 줄어 들고, 인덱스 등도 모두 삭제 된다. 테이블은 삭제하지는 않고 데이터만 삭제한다. 한꺼번에 다 지워야 한다. 삭제 후 절대 되돌릴 수 없다.
- DROP 명령어는 데이블 전체를 삭제, 공간, 객체를 삭제한다. 삭제 후 절대 되돌릴 수 없다.

#### INSERT/ UPDATE/ DELETE/ LIKE/ null
- INSERT INTO [테이블명] ([칼럼1, [칼럼2], [칼럼3 ..)
VALUES ([값1], [값2], [값3] ..)
- 모든 칼럼을 입력할 경우 입력할 칼럼 생략 가능
- VALUES 여러개 써서 동시에 여러 행 INSERT 가능


- UPDATE [테이블명]
SET [컬럼1] = [값1]
   ,[컬럼2] = [값2]
WHERE [조건]

- DELETE
FROM [테이블명]
WHERE [조건]

LIKE
- A로 시작하는 문자를 찾기
- SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE'A%'
- A를 포함하는 문자 찾기
- SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE'%A%'
- A로 시작하는 두글자 문자 찾기
- SELECT 컬럼명 FROM 테이블 WHERE 컬럼명 LIKE'A_'

null
- NULL 값은 아직 정의되지 않은 값
- NULL 은 0 또는 공백이 아니다. (0은 숫자이고, 공백은 하나의 문자이다.)
- 테이블을 생성할 때 NOT NULL 또는 PRIMARY KEY로 정의되지 않은 모든 데이터 유형은 NULL 값을 포함할 수 있다.
- NULL 값을 포함하는 연산의 경우 결과 값도 NULL 값이다.

#### 평균, 합계, 최고, 최저
평균
- SELECT AVG(컬럼)
FROM 테이블명
WHERE 조건

합계
- SELECT SUM(컬럼)
FROM 테이블명
WHERE 조건

최고
- SELECT MAX(컬럼)
FROM 테이블명
WHERE 조건

최저
- SELECT MIN(컬럼)
FROM 테이블명
WHERE 조건

#### 테이블 정보
- SHOW 테이블명
- SHOW 테이블명 FROM DB명

#### 중복 제거
SELECT DISTINCT 컬럼, 컬럼
FROM 테이블명
WHERE 조건

#### IN, NOT IN 설명
SELECT *
FROM 테이블명
WHERE 컬럼 IN (A','B)
- 'A'와 'B' 가 포함되는 데이터만 추출

SELECT *
FROM 테이블명
WHERE 컬럼 NOT IN (A','B)
- 'A'와 'B'가 포함되는 않는 데이터만 추출

#### 숫자에서 문자로
- TO_CHAR : 숫자나 날짜를 문자열로 변환

#### 문자에서 숫자로
- TO_NUMBER : 문자를 숫자로 변환

#### 문자에서 날짜로
- TO DATE : 문자를 날짜로 변환

#### 날짜 관련 함수
SYSDATE
-시스템에 저장된 현재 날짜를 반환하는 함수
SELECT SYSDATE FROM DUAL;

ROUND
- 숫자를 반올림하는 함수. 포멧 모델을 지정하면 숫자 이외에 날짜에 대해서도 반올림을 할 수 있다.
SELECT HIRE_DATE, ROUND (HIRE DATE, 'MONTH) FROM HR.EMPLOYEES;

TRUNC
- 숫자를 잘라내는 것뿐만 아니라 날짜를 잘라낼 수 있다. ROUND 함수와 마찬가지로 포맷 형식을 주어 다양한 기준으로 날짜를 잘라낼 수 있다.
- 특정 날짜(DATE)를 달(MONTH)을 기준으로 버림한 날짜를 구하기 위해서는 다음과 같이 표현한다.
SELECT HIRE DATE, TRUNCHIRE_DATE, 'MONTH)
FROM HREMPLOYEES;

MONTHS_BETWEEN
- 날짜와 날짜 사이의 개월 수를 구하는 함수.
- 다음은 각 직원들의 근무한 개월 수를 구하는 예제
SELECT LAST_NAME, SYSDATE, HIRE_ DATE, MONTHS_BETWEEN (SYSDATE, HIREDATE)
FROM HR

ADD_MONTHS
- 특정 개월 수를 더한 날짜를 구하는 함수
- 다음은 입사날짜에서 6개월을 추가하는 예제
SELECT LAST_-NAME, HIRE DATE, ADD_MONTHS(HIRE_DATE, 6)
FROM HR.EMPLOYEE;

NEXT_DAY
- 해당 날짜를 기준으로 최초로 도래하는 요일에 해당되는 날짜를 반환하는 함수.
- 오늘을 기준으로 최초로 도래하는 수요일은 언제인지 알아보는 예제.
SELECT SYSDATE, NEXT_DAY(SYSDATE, 수요일)
FROM DUAL;

LASTDAY
- 해당 날짜가 속한 달의 마지막 날짜를 반환하는 함수
- 입사한 달의 마지막 날을 구하는 예제
SELECT HIRE DATE, LAST_DAY(HIREDATE)
FROM HR.EMPLOYEES;

#### 분석 함수
CUMEDIST
- 값 집합에서 값의 누적 분포 계산

DENSERANK
- 순위 값에 간격이없는 순서가 지정된 행 집합에서 행의 순위를 계산

FIRST_VALUE
- 지정된 창 프레임에서 첫 번째 행의 값을 가져옵니다.

LAG
- 셀프조인을 사용하지 않고 현재 행 앞에 오는 지정된 물리적 오프셋에서 행에 대한 액세스를 제공합니다.

LAST_VALUE
- 지정된 창 프레임에서 마지막 행의 값을 가져옵니다.

LEAD
- 셀프조인을 사용하지 않고 현재 행을 따르는 주어진 물리적 오프셋에서 행에 대한 액세스를 제공

NTH_VALUE
- 값 집합에서 N 번째 값을 가져옵니다.

NTILE
- 순서가 지정된 행 집합을 여러 버킷으로 나누고 각 행에 적절한 버킷 번호를 할당

PERCENTRANK
- 일련의 값에서 값의 순위를 계산

RANK
- 일련의 값에서 값의 순위를 계산

ROW_NUMBER
- 파티션에서 또는 전체 결과에서 1부터 시작하여 고유 한 순차 정수를 각 행에 할당

#### 누적 함수
ROLLUP 함수
- 항목별 합계와 전체합계 구하기
- 여러 항목으로 GROUP BY를 한다음, 중간 그룹별로 통계값이 필요한 경우에 유용한 함수이다. 주로 분류해야되는 값이 많은 데이터를 다를 때, 통계를 내야할 때 사용한다.

Grouping 함수
- ROLLUP 한 중간통계값에서 NULL 로 나오기 때문에, 실제로 NULL인 값과 혼동될 우려가 있다. 이럴 때 어떤 값이 롤업으로 그루핑 된 것인지를 알 수 있게 하는 것이 Grouping 함수이다.

SUM() OVER() 함수
- 그룹별 누적 합계 구하기
- 예를 들어 A, B, C, D 라는 기준으로 Group By를 한 상태에서, A와 B까지만 Grouping한 값의 Sum(컬럼1) 의 값이 필요한 경우가 있다. 이럴 때 ROLLUP을 쓰기는 아주 번거롭고, 대신 SUM() OVER() 함수를 사용하면 된다.

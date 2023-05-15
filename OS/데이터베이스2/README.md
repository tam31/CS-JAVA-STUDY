## 트랜잭션

#### 트랜잭션이란 무엇인지 설명해주세요
- 트랜잭션이란, 데이터베이스의 상태를 변화시키기 해서 수행하는 작업의 단위를 뜻한다.
- 상태를 변화시킨다는 것은 SELECT, UPDATE, INSERT, DELETE 와 같은 SQL을 이용해서 데이터베이스에 접근 하는 것을 의미한다.
- 트랜잭션 하나는 SQL 하나가 될 수도 있고 SQL 여러개가 될 수도 있다.
- 예를 들어 상품을 구매하는 API가 있다고 하자. 구매를 하기 위한 과정이 1. 유효한 사용자인지 확인, 2. 상품 정보 가져오기, 3. 상품 구매하기 라고 한다면 SQL은 SELECT, SELECT, INSERT가 된다. 이 3개의 SQL이 하나의 트랜잭션이 되는 것이다.


#### 트랜잭션과 Lock
- 멀티 트랙잭션 환경에서 데이터베이스의 일관성과 무결성을 유지하려면 트랜잭션의 순차적 진행을 보장할 수 있는 장치가 필요하다.
- 예를들어 한명이 도서관의 좌석을 예약하는 중에 다른 한명이 같은 좌석을 예약할 수 없게 하여 한명만 좌석을 배정받을 수 있게한다.
Shared lock (공유 잠금)
- 한 트랜잭션이 리소스를 읽고 있을 때에는 다른 트랙잭션도 읽을 수는 있지만 변경은 못하게 막는 것.
- 어떤 트랜잭션에서 데이터를 읽고자 할 때 shared lock은 허용이 되지만 exclusive lock은 불가능하다.
- 어떤 자원에 shared lock이 동시에 여러개 적용될 수 있다.
- 어떤 자원에 shared lock이 하나라도 걸려있으면 exclusive lock을 걸 수 없다.
Exclusive lock (배타적 잠금)
- 한 트랜잭션이 데이터를 변경 중일 때는 완료될 때까지 다른 트랜잭션이 읽거나 변경하지 못하게 막는 것.
- exclusive lock에 걸리면 shared lock을 걸 수 없다.
- exclusive lock에 걸린 테이블, row 에 대해 다른 트랜잭션이 exclusive lock을 걸 수 없다.


#### 트랜잭션의 특성(ACID)에 대해 설명해주세요
원자성 (Atomicity)
- 트랜잭션이 DB에 모두 반영되거나, 전혀 반영되지 않거나를 뜻한다.
- All or Nothing을 생각하면 된다.
일관성 (Consistency)
- 트랜잭션 작업 처리의 결과가 항상 일관되어야 한다를 뜻한다.
- 트랜잭션이 진행되는 동안에 데이터베이스가 변경 되더라도 업데이트된 데이터베이스로 트랜잭션이 진행되는것이 아니라, 처음에 트랜잭션을 진행 하기 위해 참조한 데이터베이스로 진행된다. 이렇게 함으로써 각 사용자는 일관성 있는 데이터를 볼 수 있는 것이다.
독립성 (Isolation)
- 둘 이상의 트랜잭션이 동시에 실행되고 있을 경우 하나의 트랜잭션은 다른 트랜잭션에 끼어들 수 없다.
- 즉, 각각의 트랜잭션은 독립적이라 서로 간섭이 불가능하다.
- 하나의 트랜잭션이 완료될때까지, 다른 트랜잭션이 해당 트랜잭션의 결과를 참조할 수 없다.
지속성 (Durability)
- 트랜잭션이 성공적으로 완료되면 영구적으로 결과에 반영되어야 함을 뜻한다.
- 보통 commit 이 된다면 지속성은 만족할 수 있다.


#### 트랜잭션의 상태
![image](https://github.com/gurrl9823/CS-JAVA-STUDY/assets/21374239/654475a4-69b0-4f26-81e7-11ab231febd2)
트랜잭션은 논리적으로 5가지의 상태에 있을 수 있다.
Active
- 트랜잭션이 현재 실행 중인 상태
Failed
- 트랜잭이 실행되다 오류가 발생해서 중단된 상태
Aborted
- 브랜잭션이 비정상 종료되어 Rollback 이 수행된 상태
Partially Committed
- 트랜잭션의 연산이 마지막까지 실행되고 Commit이 되기 직전 상태
Committed
- 트랜잭션이 성공적으로 종료되어 Commit 연산을 실행한 후의 상태


#### 트랜잭션을 사용할 때 주의할 점
- 트랜잭션은 꼭 필요한 최소의 코드에만 적용하는 것이 좋다.
- 여러 개의 트랜잭션으로 쪼개서 트랜잭션의 범위를 최소화하라는 의미다.
- 일반적으로 데이터베이스 커넥션의 개수가 제한적이다. 그런데 각 단위 프로그램이 커넥션을 소유하는 시간이 길어지면 사용 가능한 여유 커넥션의 개수는 줄어들게 된다. 이러면 각 단위 프로그램에서 커넥션을 가져가기 위해 기다려야 하는 상황이 발생할 수도 있기 때문이다.


---

## 트랜잭션의 격리 수준

#### Isolation level 필요성

- Read uncommitted: 트랜잭션이 완료되지 않은 다른 트랜잭션의 변경 내용을 읽을 수 있습니다. 이로 인해 dirty read(더러운 읽기)라는 문제가 발생할 수 있습니다.
- Read committed: 트랜잭션에서 커밋된 변경 내용만 읽을 수 있습니다. 하지만 커밋되지 않은 변경 내용은 다른 트랜잭션에서 읽을 수 있으므로 non-repeatable read(반복 불가능한 읽기) 문제가 발생할 수 있습니다.
- Repeatable read: 트랜잭션이 읽은 데이터는 다른 트랜잭션에서 변경할 수 없습니다. 하지만 새로운 데이터가 추가되거나 삭제되는 경우 phantom read(유령 읽기) 문제가 발생할 수 있습니다.
- Serializable: 트랜잭션 간에 직렬화(serialization)를 보장하여 동시성 문제를 완전히 해결할 수 있지만, 성능이 저하될 수 있습니다.

#### 격리 수준의 종류와 발생하는 동시성 제어 문제

- Read uncommitted: 트랜잭션이 완료되지 않은 다른 트랜잭션의 변경 내용을 읽을 수 있습니다. 이로 인해 dirty read(더러운 읽기)라는 문제가 발생할 수 있습니다.
  Read committed: 트랜잭션에서 커밋된 변경 내용만 읽을 수 있습니다. 하지만 커밋되지 않은 변경 내용은 다른 트랜잭션에서 읽을 수 있으므로 non-repeatable read(반복 불가능한 읽기) 문제가 발생할 수 있습니다.
- Repeatable read: 트랜잭션이 읽은 데이터는 다른 트랜잭션에서 변경할 수 없습니다. 하지만 새로운 데이터가 추가되거나 삭제되는 경우 phantom read(유령 읽기) 문제가 발생할 수 있습니다.
- Serializable: 트랜잭션 간에 직렬화(serialization)를 보장하여 동시성 문제를 완전히 해결할 수 있지만, 성능이 저하될 수 있습니다.

#### 동시성 제어로 발생하는 문제

- Dirty read(더러운 읽기): 트랜잭션이 완료되지 않은 다른 트랜잭션의 변경 내용을 읽는 문제입니다. 이 경우, 다른 트랜잭션이 롤백되면 읽은 내용이 무효화되는 문제가 발생할 수 있습니다.
- Non-repeatable read(반복 불가능한 읽기): 트랜잭션에서 읽은 데이터가 다른 트랜잭션에서 변경되어 읽은 내용과 다른 경우입니다.
- Phantom read(유령 읽기): 트랜잭션에서 읽은 데이터와 다른 트랜잭션에서 새로 추가된 데이터가 있을 때 발생하는 문제입니다.

#### 낮은 단계 Isolation Level을 활용할 때 발생하는 현상들

- Dirty read(더러운 읽기): Read uncommitted 레벨에서 발생할 수 있는 문제입니다.
- Non-repeatable read(반복 불가능한 읽기): Read committed 레벨에서 발생할 수 있는 문제입니다.
- Phantom read(유령 읽기): Repeatable read 레벨에서 발생할 수 있는 문제입니다.

---

## Redis란

#### Redis정의
REDIS(REmote Dictionary Server)는 메모리 기반의 “키-값” 구조 데이터 관리 시스템이며,
모든 데이터를 메모리에 저장하고 조회하기에 빠른 Read, Write 속도를 보장하는 비 관계형 데이터베이스이다.
레디스는 크게 5가지< String, Set, Sorted Set, Hash, List >의 데이터 형식을 지원한다.
Redis는 빠른 오픈 소스 인 메모리 키-값 데이터 구조 스토어이며, 다양한 인 메모리 데이터 구조 집합을 제공하므로 사용자 정의 애플리케이션을 손쉽게 생성할 수 있다.

---

## ORM

#### ORM이란

- ORM은 Object-Relational Mapping의 약자로, 객체와 관계형 데이터베이스 간의 매핑을 처리하는 기술이나 프레임워크를 말합니다. ORM을 사용하면 객체 지향적인 프로그래밍 언어로 작성된 코드를 데이터베이스와 상호작용할 수 있는 SQL 쿼리로 자동 변환하여 데이터베이스와 상호작용할 수 있습니다.

#### 객체-관계 간의 불일치

- 관계형 데이터베이스는 테이블, 로우, 컬럼과 같은 구조를 가지고 있습니다. 반면 객체 지향 프로그래밍은 클래스, 객체, 상속과 같은 구조를 가지고 있습니다. 이 두 구조의 불일치로 인해 객체를 관계형 데이터베이스에 저장하는 것이 어렵습니다. 이를 해결하기 위해 ORM 프레임워크를 사용합니다.

#### ORM의 장단점

- 장점

객체 지향적인 코드 작성으로 생산성 향상
데이터베이스의 구조와 상관 없이 객체 모델링 가능
코드의 가독성과 유지보수성 향상
SQL 쿼리를 직접 작성하지 않아도 되므로 개발자가 데이터베이스와 상호작용하는 데 필요한 노력과 시간을 줄일 수 있음

- 단점

SQL 쿼리를 직접 작성하지 않기 때문에 데이터베이스에 대한 세부적인 조작이 어려울 수 있음
ORM 자체의 성능 문제가 발생할 수 있음
ORM 프레임워크를 사용하기 위한 추가적인 러닝 커브가 필요할 수 있음

#### ORM 프레임워크들

- 대표적인 ORM 프레임워크로는 Hibernate, Django ORM, Sequelize, Entity Framework 등이 있습니다.

---

## 데이터베이스 풀

#### DB와 Client가 Connection을 어떻게 구성하는지 설명해 주세요
- 웹 어플리케이션 서버(WAS)와 데이터베이스 간의 연결은 일반적으로 JDBC(Java Database Connectivity) 드라이버를 사용하여 구성된다.
- JDBC는 자바 언어로 다양한 종류의 관계형 데이터베이스에 접속하고 SQL문을 수행하여 처리하고자 할 때 사용되는 표준 SQL 인터페이스 API이다.
- DBMS 종류(MySQL, MsSQL, Oracle 등)에 상관 없이 하나의 JDBC API를 사용해서 데이터베이스 작업을 처리할 수 있게 된다.

![image](https://github.com/gurrl9823/CS-JAVA-STUDY/assets/21374239/0d8462a0-a3c4-4dbd-b395-f421e222c127)

1. 드라이버 로드
- DB 종류에 맞는 드라이버를 로드합니다.
- Class.forName("driver")을 사용해서 Driver Class를 로딩하여 객체를 생성합니다.
- 생성된 객체는 DriverManager에 등록됩니다.
- DriverManager 클래스는 로드된 JDBC드라이버를 통해서 Connection을 활성화해주는(만드는) 객체입니다.
- Oracle JDBC_DRIVER : Class.forName("oracle.jdbc.driver.OracleDriver"); 
- MSSQL JDBC_DRIVER : Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
- MySQL JDBC_DRIVER : Class.forName("org.git.mm.mysql.Driver"); OR Class.forName("com.mysql.jdbc.Driver");

2. 데이터베이스 계정 연결
- DriverManager.getConnection() 메소드로 Connection 객체 생성해줍니다.
- DB_URL, DB_ID, DB_PW 을 매개변수로 갖습니다.
- Connection은 DB와 연결하는 객체입니다.
- Connection conn = DriverManager.getConnection(DB_URL, ID, PW);
- Oracle DB_URL = jdbc:oracle:thin:@ip:1521:ORCL
- MSSQL DB_URL = jdbc:sqlserver:ip:1433;DatabaseName=DB명
- MySQL DB_URL = jdbc:mysql://ip:3306/DB명

3. SQL문 실행을 위한 객체 생성
3.1 파라미터를 입력 받아 동적인 쿼리문을 실행할 경우
- PreparedStatement pstmt = conn.prepareStatement();
3.2 정적인 쿼리문을 실행할 경우
- Statement stmt = conn.createStatement();

4. SQL문 실행
String SQL = "insert into modell values(?,?,?)";
4.1 executeUpdate()
- insert, update, delete등 리턴 값이 필요 없는 쿼리문일 때 사용
- pstmt.executeUpdate(SQL);
- stmt.executeUpdate(SQL);
4.2 executeQuery()
- select등 리턴 값이 필요한 쿼리문일 때 사용
- pstmt.executeQuery(SQL);
- stmt.executeQuery(SQL);
4.3 쿼리실행 후 값을 받아올 경우
- ResultSet rs = null;
- rs = pstmt.executeQuery();
- 또는
- rs = stmt.executeQuery();
- 그 다음
- while(rs.next()){
-     String name = rs.getString("name");
- }
- rs.next()는 boolean을 리턴하는데 다음 레코드가 존재하면 true를 반환

5. DB 연결 해제 (리소스 반납)
- finally 블럭에서 close()를 이용하여 리소스를 생성한 역순으로 반납
- conn.close()
- pstmt.close()
- stmt.close()

![image](https://github.com/gurrl9823/CS-JAVA-STUDY/assets/21374239/b89ab9f4-8199-4727-9eba-a4fbaa0bd198)

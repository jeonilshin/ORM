# [DB] ORM

## ORM(Object Relational Mapping)
#### Object Relational Mapping, 객체-관계 매핑
- 객체와 관계형 데이터베이스의 데이터를 자동으로 매핑(연결)해주는 것을 말한다. 
    - 객체 지향 프로그래밍은 클래스를 사용하고, 관계형 데이터베이스는 테이블을 사용한다.
    - 객체 모델과 관계형 모델 간에 불일치가 존재한다.
    - ORM을 통해 객체 간의 관계를 바탕으로 SQL을 자동으로 생성하여 불일치를 해결한다.
- 데이터베이스 데이터 <—매핑—> Object 필드
    - 객체를 통해 간접적으로 데이터베이스 데이터를 다룬다.
- Persistant API라고도 할 수 있다.
    - e.g. JPA, Hibernate 등

### ORM의 장단점

#### 장점
- 객체 지향적인 코드로 인해 더 직관적이고 **비즈니스 로직에 더 집중**할 수 있게 도와준다.
    - ORM을 이용하면 SQL Query가 아닌 직관적인 코드(메서드)로 데이터를 조작할 수 있어 개발자가 객체 모델로 프로그래밍하는 데 집중할 수 있도록 도와준다.
    - 선언문, 할당, 종료 같은 부수적인 코드가 없거나 급격히 줄어든다.
    - 각종 객체에 대한 코드를 별도로 작성하기 때문에 코드의 가독성을 올려준다.
    - SQL의 절차적이고 순차적인 접근이 아닌 객체 지향적인 접근으로 인해 생산성이 증가한다.
- **재사용 및 유지보수**의 편리성이 증가한다.
    - ORM은 독립적으로 작성되어있고, 해당 객체들을 재활용 할 수 있다.
    - 때문에 모델에서 가공된 데이터를 컨트롤러에 의해 뷰와 합쳐지는 형태로 디자인 패턴을 견고하게 다지는데 유리하다.
    - 매핑정보가 명확하여, ERD를 보는 것에 대한 의존도를 낮출 수 있다.
- **DBMS에 대한 종속성이 줄어든다.**
    - 객체 간의 관계를 바탕으로 SQL을 자동으로 생성하기 때문에 RDBMS의 데이터 구조와 Java의 객체지향 모델 사이의 간격을 좁힐 수 있다.
    - 대부분 ORM 솔루션은 DB에 종속적이지 않다.
    - 종속적이지 않다는것은 구현 방법 뿐만아니라 많은 솔루션에서 자료형 타입까지 유효하다.
    - 프로그래머는 Object에 집중함으로 극단적으로 DBMS를 교체하는 거대한 작업에도 비교적 적은 리스크와 시간이 소요된다.
    - 또한 자바에서 가공할경우 equals, hashCode의 오버라이드 같은 자바의 기능을 이용할 수 있고, 간결하고 빠른 가공이 가능하다.

#### 단점
- 완벽한 ORM 으로만 서비스를 구현하기가 어렵다.
    - 사용하기는 편하지만 설계는 매우 신중하게 해야한다.
    - 프로젝트의 복잡성이 커질경우 난이도 또한 올라갈 수 있다.
    - 잘못 구현된 경우에 속도 저하 및 심각할 경우 일관성이 무너지는 문제점이 생길 수 있다.
    - 일부 자주 사용되는 대형 쿼리는 속도를 위해 SP를 쓰는등 별도의 튜닝이 필요한 경우가 있다.
    - DBMS의 고유 기능을 이용하기 어렵다. (하지만 이건 단점으로만 볼 수 없다 : 특정 DBMS의 고유기능을 이용하면 이식성이 저하된다.)
- 프로시저가 많은 시스템에선 ORM의 객체 지향적인 장점을 활용하기 어렵다.
    - 이미 프로시저가 많은 시스템에선 다시 객체로 바꿔야하며, 그 과정에서 생산성 저하나 리스크가 많이 발생할 수 있다.

### The Object-Relational Impedance Mismatch

|    Mismach    | Second Header |
| ------------- | ------------- |
|  Granularity  | Sometimes you will have an object model which has more classes than the number of corresponding tables in the dabase. 
| Lets take an exmaple of **Person details**, we could broke down person details into two classes one is **Person** and another is **Address** for code reusability and code maintainability purpose But assume that to store Person details in database there is only **one table called Person**.  |
|  Inheritance  | RDBMSs do not define anything similar to Inheritance which is a natural paradigm in object-oriented programmiong languages.  |
|    Identity   | A RDBMS defines exactly one notion of 'sameness': the **primary key**. Java, however, defines both **object identity** (a==b) and **object equality** (a.equals(b)).  |
|  Associations |   |
|   Navigation  |   |


### 영속성(Persistence)
- 데이터를 생성한 프로그램이 종료되더라도 사라지지 않는 데이터의 특성을 말한다.
- 영속성을 갖지 않는 데이터는 단지 메모리에서만 존재하기 때문에 프로그램을 종료하면 모두 잃어버리게 된다.
- **Object Persistence(영구적인 객체)**
    - 메모리 상의 데이터를 파일 시스템, 관계형 테이터베이스 혹은 객체 데이터베이스 등을 활용하여 영구적으로 저장하여 영속성 부여한다.
    
        ![Alt text](image.png)

    - 데이터를 데이터베이스에 저장하는 3가지 방법
        - 1) JDBC(Java에서 사용)
        - 2) Spring JDBC (e.g. JDBCTemplate)
        - 3) Persistence Framework (e.g. Hibernate, Mybatis 등)

- Persistence Layer
    - 프로그램의 아키텍처에서, 데이터에 영속성을 부여해주는 계층을 말한다.
    - JDBC를 이용하여 적접 구현할 수 있지만 Persistence framework를 이용한 개발이 많이 이루어진다.

- Persistence Framework
    - JDBC 프로그래밍의 복잡함이나 번거로움 없이 간단한 작업만으로 데이터베이스와 연동되는 시스템을 빠르게 개발할 수 있으며 안정적인 구동을 보장한다.
    - Persistence Framework는 [SQL Mapper와 ORM]으로 나눌 수 있다. 
        - e.g. JPA, Hibernate, Mybatis 등

[SQL Mapper와 ORM]: https://gmlwjd9405.github.io/2018/12/25/difference-jdbc-jpa-mybatis.html
    
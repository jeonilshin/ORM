# [DB] ORM

## ORM(Object Relational Mapping)
#### Object Relational Mapping, 객체-관계 매핑


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
    
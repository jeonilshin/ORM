# [DB] ORM

## ORM(Object Relational Mapping)
Object-Relational Mapping 즉, 객체와 관계형 데이터베이스 매핑의 줄임말입니다. 우리가 OOP(Object Oriented Programming)에서 쓰는 객체라는 개념을 구현한 클래스와RDB(Relational DataBase)에서 쓰이는 데이터인 테이블을 매핑(연결)하는 것을 의미합니다.

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
    
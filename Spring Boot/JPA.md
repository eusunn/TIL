# 4강
JPA란?

Java Persistence API (Application Programing Interface) 이다
- 영속성을 의미한다.
    
  - 영속성이란?

      데이터를 생성한 프로그램의 실행이 종료되더라도 사라지지 않는 데이터의 특성을 의미한다. 연속성은 파일 시스템, 관계형 데이터베이스 혹은 객체 데이터베이스 등을 활용하여 구현한다. 

      어떤 데이터가 영구히 기록될 수 있게 해주는것 

      램에 기록하는것은 휘발성 → 하드디스크(파일시스템) 비휘발성

  - API?

      애플리케이션(A) 프로그래밍(P) 인터페이스(I)

      → 애플리케이션을 프로그래밍하기 위한 인터페이스를 제공하는 것 

      프로토콜 : 약속 

      A , B, C 가 동등할 때 

      B: 이제부터 나한테 연락할 때는 전화하지말고 직접 찾아와 

      이 약속에 A, C가 싫다고 말할 수 있다.  B는 동등한 관계이기 떄문에 강요할 수 없다. 

      → 그럼 우리 email로 연락하자! 라고 다른 해결책을 내놓을 수 있다. 이것이 프로토콜의 약속

      인터페이스 : 약속

      A , B, C 

      B: 이제부터 나한테 연락할 때는 전화하지말고 직접 찾아와 
      A,C는 B의 말을 따라야 한다.
      파워가 있는 B의 약속이 : 인터페이스
# 5강
- ORM기술 이다.
 
     → Object Relational Mapping (오브젝트를 데이터베이스를 매핑 해주는 방법  

    ORM : 나의 하인     

    추상적인 개념을 현실적으로 뽑아내는 것을 모델링이라고 한다.


- 반복적인 CRUD 작업을 생략하게 해준다.
 
   select(1건), selectAll(여러개)

    update

    delete

    insert

# 6강
- 영속성 컨텍스트를 가지고 있다.

   영속성 : 어떤 데이터를  DB에 영구적으로 저장하게 해주는 것

   컨텍스트 (context) : 대상에 대한 모든 정보

   자바는 영속성 컨텍스트 

   select 요청을 하면 영속성 컨텍스트 한테 가서 해당 데이터를 요청한다. 영속성 컨텍스트는 데이터를 가지고 있지 않기 때문에 DB에 가서 데이터를 요청하고 받아와서 데이터를 자바 오브젝트로 바꾼다.  영속성 컨텍스트에서 일어나는 모든 일은 자동으로 처리된다.

- DB와 OOP의 불일치성을 해결하기 위한 방법론을 제공한다. (DB는 객체저장 불가능)

 자바의 관점

 Class Team {
 
 int id;
 
 String name;
 
 String year;
 
 }

Class player { // DB에서 공필성을 select해오면 

  int id; // = 2
  
  String name;  // = 공필성
  
  //int teamId; // = 1 이렇게 해오면 일반 사용자는 teamId가 1인걸 보고 어느 팀인지 모른다.
  
                // 따라서 두번 select 해오던가 조인으로 해결한다. 
                
                // 근데 자바에서는 기본자료형이 아닌 오브젝트를 저장하고 뽑아 
                
                //     올수 있기때문에
                
  Team team; // Team 오브젝트 (jpa 가 매핑해줄것임)
  
 }

ORM을 하게 되면 DB와 OOP의 불일치성을 해결할 수 있다.


# 7강

- OOP의 관점에서 모델링을 할 수 있게 해준다. (상속, 콤포지션, 연관관계)

Class Car extends EntityDate{

  int id; // (pk)
  
  String name;
  
  String color;
  
  Engine engine;
  
  //Timestamp createDate;
  
  //Timestamp updateDate;
  
}

Class Engine extends EntityDate{

  int id;
  
  int power;
  
  //Timestamp createDate;
  
  //Timestamp updateDate;
  
}

Class EntityDate{

  Timestamp createDate;
  
  Timestamp updateDate;
  
}

상속  Engine - car (불가능 카의 부모가 엔진이 아니기때문에)

따라서 콤포지션(결합)을 해줘야한다.

- 방언처리가 용이하여 Migration하기 좋음. 유지보수에도 좋음

스프링 → JPA → DB

     추상화 객체
      
      dialect 
      
       -오라클
       
       -마리아
       
       -MSSQL
       
       -MySQL
       
       등등
       
오라클을 사용하다가 MySQL로 바뀌었을 때 스프링에서 코드가 많이 바뀌어야하는데 JPA를 이용하게 되면 그럴 필요가 없어진다.

- 쉽지만 어렵다.

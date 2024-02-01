## JPA
- 자바에서 객체와 관계 매핑을 위한 표준 명세이다.

## Spring Data JPA
- Spring에서 제공하는 모듈로 JPA위에 추가적인 기능을 제공하여 개발을 편리하게 만드는 라이브러리, 프레임워크이다.
- Repository라는 인터페이스를 제공함으로서 간편하게 사용 가능하다.

📌 기존에 프로젝트를 진행했을 때 실제로 entityManager를 사용하지않고 Repository를 사용하여
간단한 CRUD SQL을 작성한 경험이 있다. 이때 사용한 것이 Spring Data JPA이다.

  
### EntityManger?
- 엔티티를 관리해 데이터베이스와 애플리케이션 사이에 객체를 생성,수정,삭제하는 등의 역할을 한다.


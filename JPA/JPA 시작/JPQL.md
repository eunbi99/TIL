### 🚀 JPQL

- 하나 이상의 회원 목록을 조회하는 코드
    
    ```jsx
    TypedQuery<Member> query = em.createQuery("select m from Member m", Member.class);
    List<Member> members = query.getResultList();
    ```
    
    - 테이블이 아닌 엔티티 객체를 대상으로 검색하려면 데이터베이스의 모든 데이터를 애플리케이션으로 불러와서 엔티티 객체로 변경한 뒤 검색해야하는데 이는 불가능하다.
    - 애플리케이션이 필요한 데이터만 데이터베이스에서 불러오려면 결국 검색 조건이 포함된 SQL을 사용해야한다.
    - JPA는 SQL을 추상화한 JPQL이라는 객체지향 쿼리 언어를 제공한다.
    
- from Member은 회원 엔티티 객체를 말하는 것이지 MEMBER 테이블이 아니다.
- JPQL은 데이터베이스 테이블을 전혀 알지 못한다!
- JPQL을 사용하려면 em.createQuery(JPQL,반환타입) 메소드를 실행해서 쿼리 객체를 생성한 후 쿼리 객체의 getResultList() 메소드를 호출하면 된다.

 > ### 📍 JPQL과 SQL의 차이점
    
    JPQL은 엔티티 객체를 대상으로 쿼리한다.(= 클래스와 필드를 대상으로 쿼리한다)
    SQL은 데이터베이스 테이블을 대상으로 쿼리한다.

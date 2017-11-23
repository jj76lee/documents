# 캐스케이드  (Cascade)
## CascadeType.PERSIST
* PERSIST = DB에 저장시켜서 해당 ID의 객체가 영속성을 가지는 기능

* CascadeType.PERSIST 를 사용하지 않은 경우,
  * Team 생성후 repository에 저장후 persist 상태를 만든뒤에 저장
  * 연결 엔티티에서 Team을 저장하고, TeamMember new한뒤 repository에 저장후 member저장
* CascadeType.PERSIST 를 사용한 경우
  * member 저장시 관계가 있는 객체가 모두 PERSIST 상태라 됨
  
### 캐스케이드 양방향 관계에서, 고객쪽에 CascadeType.PERSIST 를 주는 경우, 
 엔티티는 저장되지만 관계(fk)가 NULL이 된다.

## CascadeType.Remove : 
  * 1:1에서 member 삭제시 team도 삭제됨
  * N:1에서 member 삭제시 team이 삭제되면서, constraint 제약조건에 의한 exception이 발생함
  * 역방향(mappedBy)으로 Remove , team 삭제시 member들이 삭제됨. (가장 정상적이다)
  * 양방향에 설정한다면, 위험하다.. => 코드 돌려보고 쿼리 확

```java

@Entity
@Data
public class Member {
    @Id
    @GeneratedValue
    private Long id;
    
    @Column
    private String username;
    
    @ManyToOne(cascade = CascadeType.PERSIST)
    private Team team;
}
```

## CascadeType.REFRESH
* entityManager.refresh(entity) ; DB에서 현재 엔티티의 값을 다시 조회한다.
* 하나의 엔티티를 refresh를 했더니 연쇄적으로 select 문이 실행된다  => 성능저하
  * Lazy 인 경우 개별 select
  * 아닌 경우 left join 으로 refresh
* OO 의 개념에 충실하지만, 잘못사용하면 성능이 저하된다.

## orphanRemoval 
 * 관계가 끊어진 자식 = 고아를 제거하는 옵션
 * OneToOne, OneToMany 에 제공
 * CascadeType.REMOVE 와는 다르다.

# Fetch
## JPA의 조회 전략 
  * Eager: @ManyToOne, @OneToOne 의 디폴트 fetch, -> Join이 되니까 그렇다.
  * Lazy:  @OneToMany, @ManyToMany 의 디폴트 fetch,
## Eager
  - Member(N)-(1)Team
  - 조인을 한다 * left outer join, 
    * 만약 Team 참조가 not null(optional = false )이면 inner join으로 사용됨
  - class 내의 참조 클래스의 값이 이미 들어가 있다.
 
    
## Lazy
  - lazy 라면, 해당 참조는 null은 아니고 데이터가 비어 있는 상태 (Proxy), 
    * read 하는 시점에 select
  - One to One 일때, Lazy loading

## OneToOne 양방향 관계
  - member로 Lazy Fetch로 프록시
  - Locker로 역방향(mappedBy) 로 연결시 Lazy Fetch가 아닌, 즉시 로딩(select 구)
  
# 도메인주도 설계
## Aggregate
* Aggregate => 비슷한 엔티티 끼리 묶음 
  * 엔티티는 다른 Aggregate에 묶음으면 안되요
  * 관계를 줄임으로써 북잡도를 낮춤
  * Root Entity = 모듈의 대표성을 갖추는 Entity
  * 도메인의 경리성 최대한 보장 = 외부에서 접근할때는 Root Entity를 통해서만 
  
  
##

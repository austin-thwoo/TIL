#about-jpa

#### 1. between EGER & LAZY
Eger(즉시로딩) : 조회할때 관련된 테이블을 모두 조회하는 방법

즉시로딩은 개발자가 이해할수없거나 의도하지 않은쿼리가 나갑니다

Lazy(지연로딩) : 조회할때는 그 정보만(주소?) 담겨있는 Proxy 객체가 조회되고 객체 사용시점에서 조회및 쿼리가 나간다

지연로딩은 쿼리가 사용하는 시점에서 쿼리가 나가기때문에 후에 fechJoin으로 해결하는것이 바람직할 수 있다

실무에선 지연로딩을 쓰라고 하는이유 :테이블이 한두개가 아니라 각각 쓰임에 맡게 전략을 가져가야하지만 문제를 알수있는 지연로딩으로 코딩하고 처리하는 방식으로 해결하자
# N+1 problem

## N+1문제란?

### 연관관계가 설정된 엔티티를 조회할 경우에 조회된 데이터 갯수(n) 만큼 연관관계의 조회 쿼리가 추가로 발생하여 데이터를 읽어오는 현상

```java
@Entity
public class User {
    @Id
    @GeneratedValue
    private long id;
    private String firstName;
    private String lastName;

    @ManyToOne(fetch = FetchType.EAGER)		// 즉시 로딩
    @JoinColumn(name = "team_id", nullable = false)
    private Team team;
}
```

```java
@Entity
public class Team {
    @Id
    @GeneratedValue
    private long id;
    private String name;

    @OneToMany(fetch = FetchType.EAGER)
    private List<User> users = new ArrayList<>();
}
```

excute

```java
teamRepository.findAll();
System.out.println("============== N+1 시점 확인용 ===================");
```

Result

```java
Hibernate: select team0_.id as id1_0_, team0_.name as name2_0_
					from team team0_
Hibernate: select
							 users0_.team_id as team_id1_1_0_,
							 users0_.users_id as users_id2_1_0_,
							 user1_.id as id1_2_1_,
							 user1_.first_name as first_na2_2_1_,
							 user1_.last_name as last_nam3_2_1_,
							 user1_.team_id as team_id4_2_1_ 
					 from team_users users0_
							 inner join user user1_ on users0_.users_id=user1_.id
					 where users0_.team_id=?
Hibernate: select users0_.team_id as team_id1_1_0_, users0_.users_id as users_id2_1_0_, user1_.id as id1_2_1_, user1_.first_name as first_na2_2_1_, user1_.last_name as last_nam3_2_1_, user1_.team_id as team_id4_2_1_ from team_users users0_ inner join user user1_ on users0_.users_id=user1_.id where users0_.team_id=?
Hibernate: select users0_.team_id as team_id1_1_0_, users0_.users_id as users_id2_1_0_, user1_.id as id1_2_1_, user1_.first_name as first_na2_2_1_, user1_.last_name as last_nam3_2_1_, user1_.team_id as team_id4_2_1_ from team_users users0_ inner join user user1_ on users0_.users_id=user1_.id where users0_.team_id=?
Hibernate: select users0_.team_id as team_id1_1_0_, users0_.users_id as users_id2_1_0_, user1_.id as id1_2_1_, user1_.first_name as first_na2_2_1_, user1_.last_name as last_nam3_2_1_, user1_.team_id as team_id4_2_1_ from team_users users0_ inner join user user1_ on users0_.users_id=user1_.id where users0_.team_id=?
============== N+1 시점 확인용 ===================
```

Fetch type = LAZY로 지연로딩 한 경우

```java
Hibernate: select team0_.id as id1_0_, team0_.name as name2_0_ from team team0_
```

N+1 이 발생하지 않는것처럼 보이지만

```java
List<Team> all = teamRepository.findAll();
System.out.println("============== N+1 시점 확인용 ===================");
all.stream().forEach(team -> {
    team.getUsers().size();
});
```

```java
Hibernate: select team0_.id as id1_0_, team0_.name as name2_0_ from team team0_
============== N+1 시점 확인용 ===================
Hibernate: select users0_.team_id as team_id1_1_0_, users0_.users_id as users_id2_1_0_, user1_.id as id1_2_1_, user1_.first_name as first_na2_2_1_, user1_.last_name as last_nam3_2_1_, user1_.team_id as team_id4_2_1_ from team_users users0_ inner join user user1_ on users0_.users_id=user1_.id where users0_.team_id=?
Hibernate: select users0_.team_id as team_id1_1_0_, users0_.users_id as users_id2_1_0_, user1_.id as id1_2_1_, user1_.first_name as first_na2_2_1_, user1_.last_name as last_nam3_2_1_, user1_.team_id as team_id4_2_1_ from team_users users0_ inner join user user1_ on users0_.users_id=user1_.id where users0_.team_id=?
Hibernate: select users0_.team_id as team_id1_1_0_, users0_.users_id as users_id2_1_0_, user1_.id as id1_2_1_, user1_.first_name as first_na2_2_1_, user1_.last_name as last_nam3_2_1_, user1_.team_id as team_id4_2_1_ from team_users users0_ inner join user user1_ on users0_.users_id=user1_.id where users0_.team_id=?
Hibernate: select users0_.team_id as team_id1_1_0_, users0_.users_id as users_id2_1_0_, user1_.id as id1_2_1_, user1_.first_name as first_na2_2_1_, user1_.last_name as last_nam3_2_1_, user1_.team_id as team_id4_2_1_ from team_users users0_ inner join user user1_ on users0_.users_id=user1_.id where users0_.team_id=?
```

객체를 탐색(사용?) 하는 시점에서 N+1이 발생한다

### 해결방법

1. Fetch Join⭐
    1. DB에서 데이터를 가져올 때 처음부터 연관된 데이터까지 같이 가져오게 하는 방법이다

1. EntityGraph 어노테이션
    1. @@EntityGraph 라는 어노테이션을 사용해서 Fetch 조인을 하는것인데 그냥 알아만 두자
    - 사용하는 순간 조금만 관계가 복잡해져도 헬게이트가 열린다.
2. Batch Size
    1. 이 옵션은 정확히는 N+1 문제를 안 일어나게 하는 방법은 아니고 N+1 문제가 발생하더라도 select * from user where team_id = ? 이 아닌 select * from user where team_id in (?, ?, ? ) 방식으로 N+1 문제가 발생하게 하는 방법이다. 
        
         이렇게  100번 일어날 N+1 문제를 1번만 더 조회하는 방식으로 성능을 최적화할 수 있다
```java
         #application.yml

spring:
  jpa:
    properties:
      hibernate:
        default_batch_fetch_size: 1000

#application.properties
spring.jpa.properties.hibernate.default_batch_fetch_size=1000

====>>>>>

Hibernate: select team0_.id as id1_0_, team0_.name as name2_0_ from team team0_
Hibernate: select users0_.team_id as team_id1_1_1_,
					 users0_.users_id as users_id2_1_1_, user1_.id as id1_2_0_,
					 user1_.first_name as first_na2_2_0_, user1_.last_name as last_nam3_2_0_,
					 user1_.team_id as team_id4_2_0_
					 from team_users users0_
					 inner join user user1_ on users0_.users_id=user1_.id
					 where users0_.team_id in (?, ?, ?, ?)
                     ```



##GEOMETRY

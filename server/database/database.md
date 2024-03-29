## 격리 수준
- <code>READ UNCOMMITTED</code>
  - 각 트랜잭션의 COMMIT, ROLLBACK에 상관 없이 해당 트랙잭션의 변경 내용에 대해서 SELECT 함(Dirty read 가능)
  - Dirty read를 유발하는 READ UNNCOMMITTED 격리 수준은 정합성에 문제가 많고 RDBMS 표준에서 트랜잭션 격리 수준으로 인정하지 않을 정도이다
- <code>READ COMMITTED</code>
  - 온라인 서비스에서 가장 많이 선택되는 격리 수준
  - Dirty read가 발생하지 않음 -> 무조건 COMMIT된 데이터를 조회
  - __NON-REPEATABLE READ__ 라는 부정합 존재 -> 트랜잭션이 COMMIT 되어야만 해당 데이터를 정확하게 조회할 수 있으므로 다른 하나의 트랜잭션 내에서 똑같은 SELECT를 했을 때 다른 데이터를 조회할 수 있음(REAPEATABLE READ 시 같은 데이터를 보장하지 않음)
  - 금전적인 처리와 같이 데이터 정합성이 중요한 경우 해당 격리 수준보다 높은 격리 수준을 사용
<code>REPEATABLE READ</code>
  - MySQL InnoDB 스토리지 엔진에서 기본으로 사용하는 격리 수준
  - 바이너리 로그를 가진 MySQL 서버에서는 REPEATABLE READ 격리 수준 이상을 사용해야함
  - READ COMMITED에서 발생하는 __NON-REPEATABLE READ__  부정합이 발생하지 않음
  - 언두 로그를 이용해 REPEATABLE READ를 보장한다 -> 한 트랜잭션에서 같은 데이터 조회 시 다른 트랜잭션이 해당 데이터를 수정하더라도 언두 로그에 존재하는 데이터를 조회하게 됨
  - __PHANTOM READ 부정합 발생__ 
    - 다른 트랜잭션에서 데이터 수정 발생 시 똑같은 READ에서도 레코드가 보였다 안 보였다 하는 현상으로 SELECT ... FOR UPDATE 쿼리에서 발생 가능
    - FOR UPDATE, LOCK IN SHARE MODE 쿼리는 레코드에 쓰기 잠금을 걸어야하지만, 언두 로그에는 잠금을 걸 수 없으므로 언두 영역의 변경 전 데이터를 가져오는 게 아니라 현재 레코드의 값을 가져오게 됨
- <code>SERIALIZABLE</code>
  - 가장 단순하면서 가장 엄격한 격리 수준
  - 동시 처리 성능이 다른 격리 수준보다 떨어짐
  - PHANTOM READ 발생 X
  - InnoDB 스토리지 엔진에서는 갭 락과 넥스트 키 락 덕분에 REPEATABLE READ 격리 수준에서도 이미 PHANTOM READ가 발생하지 않아 FOR UPDATE, LOCK IN SHARE MODE의 경우를 제외하고는 굳이 SERIALIZABLE을 사용할 필요성은 없음


## Index
https://velog.io/@gillog/SQL-Index인덱스
--참고

indexs는 rdbms에서 검색 속도를 높이기 위한 기술이다.

RDBMS에 서 사용하는 INDEX는 B-Tree 에서 파생된 __B+ Tree__ 를 사용해서 색인화한다.

보통 SELECT 쿼리의 WHERE절이나 JOIN 예약어를 사용했을때 인덱스가 사용되며 

SELECT 쿼리의 검색 속도를 빠르게 하는데 목적을 두고 있다.




## Cluster-클러스터
보통 데이터베이스 구축의 경우 1개의 서버로 하나의 데이터베이스를 구축해서 사용하는 편입니다.
그런데 이렇게 1개의 서버가 하나의 데이터베이스를 사용할 경우 이 서버가 죽으면 서비스가 죽는 현상이 발생하게 됩니다.
또는 사용자가 엄청나게 유입되었을 때 이에 대한 처리를 서버 하나가 처리할려고 하면 서버는 견디지 못하고 뻗어버리게 됩니다.
이런 여러가지 이유로 **하나의 데이터베이스를 여러 서버가 나눠서 구축**하게 됩니다.
이처럼 하나의 데이터베이스를 여러개의 서버로 구축되는 경우를 클러스터(Cluster)라고 지칭합니다.

데이터베이스 클러스터의 조건을 만족시키기 위한 3가지 조건
- 고가용성
- 병렬처리
- 성능향상
 ### {1}. 고가용성
데이터베이스에서 가용성이란 데이터베이스가 동작하기 있는 시간과 정지한 시간의 비율을 뜻합니다.
즉, 1년 동안 몇 분이 정지했음을 비율로 나타낸 것이 가용성인데요
데이터베이스도 컴퓨터 위에서 돌아가기 때문에 여러분도 알다시피 컴퓨터는 여러 이유로 멈출때가 있습니다(어떨 땐 아무 이유 없이 꺼질 때도 있는거 같아요).
이런 현상이 일어났을 때 서버가 하나뿐이라면 서비스는 데이터베이스가 복구될 때까지 정지되는 크나큰 장애가 발생하게 됩니다.
이처럼 **한 부분의 문제가 전체 시스템을 정지시켜 버리는 것을 SPOF(Single Point Of Failure)**
라고합니다. 이를 해결하기 위해 고가용성 클러스터를 사용합니다.
 ### {2}. 병렬처리
 테이블에 데이터도 엄청 많고 컬럼(필드)도 엄청 많아 SQL 문이 복잡하게 될 경우 SQL 문을 실행하는데 많은 시간이 걸리게 됩니다.
이런 상황에서 데이터베이스를 여러개의 단위별로 병렬처리해서 결과를 통합하여 넘겨준다면 훨씬 빠르게 결과를 얻을 수 있습니다.
복제 데이터베이스는 항상 원본 데이터베이스와 같은 데이터를 가지고 있기 때문에 DML(SELECT, INSERT, UPDATE, DELETE)을 고려해서 분산시키면 전체적인 성능향상을 시킬 수 있습니다.
데이터베이스 클러스터는 병렬처리를 할 수 있어야 합니다.

 ### {3}. 성능향상
데이터베이스를 사용하는 사용자가 엄청나게 많아질 경우 데이터베이스의 복제본을 만들어서 참조 처리의 경우 복제 데이터베이스를 사용하면 사용자가 많아져도 대비를 할 수 있습니다.
데이터베이스 클러스터는 이러한 성능향상을 만족시킬 수 있어야 합니다.

### 결 론
- 데이터베이스에서 클러스터란 여러개의 서버가 하나의 데이터베이스를 나눠서 처리하는 형태를 뜻한다.
- 고가용성, 병렬처리, 성능향상   
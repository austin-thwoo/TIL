## Elasticsearch

Elasticsearch는 Apache Lucene 기반의 Java 오픈소스 분산형 RESTful 검색 및 분석 엔진입니다.
방대한 양의 데이터에 대해 실시간으로 저장과 검색 및 분석 등의 작업을 수행할 수 있습니다.
특히 정형 데이터, 비정형 데이터, 지리 데이터 등 모든 타입의 데이터를 처리할 수 있는데 이는 JSON 문서(Document)로 데이터를 저장하기 때문입니다.
Elasticsearch는 단독 검색을 위해 사용하거나, ELK(Elasticsearch & Logstash & Kibana) 스택을 기반으로 사용합니다.

###[1]. DBMS와 Elasticsearch 용어 비교



|DBMS|Elasticsearch|
|------|---|
|DBMS HA 구성(MMM, M/S)|Cluster|
|DBMS Instance|Node|
|Table|Index|
|Partition|Shard/ Routing|
|Row|Document|
|Column|Field|
|Row of columnar data|Serialized JSON document|
|Join|Nested or Parent/Child|
|SQL(DML)|QueryDSL|
|Index|Analyzed|
|Primary Key	|_id|
|Configuration|elasticsearch.yml & settings|
|Schema	|Mappings|

@Document : ES에 매핑할 클래스임을 나타내고 클래스 레벨에 적용합니다. 다음과 같은 속성을 제공합니다.
indexName : 이 엔티티를 저장할 인덱스 이름
createIndex : repository 부트스트래핑에 인덱스를 부여할지 여부, default = true
versionType : 버전 관리, default= EXTERNAL
@Id : ID 목적으로 사용되는 필드 표기
@Transient : 기본적으로 모든 필드는 저장 또는 검색 시 도큐먼트에 매핑되는데 이 주석이 포함된 필드는 제외
@PersistenceConstructor : 데이터베이스에서 개체를 인스턴스화할 때 사용할 생성자(보호된 패키지도 포함). 생성자 argument는 검색된 문서의 키 값에 이름에 의해 매핑
@Field : 필드의 속성 정의, 대부분의 속성이 Elasticsearch Mapping 정의에 매핑
name : ES 문서에 나타낼 필드 이름, 설정되지 않을 경우 Java 필드 이름 그대로 사용
type : 필드 유형 정의, 유형 참조 문서
format 및 pattern : Date 타입의 필드의 경우 반드시 format을 정의해야 한다.
store : 원래 필드 값이 ES에 저장되야 하는지 판단하는 플래그, default = false
커스텀 analyzer와 normalizer를 지정하여 커스텀마이징하는 analyzer, searchAnalyzer, Normalizer
@GeoPoint : 필드가 geo_point 데이터 형식임을 표기, 만약 필드가 GeoPoint 클래스의 인스턴스인 경우 생략 가능


	
	
	
	
	
	
	
	
	
	
	

	



```javascript
docker run -d --name elasticsearch -v /Users/austin/Documents/austin/docker/elasticsearch_volume:/usr/share/elasticsearch/data -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.17.9
```

https://www.baeldung.com/spring-data-elasticsearch-tutorial

```java
GET _search
{"prefix": {"tag.keyword": {"value": "?0"}}}


DELETE /tagdoc/_doc/%23수정

POST /tagdoc/_doc/_se


PUT tagdoc/
{
  "properties": {
    "count": {
      "type": "long"
    }
  }
}
GET tagdoc/_doc/%23수정

PUT tagdoc/_mapping
{
  "properties": {
    "count": {
      "type": "long",
      "null_value": 0
    }
  }
}

POST tagdoc/_doc/
{
  "id":"#수정"
  "": "GET /search HTTP/1.1 200 1070000",
  "user": {
    "id": "kimchy"
  }
}

GET tagdoc/_mapping



PUT tagdoc/_mapping
{
  "properties": {
    "oriId": {
      "type": "long"
    },
    "tag": {
      "type": "text",
      "fields": {
        "keyword": {
          "type": "keyword",
          "ignore_above": 256
        }
      }
    }
  }
}

GET /tagdoc/_search
{"size": 5000,
  "sort": [
  {
    "oriId": {
      "order": "asc"
      
    }
  }
]
  
}
GET /tagdoc/_search
{
 "size": 5000,
  "query": {
    "match_all": {}
  }
}
PUT /tagdoc/_settings
{
  "index.max_result_window": 10000
}



POST tagdoc/_update_by_query
{
  "script": {
    "source": "ctx._source.count = 0",
    "lang": "painless"
  },
  "query": {
    "match_all": {}
  }
}
```



```java
PUT tagdoc/_mapping
{
  "properties": {
    "postCount": {
      "type": "long",
      "null_value": 0
    }
  }
}
PUT tagdoc/_mapping
{
  "properties": {
    "shortsCount": {
      "type": "long",
      "null_value": 0
    }
  }
}
```
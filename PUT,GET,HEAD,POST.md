
# 1. PUT : 데이터 입력


```put [인덱스 이름]/_doc/[도큐먼트아이디]``` : [인덱스 이름] 위치에 메세지가 쌓임 

```
PUT my_index/_doc/1
{
  "message":"안녕하세요"
}
```
 

# 2. GET 데이터 확인 

- id를 아는 특정 데이터를 확일할 때
```GET my_index/_doc/1``` : 입력받은 my_index/_doc/1 의 정보가 출력 됨

  - 결과 
```
{
  "_index" : "my_index",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 2,
  "_seq_no" : 1,
  "_primary_term" : 2,
  "found" : true,
  "_source" : {
    "message" : "안녕하세요"
  }
}
```


```GET my_index/_source/1``` : doc 내용만
  - 결과    
```    
{
  "message" : "안녕하세요"
}
```    
    
    
- 데이터 여러개 한꺼번에 볼때    
```GET my_index/_search```
  - 결과    
```
{
  "took" : 1,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 3,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "my_index",
        "_type" : "_doc",
        "_id" : "1",
        "_score" : 1.0,
        "_source" : {
          "message" : "안녕하세요"
        }
      },
      {
        "_index" : "my_index",
        "_type" : "_doc",
        "_id" : "2",
        "_score" : 1.0,
        "_source" : {
          "message" : "안녕하세요 엘라스틱"
        }
      },
      {
        "_index" : "my_index",
        "_type" : "_doc",
        "_id" : "9ftxInYB1orpAuoXE-zd",
        "_score" : 1.0,
        "_source" : {
          "message" : "안녕하세요 엘라스틱"
        }
      }
    ]
  }
}
```    
    
    
- 데이터 10개가 넘어갈때 사이즈 옵션을 안주면 다 안보임

```GET my_index/_search?size=100```

 

- 매핑 인덱스 형태 자동으로 잡기 

```GET my_index/_mapping/```






# 3. HEAD 상태정보 리턴    

```HEAD my_index/_doc/1``` -> ```200 - OK```
     
    
    
    
# 4. POST
- id없이 insert       
```
POST my_index/_doc/    
{
  "message":"안녕하세요 엘라스틱" 
}
```
 


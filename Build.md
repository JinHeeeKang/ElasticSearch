# mac 에서 Elastic Search, Kibana, Logstash 환경 구축
- 맥에서 환경 구축하는 건 처음이라 구글링하며 설치 해보았습니다.

## 1. JAVA 설치

- Java 8 JDK 파일 설치 구글링 해서 나온 블로그의 url을 통해 다운로드

- (참고)
 http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html  
 출처: https://blog.acu.pe.kr/56 [아쿠 :: 컴공의 기록]

- java -version 로 설치 됐는지 확인
```
java version "1.8.0_171"
Java(TM) SE Runtime Environment (build 1.8.0_171-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.171-b11, mixed mode)
```

## 2. Elastic Search 설치
- https://www.elastic.co/kr/downloads/elasticsearch 에서도 가능
- Brew 패키지 관리자 설치 후 Elasticsearch을 설치함


### 2.1 Brew 패키지 관리자 설치
- 터미널에 붙여넣기 
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

### 2.2 elasticsearch 설치
```
brew install elasticsearch
```

## 3. elasticsearch 실행
- 실행
```
elasticsearch
```
- 접속 확인
```
http://localhost:9200/
```
- 이런 화면이 나오면 성공
```
{
  "name" : "gangjinhuiui-MacBook-Pro.local",
  "cluster_name" : "elasticsearch_brew",
  "cluster_uuid" : "S391dADYSqqRa7WRGmiybA",
  "version" : {
    "number" : "7.8.1-SNAPSHOT",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "unknown",
    "build_date" : "2020-07-31T16:47:49.963461Z",
    "build_snapshot" : true,
    "lucene_version" : "8.5.1",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}
```

-------

# Kibana 설치
- 참조 https://www.elastic.co/guide/en/kibana/current/brew.html 
- 아래 방식으로 설치 후 에러 발생했기때문에 에러부분(Kibana 3.1) 확인 후 설치 권장 


__(중요) elasticsearch을 elasticsearch-full 을 설치했다면 kibana도 kibana-full, elasticsearch을 설치했다면 kibana도 kibana__


## 1.1 Elastic Homebrew repository로 이동 후 kibana 설치

```
brew tap elastic/tap
brew install elastic/tap/kibana-full
```


## 1.2 kibana 실행 중 에러 발생
- 어느 블로그에서 본대로 설치 했지만 왜인지 모르게 오류 발생
```
[fatal][root] { Error: [mapper_parsing_exception] No handler for type [flattened] declared on field [state]
```
- Elasticsearch 와 동일한 버전이 아니라서 발생한 듯
- http://localhost:9200 에 나오는 Elasticsearch의 설정을 보면, "build_flavor" : "oss" 이기 때문에  Kibana도 oss 버전을 사용해야함!


__해결방법__
- kibana-full 을 삭제하고 그냥 kibana를 설치
```
brew list
brew remove kibana-full
brew install kibana
```

## 3 kibana 실행
- 엘라스틱서치 실행 후, 다른 터미널을 열어 키바나 실행 
- 터미널에서 아래 코드로 실행
```
kibana
```
- kibana 인터페이스
```
http://localhost:5601
```

-------
# Logstash 설치

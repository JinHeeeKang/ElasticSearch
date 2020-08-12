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
-------
# Kibana 설치
- 참조 https://www.elastic.co/guide/en/kibana/current/brew.html 
## 1. Elastic Homebrew repository로 이동
```
brew tap elastic/tap
```
## 2. kibana 설치
```
brew install elastic/tap/kibana-full
```
## 3. kibana 실행
- 엘라스틱서치 실행 후, 다른 터미널을 열어 키바나 실행 
- Homebrew package 로 설치 했기 때문에 아래 코드로 start, stop
```
brew services start elastic/tap/kibana-full
brew services stop elastic/tap/kibana-full
```
- 또는
```
kibana
```
- kibana 인터페이스
```
http://localhost:5601
```

-------
# Logstash 설치

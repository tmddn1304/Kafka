Apache Kafka는 무엇인가?데이터를 처리하는 플랫폼이다.
또다른 용어로는 이벤트 스트리밍 플랫폼이라고함

실시간으로 흐르는 이벤트스트리밍을 받아주고 그 이벤트스트리밍을 필요로 하는것으로 데이터를 전송해주는것

이벤트, 이벤트 스트림이란?

이벤트란? 비니스에서 일어나는 모든일(데이터)을 의미
ex) 웹사이트에서 무언가를 클릭하는 것
    청구서발행
    송금
    위치 정보
    GPS 좌표
이벤트는 빅데이터의 특징을 가짐
    비즈니스의 모든영역에서 광범위하게 발생
    대용량의 데이터 발생

이벤트 스트림은 연속적인 많은 데이터를 의미

아파치 카프카는 링크드인에서 개발
    하루4.5개 이상의 이벤트 스트림 처리
    하루 3000억 개 이상의 사용자 관련 이벤트 스트림 처리
    기존의 Messaging Platform(예 MQ)로 처리 불가능
    이벤트 스트림 처리를 위해 개발

### 아파치 카프카의 3가지 주요 특징

1. 이벤트 스트림을 안전하게 전송(Publish & Subscribe)
2. 이벤트 스트림을 디스크에 저장 (Write to Disk) -> 이전과 가장 구분되는 기능
3. 이벤트 스트림을 분석 및 처리
###

아파치 카프카 이름의 기원
Fraz Kafka에서 가져온 이름
쓰기에 최적한된 시스템이기 때문에 작가의 이름을 사용하는 의미가 있다고 생각

Apache Kafka의 등장

2012년 최상위 오픈소스 프로젝트로 정식 출범
80%상의 기업들이 사용

Confluent Inc 
Kafka 창시자가 만든 회사
20114년 설립

Kafka 사용 사례
Event(메시지/데이터)가 사용되는 모든곳
    메세지 시스템
    IOT 디바이스로부터 데이터수집
    애플리케이션에서 발생하는 로그 수집
    RealTime Event Stream Processing
    DB 동기화(MSA 기반의 분리된 DB간 동기화)
    실시간 ETL (배치?) 
    Spark, Flink, Storm, Hadoop과 같은 빅데이터 기술에서 사용

교통
-운전자-탑승자 매치
-도착예상시간(ETA)업데이트
-실시간 차량 진단

금융
-사기 감지, 중복거래 감지
-거래, 위험 시스템
-모바일 애플리케이션 / 고객경험

오락
-실시간 추천
-사기 감지
-In-App 구매

온라인 마켓
-실시간 재고정보
-대용량 주문의 안전한 처리(매진이라던가)

아파치 카프카의 성능
저렴한 장비로 초당 2백만 Writes

### Apache Kafka 주요요소

Producer : 메시지를 생산해서 Kafka의 Topic으로 메시지를 보내는 애플리케이션

Consumer : Topic의 메시지를 가져와서 소비(Consume)하는 애플리케이션

Consumer Group : Topic의 메시지를 사용하기 위해 협력하는 Consumer들의 집합

하나의 Consumer는 하나의 Consumer Group에 포함되며, 
Consumer Group내의 Consumer들은 협력하여 Topic의 메시지를 분산 병렬처리함


Producer와 Consumer의 분리
-> 기본동작 방식

Producer와 Consumer는 서로 알지 못하며, Producer와 Consumer는 각각 고유의 속도로 Commit Log에 Write 및 Read를 수행

다른 Consumer Group에 속한 Consumer들은 서로 관련이 없으며, Commit Log에 있는 Event(Message)를 동시에 다른 위치에서 Read 할 수 있음

![Alt text](/image/consumer.png)


![Alt text](/image/commitLog.png)
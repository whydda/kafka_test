## Kafka Test

### Kafka 설치

```shell
> brew install zookeeper

> brew install kafka

> brew cleanup kafka

# 실헹
> brew services start zookeeper
> brew services start kafka

# 서비스 리스트 
> brew services list

# os 명령어
netstat -an | grep 2181
# process kill 시 사용 (pid확인)
lsof -i :8080
lsof -i :2121

# vi server.properties
# 주석 제거하고 localhost로 변경
listeners=PLAINTEXT://localhost:9092 로 변경
```

## Kafka 기본명령어
* 토픽생성
```shell
> kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic whydda 
```


* 토픽리스트
```shell
> kafka-topics --list --bootstrap-server localhost:9092 
```


* 메시지 컨슘 (소비자)
```shell
> kafka-console-consumer --bootstrap-server localhost:9092 --topic whydda 
```

* 모든 메시지 컨슘
```shell
> kafka-console-consumer --bootstrap-server localhost:9092 --topic whydda --from-beginning
```

* 메시지 발행
```shell
> kafka-console-producer --bootstrap-server localhost:9092 --topic whydda
> Hello World
```

## 실행방법 정리 
먼저 카프라를 먼저 설치하고 메시지 발행 및 구독을 테스트 후 kafka프로젝트를 만들어 topic을 내가 만는것으로 변경하면 컨슈머들에게 메시지가 전달되는것을 확인할 수 있음.

### curl
```text
curl -X POST -H "Content-Type: application/json" \
http://localhost:8080/kafka/publish \
-d '{"author":"whydda", "content":"ㅂㅏ보야"}' -k
```

간단한 테스트 끄읏 :)
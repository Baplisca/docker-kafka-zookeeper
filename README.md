# docker-kafka-zookeeper

## How to start
```bash
git clone docker-kafka-zookeeper
cd docker-kafka-zookeeper
# memo
ipconfig getifaddr en0
# Change the value of KAFKA_ADVERTISED_HOST_NAME to the "ipconfig getifaddr en0" value
vi docker-compose.yml

docker-compose up -d
```
The Kafka server should now be listening on port 9092 on localhost

## In kafka shell
```bash
# register topic (topic name -> test)
$KAFKA_HOME/bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic test

# check current topic
$KAFKA_HOME/bin/kafka-topics.sh --list --zookeeper zookeeper:2181

# get comsumer group name
# $KAFKA_HOME/bin/kafka-consumer-groups.sh --bootstrap-server kafka:9092 --list

# produce message (stop command -> ctrl + c)
$KAFKA_HOME/bin/kafka-console-producer.sh --broker-list kafka:9092 --topic test
>ping
>pong

# comsume message
$KAFKA_HOME/bin/kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic test --from-beginning
ping
pong
Processed a total of 2 messages

```
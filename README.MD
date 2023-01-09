# GO Kafka Example

This is repository how to use kafka in golang, with shopify sarama

## Tutorial

You can see tutorial to make this repository in [here](https://medium.com/easyread/implementasi-kafka-menggunakan-golang-testing-db183e0b3c29)

## How to run

*change 10.125.75.129 to ip or host

docker network create kafka

docker run --network=kafka -p 8092:8080 --name kafka-ui -e KAFKA_CLUSTERS_0_NAME=local -e KAFKA_CLUSTERS_0_BOOTSTRAPSERVERS=10.125.75.129:9092 -d provectuslabs/kafka-ui:latest

docker run --network=kafka -d --name zookeeper -e ZOOKEEPER_CLIENT_PORT=2181 -p 2181:2181 confluentinc/cp-zookeeper:latest

docker run --network=kafka -d -p 9092:9092 --name kafka -e KAFKA_ZOOKEEPER_CONNECT=zookeeper:2181 -e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://10.125.75.129:9092 -e KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR=1 confluentinc/cp-kafka:latest

```bash
# clone this repo
git clone git@github.com:mufti1/kafka-example.git
# or
git clone https://github.com/mufti1/kafka-example.git

# Add kafka to your hosts
sudo nano /etc/hosts
127.0.0.1 kafka

cd kafka-example

# running docker compose
docker-compose up

# run consumer with command
go run cmd/consumer/main.go

# run publisher with command
go run cmd/publiser/main.go
```

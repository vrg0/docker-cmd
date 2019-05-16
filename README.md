#docker常用命令
##docker搭建kafka
docker pull wurstmeister/zookeeper
docker pull wurstmeister/kafka
docker run -d --name zookeeper -p 2181:2181 -t wurstmeister/zookeeper
docker run -d --name kafka -e KAFKA_ZOOKEEPER_CONNECT=zookeeper:2181 -e KAFKA_LISTENERS=PLAINTEXT://:9092 -e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://127.0.0.1:9092 -e KAFKA_BROKER_ID=1 -p 9092:9092 --link zookeeper:zk -t wurstmeister/kafka

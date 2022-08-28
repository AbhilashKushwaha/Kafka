1. Install Docker Desktop : https://docs.docker.com/docker-for-windows/install/
2. Make sure to restart your computer after the process is done. After the restart, Docker may ask you to install other dependencies so make sure to accept every one of them.
3. Creating a docker-compose.yml file
Code in file : 
version: '2'
services:
  zookeeper:
    image: wurstmeister/zookeeper
    ports:
      - "2181:2181"
  kafka:
    image: wurstmeister/kafka
    ports:
      - "9092:9092"
    environment:
      KAFKA_ADVERTISED_HOST_NAME: 127.0.0.1
      KAFKA_CREATE_TOPICS: "simpletalk_topic:1:1"
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
	  
4. navigate to the docker YML file and in CMD run :docker-compose up
5. Check If Kafka and Zookeeper is running uding CMD : docker ps
6. Now you can run both the project in Repo  ST_KafkaConsumer and ST_KafkaProducer
7. when both are running use POSTMan to hit the api/Kafka controller with message. Kafka will work.
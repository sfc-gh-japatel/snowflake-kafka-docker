# Snowflake Sink Connector Docker 

This repository contains a sample docker compose file that can be used to start off testing [Snowflake's Kafka connector](https://docs.snowflake.com/en/user-guide/kafka-connector.html).

It has following services:

- Zookeeper
- Kafka Broker
- Schema Registry
- Kafka Connect 
- Confluent Control Center


## Install Docker and Docker Compose 

[Install Link](https://docs.docker.com/compose/install/)


### 1 - Starting the environment

Start the environment with the following command:

```bash
docker compose -f kafka-connect.yml up --remove-orphans
```

Wait until all containers are up so you can start the testing.

### 2 - Install the connector

Open a terminal to execute the following command:

```bash
curl -X POST -H "Content-Type:application/json" -d @examples/sf-connector-example.json http://localhost:8083/connectors
```

### 4 - Check the data in Kafka

Open a terminal to execute the following command:

```bash
docker exec kafka kafka-console-consumer --bootstrap-server kafka:9092 --topic source-1 --from-beginning
```

### 5 Check Data in Snowflake Account 

Login to your account using username provided in config and verify data in the table. 

# License

This project is licensed under the [Apache 2.0 License](./LICENSE).

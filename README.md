# Real-time Change Data Capture Pipeline using Apache Kafka
This project aims to utilize Apache Kafka in the creation of a real-time Change Data Capture Pipeline. The process involves extracting data from the movie table, which holds diverse movie details, within the source database stream,
and transferring it to the sink database. Within the sink database, two tables are present: 'movie,' which replicates the source data, and 'movie_title,'which modifies the data to exhibit solely the title and release year.
Any alterations made to the data in the source database will be instantly reflected in the sink database, ensuring autonomous real-time updates.

[This project is part of Online course: Road to Data Engineer 2.0]

![Alt text](img/overview.png?raw=true "Title")


In this project, MySQL databases from GCP Cloud SQL serve as both the source and sink databases. GCP Compute Engine is utilized as a VM for hosting the project components. The Debezium CDC connector runs within a Docker container, 
serving as the source connector, while the JDBC connector, also within a Docker container, acts as the sink connector. Real-time data processing is achieved using KSQL streams

## Files in this project
- [docker-compose.yml](src/docker-compose.yml) -> running multi-container Docker setup including Zookeeper, a broker, Schema Registry, Control Center, and ksqlDB 
- [mysql-source.json](src/mysql-source.json) -> configuration file for setup source connector of kafka with debezium CDC connector.
- [mysql-sink-kafka.json](src/mysql-sink-kafka.json) -> configuration file for setup source connector of kafka with  JDBC connector.
- [mysql-sink-ksql.json](src/mysql-sink-ksql.json) -> configuration file for setup source connector of kafka kstream topic with JDBC connector
- [CLI.txt](src/CLI.txt) -> Command line Interface that use in project
- [debezium-debezium-connector-mysq](src/connectors/debezium-debezium-connector-mysql) ->  debezium-connector file
- [confluentinc-kafka-connect-jdbc](src/connectors/confluentinc-kafka-connect-jdbc) -> JDBC-connector file
- [mysqlsource/movies.sql](src/mysqlsource/movies.sql) -> SQL script for create movie table of source database
- [mysqlsink/movies.sql](src/mysqlsink/movies.sql) -> SQL script for create movie table of sink database 

## Example data in Source & Sink Database

![Alt text](img/ex_data.png?raw=true "Title")


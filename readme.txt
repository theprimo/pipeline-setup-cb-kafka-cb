# Read a couchbase source bucket doc, transform it, publish to kafka, finally transformed doc push it to couchbase target bucket 

#source connector receives records from an upstream system (CB source) and transforms the record according 
#to the transformation rules and pushes the transformed record to the downstream system (Kafka target)

#sink connector receives records from an upstream system (Kafka target) and publishes the record
#to the downstream system (CB target)

# Couchbase source bucket - transform record - Kafka target - Couchbase target bucket
# folder - kafka-connect-couchbase-3.4.8

I. This kafka-connect-couchbase-3.4.8 folder contains below 2 folders & 2 files
1. config  - config files
2. jars    - dependency jar files 
3. kafka-cmds.txt  - kafka cb connect commands
4. readme.txt  - setup guide


II. config folder contains below
1. pulse-cb-sink.properties - couchbase source to kafka properties
2. pulse-cb-source.properties - kafka to couchbase target properties
3. connect-standalone.properties - kafka connect properties
4. connect-standalone.sh - script to run the connectors command


III. jars folder contains 18 jars below
1.connect-api-2.5.0.jar
2.connect-transforms-2.5.0.jar
3.core-io-1.7.13.jar
4.custom-transform-5.0.0.jar
5.dcp-client-0.26.0.jar
6.HdrHistogram-2.1.11.jar
7.java-client-2.7.13.jar
8.javax.ws.rs-api-2.1.1.jar
9.kafka-clients-2.5.0.jar
10.kafka-connect-couchbase-3.4.8.jar
11.LatencyUtils-2.0.3.jar
12.lz4-java-1.7.1.jar
13.micrometer-core-1.3.0.jar
14.opentracing-api-0.31.0.jar
15.rxjava-1.3.8.jar
16.slf4j-api-1.7.30.jar
17.snappy-java-1.1.7.3.jar
18.zstd-jni-1.4.4-7.jar


IV. setup & how to run
1. copy the folder kafka-connect-couchbase-3.4.8 to target kafka pod or container
   (ex path: /opt/kafka/kafka-connect-couchbase-3.4.8)
2. goto config folder, make changes accordinglly to all 3 properties fiels
3. from the config folder, run below command
   (ex path: /opt/kafka/kafka-connect-couchbase-3.4.8/config)
   connect-standalone.sh connect-standalone.properties pulse-cb-source.properties pulse-cb-sink.properties
4. observe cdc event changes from couchbase source to couchbase target



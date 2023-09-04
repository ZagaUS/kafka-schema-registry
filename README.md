# Setting up Kafka Schema Registry
## 1. Setting up Kafka

> oc apply -f ./kafka.yaml

## 2. Setting up Kafka Connect
 [NOTE] AMQ Stream Kafka Connect CRD image does not support the mongodb sink connector. In order to use the mongodb sink connector extend the amq-streams/kafka-34-rhel8:2.4.0-6(current latest) image with the mongodb sink connector jar file downloaded from the [official site ](https://www.confluent.io/hub/mongodb/kafka-connect-mongodb) and configure this custom image in the kafka connect CRD.

**Step 1:** 
Create a Docker file and push it to the container registry.

> docker build -t mongo-plugin .

**Step 2:**
Create a Kafka connect file with the custom image and apply it to the Openshift 

> oc apply -f ./kafka-connect.yaml




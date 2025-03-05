# kafka-dr-setup : active-active 


**Active-Active Kafka Disaster Recovery Setup with Strimzi**
This guide provides step-by-step instructions for setting up an active-active disaster recovery (DR) setup for Apache Kafka using the Strimzi operator on OpenShift. The setup ensures bidirectional data replication between two Kafka clusters, enabling both clusters to serve clients simultaneously.

**Prerequisites**
Two OpenShift clusters (primary and DR) with network connectivity.

Strimzi operator installed on both clusters.

Persistent storage configured for Kafka topics and data.

Network access between Kafka brokers in both clusters.

Steps


### Deploy Kafka clusters on both the primary and DR sites using Strimzi custom resources (CRs).


#### Primary Cluster

1. Create a Kafka CR on the primary cluster:

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/primary-cluster/kafka-primary-cluster.yaml#L1-L67

2. Create a user for Kafka primary cluster:

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/primary-cluster/primary-cluster-user2.yaml#L1-L29

3. Deploy Kafka UI for primary cluster

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/primary-cluster/primay-kafka-ui.yaml#L1-L78

#### Secondary Cluster

1. Create a Kafka CR on the secondary cluster:

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/secondary-cluster/kafka-secondary-cluster.yaml#L1-L67

2. Create a user for Kafka secondary cluster:

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/secondary-cluster/secondary-cluster-user2.yaml#L1-L29

3. Deploy Kafka UI for primary cluster

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/secondary-cluster/secondary-kafka-ui.yaml#L1-L78


### Deploy mirror Maker 2 on Secondary Cluster.

#### Setup primary cluster User secret on secnodary [DR] ocp 

1. Create the Kafka User secret from primary cluster into the secondary cluster.

2. Create the kafka-cluster-ca-cert for primary cluster into the secondary clusster.



### Deploy the mirror maker2 in the secondary cluster 


.1 Use thefollwoing CR to deploy mirrormaker2


https://github.com/abhishekvishnoi/kafka-dr-setup/blob/b18f00479d45a4c4ac85a078bdf47aacf38aaa81/DC-DR/secondary-cluster/kafka-mirror-maker-2-tls.yaml#L1-L58
# kafka-dr-setup : active-active 


**Active-Active Kafka Disaster Recovery Setup with Strimzi**
This guide provides step-by-step instructions for setting up an active-active disaster recovery (DR) setup for Apache Kafka using the Strimzi operator on OpenShift. The setup ensures bidirectional data replication between two Kafka clusters, enabling both clusters to serve clients simultaneously.

**Prerequisites**
Two OpenShift clusters (primary and DR) with network connectivity.

Strimzi operator installed on both clusters.

Persistent storage configured for Kafka topics and data.

Network access between Kafka brokers in both clusters.

Steps
1. Deploy Kafka Clusters
   Deploy Kafka clusters on both the primary and DR sites using Strimzi custom resources (CRs).

1.1. Primary Cluster

1.1.1. Create a Kafka CR on the primary cluster:

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/primary-cluster/kafka-primary-cluster.yaml#L1-L67

1.1.2. Create a user for Kafka primary cluster:

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/primary-cluster/primary-cluster-user2.yaml#L1-L29

1.1.3. Deploy Kafka UI for primary cluster

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/primary-cluster/primay-kafka-ui.yaml#L1-L78

1.2. Secondary Cluster

1.2.1. Create a Kafka CR on the secondary cluster:

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/secondary-cluster/kafka-secondary-cluster.yaml#L1-L67

1.2.2. Create a user for Kafka secondary cluster:

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/secondary-cluster/secondary-cluster-user2.yaml#L1-L29

1.2.3. Deploy Kafka UI for primary cluster

https://github.com/abhishekvishnoi/kafka-dr-setup/blob/2bbebfe5f1114a866f88b3323bf5ac00fd266cae/DC-DR/secondary-cluster/secondary-kafka-ui.yaml#L1-L78
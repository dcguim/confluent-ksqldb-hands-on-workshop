# Create Confluent Cloud clusters

This script create cluster with ksqlDB Apps based on the attendees.txt file. Each entry will get an entry.
## Prerequisites
* Confluent Cloud Org
* Environment ksqldb-workshop have to created before
* ccloud cli installed
* Your Confluent Cloud Org-Organization need RBAC enabled. If this is not done, please go [back](../labs/00_Setup-ccloud.md) and setup the Confluent manually.
* env-vars file have to be set with correct information
    * `export XX_CCLOUD_ENV=env-ID`  sset the ID of the ksqlDb-workshop environment
    * `export XX_CCLOUD_EMAIL= your email` set your login Email address to Confluent Cloud
    * `export XX_CCLOUD_PASSWORD=your password` set your password for Confluent Cloud user
    * `export XX_CCLOUD_CLUSTERNAME=ksqldb` clustername of confluent cloud cluster
    * `export XX_CCLOUD_ATTENDEES=./attendees.txt` name of the attendee list, here one email per line.
    * `export XX_CLOUD_PROVIDER=aws` cloud provider where the cluster should be created
    * `export XX_CLOUD_SRREGION=us` region in cloud provider for Schema Registry
    * `export XX_CLOUD_REGION=us-east-2` region in cloud provider for cluster
    * `export XX_CLOUD_TYPE=basic` cluster type.
    * `export XX_CLOUD_RBAC=1` this flag is used for RBAC, do not change

## Create Clusters
Create for each attendee in `attendees.txt` a cluster in Confluent Cloud. Max 20 clusters can be created. We have a limit of 20 ksqlDB Apps per environment. If you need more, contact the Confluent Support.
A good `attendee.txt` setup would look like this, e.g. for 4 users:
```bash
mustermann+rabc001@mustermann.io
mustermann+rbac002@mustermann.io
mustermann+rbac003@mustermann.io
mustermann+rbac004@mustermann.io
```

Then start the cluster executions:
```bash
cd ccloud
./00_create_ccloudclusters.sh
```
For each attendee you will get properties file and an entry with all relevant information in `attendees_cluster.txt`.
## Destroy clusters
Destroy the confluent cloud environment including all clusters:
```bash
cd ccloud
./02_drop_ccloudcluster.sh
```
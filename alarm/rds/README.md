# RDS Alarms

- ReadLatency
  - Threshold : 1500(ms)
- WriteLatency
  - Threshold : 1500(ms)

## Cluster/Instance Alarm

``` shell
RDS_CLUSTER_NAME="[RDS CLUSTER NAME]"
LATENCEY_THRESHOLD="1500"     # Default is 1500ms.
CLOUDFORMATION_STACK_NAME="[CLOUDFORMATION STACK NAME]"
CLOUDFORMATION_TAG="[CLOUDFORMATION TAG LIKE 'project=production']"
REGION="[REGION CODE]"

aws cloudformation deploy \
    --template-file ./rds-cluster-alarm.yaml \
    --stack-name $CLOUDFORMATION_STACK_NAME \
    --parameter-overrides \
        RdsClusterName=$RDS_CLUSTER_NAME \
        LatencyThreshold=$LATENCEY_THRESHOLD \
    --tags $CLOUDFORMATION_TAG \
    --region $REGION
```

## Event Subscription Notification Alarm


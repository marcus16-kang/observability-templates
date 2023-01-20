# DynamoDB Alarms

- GetLatency
  - Threshold : 1500(ms)
- PutLatency
  - Threshold : 1500(ms)
- QueryLatency
  - Threshold : 1500(ms)
- ScanLatency
  - Threshold : 1500(ms)
- ReadThrottle
  - Threshold : 1000(count)
- WriteThrottle
  - Threshold : 1000(count)

``` shell
DYNAMODB_TABLE_NAME="[DYNAMODB TABLE NAME]"
LATENCEY_THRESHOLD="1500"   # Default is 1500ms.
THROTTLE_THRESHOLD="1000.0" # Default is 1000 count.
CLOUDFORMATION_STACK_NAME="[CLOUDFORMATION STACK NAME]"
CLOUDFORMATION_TAG="[CLOUDFORMATION TAG LIKE 'project=production']"
REGION="[REGION CODE]"

aws cloudformation deploy \
    --template-file ./dynamodb-alarm.yaml \
    --stack-name $CLOUDFORMATION_STACK_NAME \
    --parameter-overrides \
        DynamoDBTableName=$DYNAMODB_TABLE_NAME \
        LatencyThreshold=$LATENCEY_THRESHOLD \
        ThrottleThreshold=$THROTTLE_THRESHOLD \
    --tags $CLOUDFORMATION_TAG \
    --region $REGION
```
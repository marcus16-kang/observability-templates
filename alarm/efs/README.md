# EFS Alarms

- DataReadIOBytes
  - Threshold : 512MB(536870912B)
- DataWriteIOBytes
  - Threshold : 512MB(536870912B)

``` shell
EFS_FILE_SYSTEM_ID="[RDS CLUSTER NAME]"
BYTES_THRESHOLD="536870912"     # Default is 536870912B(512MB).
CLOUDFORMATION_STACK_NAME="[CLOUDFORMATION STACK NAME]"
CLOUDFORMATION_TAG="[CLOUDFORMATION TAG LIKE 'project=production']"
REGION="[REGION CODE]"

aws cloudformation deploy \
    --template-file ./efs-alarm.yaml \
    --stack-name $CLOUDFORMATION_STACK_NAME \
    --parameter-overrides \
        EfsFileSystemId=$EFS_FILE_SYSTEM_ID \
        BytesThreshold=$LATENCEY_THRESHOLD \
    --tags $CLOUDFORMATION_TAG \
    --region $REGION
```
# Application Load Balancer Alarms

- RequestCountAnomaly
  - Anomaly Value
- HTTPCode_Target_5XX_Count
  - Threshold : 100(count)
- TargetResponseTime
  - Threshold : 2.0(s)

``` shell
ALB_NAME="[APPLICATION LOAD BALANCER NAME]"
TARGET_COUNT_THRESHOLD="100"            # Default is 100(count)
TARGET_RESPONSE_TIME_THRESHOLD="2.0"    # Default is 2.0(s)
CLOUDFORMATION_STACK_NAME="[CLOUDFORMATION STACK NAME]"
CLOUDFORMATION_TAG="[CLOUDFORMATION TAG LIKE 'project=production']"
REGION="[REGION CODE]"

ALB_ARN=$(aws elbv2 describe-load-balancers \
    --names $ALB_NAME \
    --query 'LoadBalancers[0].LoadBalancerArn' \
    --region $REGION \
    --output text | \
    cut -d '/' -f2-4)

aws cloudformation deploy \
    --template-file ./alb-alarm.yaml \
    --stack-name $CLOUDFORMATION_STACK_NAME \
    --parameter-overrides \
        ApplicationLoadBalancerArn=$ALB_ARN \
        TargetCountThreshold=$TARGET_COUNT_THRESHOLD \
        TargetResponseThreshold=$TARGET_RESPONSE_TIME_THRESHOLD \
    --tags $CLOUDFORMATION_TAG \
    --region $REGION
```
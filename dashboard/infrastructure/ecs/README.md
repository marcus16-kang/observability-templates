# ECS Infrastructure Monitoring

## Each Instances' CPU Utilization

```
SEARCH('{ECS/ContainerInsights,ClusterName} MetricName=\"instance_cpu_utilization\" ClusterName=\"<CLUSTER NAME>\"', 'Average', 60)
```

![assets/dashboard/infrastructure/ecs/01.png](../../../assets/dashboard/infrastructure/ecs/01.png)

## Each Instances' Memory Utilization

```
SEARCH('{ECS/ContainerInsights,ClusterName,ContainerInstanceId,InstanceId} MetricName=\"instance_memory_utilization\" ClusterName=\<CLUSTER NAME>\"', 'Average', 60)
```

![assets/dashboard/infrastructure/ecs/02.png](../../../assets/dashboard/infrastructure/ecs/02.png)

## Each Instances' 
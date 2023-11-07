# Kafka-rest-proxy

Запуск Kafka в Docker:
```
docker-compose up -d
```

Получение информации о локальном кластере:
```
Command:
curl http://localhost:8082/v3/clusters

Response:
{
  "kind": "KafkaClusterList",
  "metadata": {
    "self": "http://rest-proxy:8082/v3/clusters",
    "next": null
  },
  "data": [
    {
      "kind": "KafkaCluster",
      "metadata": {
        "self": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow",
        "resource_name": "crn:///kafka=fl_XwzLmTYeF6lYulvfWow"
      },
      "cluster_id": "fl_XwzLmTYeF6lYulvfWow",
      "controller": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/brokers/1"
      },
      "acls": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/acls"
      },
      "brokers": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/brokers"
      },
      "broker_configs": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/broker-configs"
      },
      "consumer_groups": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/consumer-groups"
      },
      "topics": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics"
      },
      "partition_reassignments": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/-/partitions/-/reassignment"
      }
    }
  ]
}
```
Идентификатор кластера в Response `fl_XwzLmTYeF6lYulvfWow`.

Получение списка topic'ов:
```
Command:
curl http://localhost:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics

Response:
{
  "kind": "KafkaTopicList",
  "metadata": {
    "self": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics",
    "next": null
  },
  "data": [
    {
      "kind": "KafkaTopic",
      "metadata": {
        "self": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-command",
        "resource_name": "crn:///kafka=fl_XwzLmTYeF6lYulvfWow/topic=_confluent-command"
      },
      "cluster_id": "fl_XwzLmTYeF6lYulvfWow",
      "topic_name": "_confluent-command",
      "is_internal": false,
      "replication_factor": 1,
      "partitions_count": 1,
      "partitions": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-command/partitions"
      },
      "configs": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-command/configs"
      },
      "partition_reassignments": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-command/partitions/-/reassignment"
      },
      "authorized_operations": []
    },
    {
      "kind": "KafkaTopic",
      "metadata": {
        "self": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-metrics",
        "resource_name": "crn:///kafka=fl_XwzLmTYeF6lYulvfWow/topic=_confluent-metrics"
      },
      "cluster_id": "fl_XwzLmTYeF6lYulvfWow",
      "topic_name": "_confluent-metrics",
      "is_internal": false,
      "replication_factor": 1,
      "partitions_count": 12,
      "partitions": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-metrics/partitions"
      },
      "configs": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-metrics/configs"
      },
      "partition_reassignments": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-metrics/partitions/-/reassignment"
      },
      "authorized_operations": []
    },
    {
      "kind": "KafkaTopic",
      "metadata": {
        "self": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-telemetry-metrics",
        "resource_name": "crn:///kafka=fl_XwzLmTYeF6lYulvfWow/topic=_confluent-telemetry-metrics"
      },
      "cluster_id": "fl_XwzLmTYeF6lYulvfWow",
      "topic_name": "_confluent-telemetry-metrics",
      "is_internal": false,
      "replication_factor": 1,
      "partitions_count": 12,
      "partitions": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-telemetry-metrics/partitions"
      },
      "configs": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-telemetry-metrics/configs"
      },
      "partition_reassignments": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent-telemetry-metrics/partitions/-/reassignment"
      },
      "authorized_operations": []
    },
    {
      "kind": "KafkaTopic",
      "metadata": {
        "self": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent_balancer_api_state",
        "resource_name": "crn:///kafka=fl_XwzLmTYeF6lYulvfWow/topic=_confluent_balancer_api_state"
      },
      "cluster_id": "fl_XwzLmTYeF6lYulvfWow",
      "topic_name": "_confluent_balancer_api_state",
      "is_internal": false,
      "replication_factor": 1,
      "partitions_count": 1,
      "partitions": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent_balancer_api_state/partitions"
      },
      "configs": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent_balancer_api_state/configs"
      },
      "partition_reassignments": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_confluent_balancer_api_state/partitions/-/reassignment"
      },
      "authorized_operations": []
    },
    {
      "kind": "KafkaTopic",
      "metadata": {
        "self": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_schemas",
        "resource_name": "crn:///kafka=fl_XwzLmTYeF6lYulvfWow/topic=_schemas"
      },
      "cluster_id": "fl_XwzLmTYeF6lYulvfWow",
      "topic_name": "_schemas",
      "is_internal": false,
      "replication_factor": 1,
      "partitions_count": 1,
      "partitions": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_schemas/partitions"
      },
      "configs": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_schemas/configs"
      },
      "partition_reassignments": {
        "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/_schemas/partitions/-/reassignment"
      },
      "authorized_operations": []
    }
  ]
}
```

Создание topic'а с именем my_topic:
```
Command:
curl -X POST -H "Content-Type:application/json" -d '{"topic_name":"my_topic"}' \
       http://localhost:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics

Response:
{
  "kind": "KafkaTopic",
  "metadata": {
    "self": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/my_topic",
    "resource_name": "crn:///kafka=fl_XwzLmTYeF6lYulvfWow/topic=my_topic"
  },
  "cluster_id": "fl_XwzLmTYeF6lYulvfWow",
  "topic_name": "my_topic",
  "is_internal": false,
  "replication_factor": 1,
  "partitions_count": 1,
  "partitions": {
    "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/my_topic/partitions"
  },
  "configs": {
    "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/my_topic/configs"
  },
  "partition_reassignments": {
    "related": "http://rest-proxy:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/my_topic/partitions/-/reassignment"
  },
  "authorized_operations": []
}
```

Запись в my_topic:
```
Command:
curl -X POST -H "Content-Type: application/json" \
       -d '{"value":{"type":"JSON","data":{"name":"my_record"}}}' \
       http://localhost:8082/v3/clusters/fl_XwzLmTYeF6lYulvfWow/topics/my_topic/records

Response:
{
  "error_code": 200,
  "cluster_id": "fl_XwzLmTYeF6lYulvfWow",
  "topic_name": "my_topic",
  "partition_id": 0,
  "offset": 0,
  "timestamp": "2023-11-07T05:33:27.569Z",
  "value": {
    "type": "JSON",
    "size": 20
  }
}
```

Создание consumer'а:
```
Command:
curl -X POST -H "Content-Type: application/vnd.kafka.v2+json" -H "Accept: application/vnd.kafka.v2+json" \
       -d '{"name": "my_consumer_instance", "format": "json", "auto.offset.reset": "earliest"}' \
       http://localhost:8082/consumers/my_consumer

Response:
{
  "instance_id": "my_consumer_instance",
  "base_uri": "http://rest-proxy:8082/consumers/my_consumer/instances/my_consumer_instance"
}
```

Подписание consumer'а на topic с именем my_topic:
```
Command:
curl -X POST -H "Content-Type: application/vnd.kafka.v2+json" \
       -d '{"topics":["my_topic"]}' \
      http://localhost:8082/consumers/my_consumer/instances/my_consumer_instance/subscription

Response:
# No content in response
```

Получение данных из my_topic:
```
Command:
curl -X GET -H "Accept: application/vnd.kafka.json.v2+json" \
       http://localhost:8082/consumers/my_consumer/instances/my_consumer_instance/records

Response:
[
  {
    "topic": "my_topic",
    "key": null,
    "value": {
      "name": "my_record"
    },
    "partition": 0,
    "offset": 0
  }
]
```

Удаление consumer'а:
```
Command:
curl -X DELETE -H "Accept: application/vnd.kafka.v2+json" \
       http://localhost:8082/consumers/my_consumer/instances/my_consumer_instance

Response:
# No content in response
```

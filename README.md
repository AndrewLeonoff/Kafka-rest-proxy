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
  {"kind":"KafkaClusterList",
   "metadata":{"self":"http://localhost:8082/v3/clusters","next":null},
   "data":[
    {"kind":"KafkaCluster",
     "metadata":{"self":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q",
     "resource_name":"crn:///kafka=xFhUvurESIeeCI87SXWR-Q"},
     "cluster_id":"xFhUvurESIeeCI87SXWR-Q",
     "controller":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/brokers/0"},
     "acls":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/acls"},
     "brokers":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/brokers"},
     "broker_configs":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/broker-configs"},
     "consumer_groups":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/consumer-groups"},
     "topics":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics"},
     "partition_reassignments":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/-/partitions/-/reassignment"}
    }
   ]
  }
```
Идентификатор кластера в Response `xFhUvurESIeeCI87SXWR-Q`.

Получение списка topic'ов:
```
Command:
curl http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics

Response:
  {"kind":"KafkaTopicList",
   "metadata":{"self":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics","next":null},
   "data":[
    {"kind":"KafkaTopic",
     "metadata":{"self":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/jsontest",
     "resource_name":"crn:///kafka=xFhUvurESIeeCI87SXWR-Q/topic=jsontest"},
     "cluster_id":"xFhUvurESIeeCI87SXWR-Q",
     "topic_name":"jsontest",
     "is_internal":false,
     "replication_factor":1,
     "partitions_count":1,
     "partitions":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/jsontest/partitions"},
     "configs":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/jsontest/configs"},
     "partition_reassignments":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/jsontest/partitions/-/reassignment"}
    }
   ]
  }
```

Создание topic'а с именем jsontest:
```
Command:
curl -X POST -H "Content-Type:application/json" -d '{"topic_name":"jsontest"}' \
       http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics

Response:
  {"kind":"KafkaTopic",
   "metadata":{"self":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/jsontest",
   "resource_name":"crn:///kafka=xFhUvurESIeeCI87SXWR-Q/topic=jsontest"},
   "cluster_id":"xFhUvurESIeeCI87SXWR-Q",
   "topic_name":"jsontest",
   "is_internal":false,
   "replication_factor":1,
   "partitions_count":1,
   "partitions":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/jsontest/partitions"},
   "configs":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/jsontest/configs"},
   "partition_reassignments":{"related":"http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/jsontest/partitions/-/reassignment"}
  }
```

Запись в jsontest:
```
Command:
curl -X POST -H "Content-Type: application/json" \
       -d '{"value":{"type":"JSON","data":{"name":"testUser"}}}' \
       http://localhost:8082/v3/clusters/xFhUvurESIeeCI87SXWR-Q/topics/jsontest/records

Response:
  {"error_code":200,
   "cluster_id":"xFhUvurESIeeCI87SXWR-Q",
   "topic_name":"jsontest",
   "partition_id":0,
   "offset":0,
   "timestamp":"2023-03-09T14:07:23.592Z",
   "value":{"type":"JSON","size":19}
  }
```

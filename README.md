# elastic-stack-throughput-aggregator

## Target resources

### Elasticsearch

### Logstash

Via [Monitoring APIs](https://www.elastic.co/guide/en/logstash/current/monitoring.html)

``` sh
$ curl -s 'logstash.host:9600/_node/stats/pipeline' | jq .pipeline.events
{
  "duration_in_millis": 1251249,
  "in": 2988838,
  "filtered": 2988838,
  "out": 2988838
}
```

### Filebeat
# elastic-stack-throughput-aggregator

## Target resources

### Elasticsearch

Via [Indices APIs](https://www.elastic.co/guide/en/elasticsearch/reference/current/indices-stats.html)

``` sh
$ curl -s '192.168.50.52:9200/httpd_access_log-2017.02.16/_stats/indexing' | jq '.indices["httpd_access_log-2017.02.16"].primaries'
{
  "indexing": {
    "index_total": 3939530,
    "index_time_in_millis": 491992,
    "index_current": 0,
    "index_failed": 0,
    "delete_total": 0,
    "delete_time_in_millis": 0,
    "delete_current": 0,
    "noop_update_total": 0,
    "is_throttled": false,
    "throttle_time_in_millis": 0
  }
}
```

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

Required enabling `-httpprof`

``` sh
$ curl -s '192.168.50.53:8888/debug/vars' | jq '.["publish.events"]'
133
```
# ElasticStackExample

https://www.elastic.co/guide/en/elastic-stack-get-started/current/get-started-docker.html

## Doker Version

```
 % docker -v 
Docker version 19.03.5, build 633a0ea
```

## Docker pull and run Elasticsearch 

pull
```
% docker pull docker.elastic.co/elasticsearch/elasticsearch:7.10.0
```

run
```
 % docker run -d --rm -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.10.0
```

## Docker pull and run Kibana

pull
```
% docker pull docker.elastic.co/kibana/kibana:7.10.0
```

run
```
% docker run -d --rm --link baca170ef8cb:elasticsearch -p 5601:5601 docker.elastic.co/kibana/kibana:7.10.0
```
baca170ef8cbはElasticsearchのコンテナID

## ブラウザでKibanaにアクセス

http://localhost:5601 
ブラウザでKibanaにアクセス可能になる

## Elasticsearchにデータを入れてみる

post
```
% cat test.json 
{
    "user" : "Taro",
    "post_date" : "2009-11-15T14:12:12",
    "message" : "trying out Elastic Search"
}
% curl -XPOST -H "Content-type: application/json" http://localhost:9200/my_index/data/ -d @test.json
```






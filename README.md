# pi-elk


```bash
curl -sSL https://get.docker.com | sh
```

```bash
docker network create elastic
```

https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html

```bash
docker run --name es01 --net elastic -p 9200:9200 -it docker.elastic.co/elasticsearch/elasticsearch:8.7.1
```

https://www.elastic.co/guide/en/kibana/current/docker.html

```bash
docker run --name es-node01 --net elastic -p 9200:9200 -p 9300:9300 -t docker.elastic.co/elasticsearch/elasticsearch:8.7.1
```

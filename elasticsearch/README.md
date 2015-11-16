# Build Elasticsearch image
```sh
$ docker build -t es .
```

# Run Elasticsearch Container
```sh
$ docker run -d -p 9200:9200 -p 9300:9300 -v /home/docker/elasticsearch:/data es
```

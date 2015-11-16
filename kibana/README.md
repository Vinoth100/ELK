# Build Kibana image
```sh
$ docker build -t kib .
```

# Run Kibana Container
```sh
$ docker run -d -p 5601:5601 -e ESURL=http://192.168.1.112:9200 kib

```

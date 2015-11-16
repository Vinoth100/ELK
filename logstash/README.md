# Build Logstash image
```sh
$ docker build -t ls .
```

# Run Logstash Container
```sh
$ docker run -d -v /etc/logstash:/data ls
```

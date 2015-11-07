FROM ubuntu:14.04
RUN apt-get --assume-yes install software-properties-common && \
 add-apt-repository --yes ppa:webupd8team/java && \ 
 apt-get --assume-yes update && \
 echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections && \
 apt-get --assume-yes install oracle-java8-installer  && \
 wget -qO - https://packages.elasticsearch.org/GPG-KEY-elasticsearch | sudo apt-key add - && \
 echo "deb http://packages.elasticsearch.org/logstash/1.5/debian stable main" | sudo tee -a /etc/apt/sources.list && \
 apt-get update && sudo apt-get install logstash && \
 ln -s /lib/x86_64-linux-gnu/libcrypt.so.1 /usr/lib/x86_64-linux-gnu/libcrypt.so 
ADD config/logstash.conf /etc/logstash/logstash.conf
VOLUME ["/data"]
ENTRYPOINT ["/opt/logstash/bin/logstash","-f","/etc/logstash/logstash.conf"]


# Build Logstash image from ubuntu 14.04
FROM ubuntu:14.04

# Install Java 8
RUN apt-get --assume-yes install software-properties-common && \
 add-apt-repository --yes ppa:webupd8team/java && \ 
 apt-get --assume-yes update && \
 echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections && \
 apt-get --assume-yes install oracle-java8-installer  

# Install logstash 1.5 and create a soft link to the library
RUN wget -qO - https://packages.elasticsearch.org/GPG-KEY-elasticsearch | sudo apt-key add - && \
 echo "deb http://packages.elasticsearch.org/logstash/1.5/debian stable main" | sudo tee -a /etc/apt/sources.list && \
 apt-get update && sudo apt-get install logstash && \
 ln -s /lib/x86_64-linux-gnu/libcrypt.so.1 /usr/lib/x86_64-linux-gnu/libcrypt.so 

# Add the logstash.conf
ADD config/logstash.conf /etc/logstash/logstash.conf

#Mount /data as Volume
VOLUME ["/data"]

# Start the logstash as entrypoint
ENTRYPOINT ["/opt/logstash/bin/logstash","-f","/etc/logstash/logstash.conf"]


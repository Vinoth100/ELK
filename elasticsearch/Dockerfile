# This Docker file is to build elastic search from base ubuntu image
FROM ubuntu

# Install Java 8
RUN apt-get --assume-yes install software-properties-common && \
 add-apt-repository --yes ppa:webupd8team/java && \ 
 apt-get --assume-yes update && \
 echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections && \
 apt-get --assume-yes install oracle-java8-installer 

# Install elasticsearch 1.7
RUN wget -qO - https://packages.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add - && \
echo "deb http://packages.elastic.co/elasticsearch/1.7/debian stable main" | sudo tee -a /etc/apt/sources.list.d/elasticsearch-1.7.list && \
sudo apt-get update && sudo apt-get install elasticsearch

# Path for mounting Volume
VOLUME ["/data"]

# Entry point to begin the elasticsearch service
# Provided elastic search default path to expect data and log files.
ENTRYPOINT ["/usr/share/elasticsearch/bin/elasticsearch","-Des.default.path.conf=/data","-Des.default.path.logs=/data"]

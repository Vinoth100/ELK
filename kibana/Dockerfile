# Install Kibana 4.1.2 from ubuntu base image

FROM ubuntu:14.04

# Install Java 8
RUN apt-get --assume-yes install software-properties-common && \
 add-apt-repository --yes ppa:webupd8team/java && \ 
 apt-get --assume-yes update && \
 echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections && \
 apt-get --assume-yes install oracle-java8-installer 

# Install Kibana 4.1.2
RUN  wget https://download.elastic.co/kibana/kibana/kibana-4.1.2-linux-x64.tar.gz && \
tar -xvf kibana-4.1.2-linux-x64.tar.gz

# Copy the extracted folder to /opt/kibana

RUN mkdir /opt/kibana && \
cp -R kibana-4.1.2-linux-x64/* /opt/kibana && \
rm -rf kibana-4.1.2-linux-x64 && \
rm kibana-4.1.2-linux-x64.tar.gz

# Make the kibana port accessible from outside
EXPOSE 5601

ADD config/kibana.yml /opt/kibana/config/kibana.yml

# Entry point to begin the kibana service
ENTRYPOINT ["/opt/kibana/bin/kibana","-e","http://192.168.1.112:9200"]


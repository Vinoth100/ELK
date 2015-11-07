# ELK
This is a project for freshers who wants to learn ELK stack along with creating docker images and running each stack in a container

Logstash: 

Step 1: Create a docker image for logstash from file logstash directory where Dockerfile is present
docker build -t ls .

Step 2: Run the container as daemon and provide the mount path
docker run -d -v /etc/logstash:/data ls

Step 3:Create a  new file  my.log file at the mounted volume /etc/logstash
and paste the below lines
1438387494.776675940 - pid:10278 - Task123 [key1=1,key2=2,key3=3] - some message12345
1438387494.776675940 - pid:10278 - Task123 [key1=1,key2=2,key3=3] - some message12346

Step 4: Get the docker job id using "docker ps"
command and see the container logs "docker logs jobid"


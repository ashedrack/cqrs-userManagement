#1. Java Development Kit (JDK)

OpenJDK:
https://openjdk.java.net/install/

Oracle JDK:
https://www.oracle.com/java/technologies/javase-downloads.html

Once installed, check Java version:
> java -version

#2. Maven

Download from:
https://maven.apache.org/download.cgi

Once installed, check Maven version:
> mvn -v OR mvn --version

#3. IDE or Code Editor

IntelliJ IDEA:
https://www.jetbrains.com/idea/download/

NetBeans IDE:
https://netbeans.apache.org/download/index.html

Eclipse:
https://www.eclipse.org/downloads/

VS Code:
https://code.visualstudio.com/download

#4. Postman

Download from:
https://www.postman.com/downloads/

#5. Docker

Download for Mac or Windows:
https://www.docker.com/products/docker-desktop

Download for Linux Ubuntu:
https://docs.docker.com/engine/install/ubuntu/

Download for Linux Debian:
https://docs.docker.com/engine/install/debian/

Download for Linux CentOS:
https://docs.docker.com/engine/install/centos/

Download for Linux Fedora:
https://docs.docker.com/engine/install/fedora/

Once installed, check Docker version:
> docker --version

#6. Create Docker Network - springbankNet (We will put all our containers in the same network)

docker network create --attachable -d overlay springbankNet

#7. Axon Platform

Run in Docker:
docker run -d --name axon-server \
-p 8024:8024 -p 8124:8124 \
--network springbankNet \
--restart always axoniq/axonserver:latest

Once installed, check if running:
http://localhost:8024/

#8. MongoDB

Run in Docker:
docker run -it -d --name mongo-container \
-p 27017:27017 --network springbankNet \
--restart always \
-v mongodb_data_container:/data/db \
mongo:latest

Download Client Tools – Robo 3T:
https://robomongo.org/download

#9. MySQL

Run in Docker:
docker run -it -d --name mysql-container \
-p 3306:3306 --network springbankNet \
-e MYSQL_ROOT_PASSWORD=springbankRootPsw \
--restart always \
-v mysql_data_container:/var/lib/mysql  \
mysql:latest

Client tools in Docker – Adminer:
docker run -it -d --name adminer \
-p 8080:8080 --network springbankNet \
-e ADMINER_DEFAULT_SERVER=mysql-container \
--restart always adminer:latest




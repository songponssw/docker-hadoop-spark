Dockerfile bases on https://github.com/sequenceiq/docker-spark and https://github.com/sequenceiq/docker-hadoop-build

Run Hadoop Container 
	docker run --name hadoop-node --rm -it -p 8088:8088 -p 8042:8042 -p 4040:4040 cyborgcat/docker-hadoop-spark:1.0.0 bash

Run Hadoop+Postgresql
	docker-compose up -d 

Access to Hadoop container
	docker exec -ti hadoop-node sh
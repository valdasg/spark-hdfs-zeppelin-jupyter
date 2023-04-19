# Spark / Zeppelin development environment
Repository to create hdfs/spark/zeppelin/jupyter development environment.
To recreate environment, install Docker and docker-compose, clone repository and run:
```
docker-compose up -d --build
```
To access services use:
- Spark master: http://localhost:8080
- Zeppelin: http://localhost:8081
- Jupyter: http://localhost:8888

To get Jupyter login token do:
```
docker logs jupyter
```

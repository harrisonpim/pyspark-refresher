# PySpark refresher

It's been a while since I've used PySpark. This repo is a quick refresher on the basics, using docker and jupyter.

## Jupyter notebook interface

To start the jupyter notebook container with a connection to the spark cluster, run

```shell
docker compose up
```

## Standalone spark interface

You might not want to interact with spark through notebooks, preferring to work via a shell on a standalone spark container. To start the spark cluster, run

```shell
docker compose up --build -d spark
```

To open a scala spark shell, run

```shell
docker exec -it pyspark-refresher_spark_1 /opt/bitnami/spark/bin/spark-shell spark://spark:7077
```

To open a python spark shell, run

```shell
docker exec -it pyspark-refresher_spark_1 /opt/bitnami/spark/bin/pyspark --master spark://spark:7077
```

For anything else, you can open a regular bash shell in the container with

```shell
docker exec -it pyspark-refresher_spark_1 /bin/bash
```

## Adding more workers

To add more workers, run eg.

```shell
docker compose up --scale spark-worker=3
```

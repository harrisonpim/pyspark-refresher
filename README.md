# PySpark refresher

It's been a while since I've used PySpark. In this repo I'm giving myself a quick refresher on the basics. I'm setting up an environment with docker, and running the code through jupyter.

I'll be working through a lot of the examples/functionality from the [PySpark docs](https://spark.apache.org/docs/latest/api/python/index.html). The code itself lives in the [jupyter/notebooks](./jupyter/notebooks) directory.

## Running this yourself

### Jupyter notebook interface

To start the jupyter notebook container with a connection to the standalone spark cluster, run

```shell
docker compose up --build
```

### Standalone spark interface

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

## Getting data

I've used a couple of standard datasets in this repo.

To get them yourself, run

```shell
docker compose run get_data
```

## Modifications

## Adding more workers

To add more workers, run eg.

```shell
docker compose up --scale spark-worker=3
```

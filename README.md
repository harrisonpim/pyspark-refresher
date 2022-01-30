# PySpark refresher

It's been a while since I've used PySpark. In this repo I'm giving myself a quick refresher on the basics. I'm setting up a spark cluster with docker, and running code against it through a jupyterlab container. Every bit of this setup should be completely reproducible.

I'll be working through a lot of the examples/functionality from the [docs](https://spark.apache.org/docs/latest/api/python/index.html), exploring some standard datasets, and finally building a simple ML pipeline. The code itself lives in the [jupyter/notebooks](./jupyter/notebooks) directory.

## Running this yourself

### Jupyter notebook interface

To start the jupyter notebook container with a connection to the standalone spark cluster, run

```shell
docker compose up --build jupyter
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

### Datasets

I've used a couple of standard datasets in this repo, which live in the [data/](./data/) directory. To get them yourself, run

```shell
docker compose run get_data
```

### Adding more spark worker nodes

By default, everything above will run with a single worker node. To add more workers, run eg.

```shell
docker compose up --build jupyter --scale spark-worker=3
```

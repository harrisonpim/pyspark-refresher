FROM jupyter/pyspark-notebook

RUN pip install --upgrade pip pip-tools 
COPY requirements.* .
RUN pip-compile requirements.* --output-file requirements.txt
RUN pip install -r requirements.txt

RUN rm -rf work requirements* 

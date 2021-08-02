FROM continuumio/anaconda3

RUN pip install --upgrade pip
RUN pip install psycopg2-binary
RUN pip install mlflow[extras] sklearn jupyter jupyterlab

RUN mkdir -p /work/
RUN chmod 777 /work

CMD jupyter-lab --no-browser --ip=0.0.0.0 --port 8888 --allow-root --notebook-dir /work

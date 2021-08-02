FROM continuumio/anaconda3

RUN pip install --upgrade pip

RUN pip install mlflow[extras] google-cloud
RUN pip install psycopg2-binary

EXPOSE 5000

RUN mkdir -p /server

WORKDIR /server

COPY . /server

RUN chmod +x wait-for-it.sh

RUN mkdir /mlflow/

CMD ./wait-for-it.sh postgres:5432 -- mlflow server \
    --backend-store-uri postgresql://admin:secret@postgres:5432/mlflow \
    --default-artifact-root gs://mlops-runs/mlflow-runs \
    --host 0.0.0.0

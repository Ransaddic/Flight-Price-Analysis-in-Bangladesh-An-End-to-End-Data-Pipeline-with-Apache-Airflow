FROM apache/airflow:2.8.0-python3.9

USER root

RUN apt-get update && apt-get install -y \
    openjdk-17-jre-headless \
    default-mysql-client \
    libpq-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

USER airflow

COPY docker/requirements.txt /requirements.txt
RUN pip install --no-cache-dir -r /requirements.txt

COPY ./dags /opt/airflow/dags
COPY ./scripts /opt/airflow/scripts
COPY ./data /opt/airflow/data

# Airflow local setup
[<img src="https://img.shields.io/badge/Airflow-2.2.5-blue.svg?logo=LOGO">](https://airflow.apache.org/docs/apache-airflow/stable/start/local.html)

Quick setup for a local airflow instance.

> Only for development usage

## Installation
Activate a virtual environment

```bash
python -m virtualenv .venv
```

Activate it

```bash
source .venv/bin/activate
```

Create the airflow folders

```bash
mkdir -p ./logs ./dags ./plugins
```

Install airflow, example version 2.2.5:

```bash
# If you do not set this, airflow will set his home at the default "~/" directory:
export AIRFLOW_HOME=$(pwd)
AIRFLOW_VERSION=2.2.5
PYTHON_VERSION="$(python --version | cut -d " " -f 2 | cut -d "." -f 1-2)"
CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"
pipenv install "apache-airflow[async,postgres,google]==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"

# or 
chmod +x install.sh
./install.sh
```

## Run airflow

Initialize database

```bash
airflow db init
```

Run airflow webserver

```bash
airflow standalone
```

This file generates a local password for the `admin` user. Use that to connect to airflow.

Go to `localhost:8080` and log in.

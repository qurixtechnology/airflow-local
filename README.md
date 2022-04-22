# Airflow local setup

Light setup to setup a local airflow instance..

## Installation
Activate a virtual environment

```bash
pip install pipenv
mkdir .venv
pipenv shell
```

Create the airflow folders

```bash
mkdir -p ./logs ./dags ./plugins
```

Install airflow, example version 2.2.5:

```bash
export AIRFLOW_HOME=pwd
AIRFLOW_VERSION=2.2.5
PYTHON_VERSION="$(python --version | cut -d " " -f 2 | cut -d "." -f 1-2)"
CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"
pip install "apache-airflow[async,postgres,google]==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"

# or 
bash install.sh
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
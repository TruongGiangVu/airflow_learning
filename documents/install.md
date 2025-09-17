# Install by docker

## General

- Airflow version: 3.0.6
- Phải cài docker trước

## Setup app folder

```bash
# tạo foler ứng dụng
mkdir airflow

# move vào folder ứng dụng
cd airflow

# kéo file yaml triển khai apache-airflow về
curl -LfO "https://airflow.apache.org/docs/apache-airflow/3.0.6/docker-compose.yaml"

# tạo thêm folder cho ứng dụng
mkdir -p ./dags ./logs ./plugins
# folder logs: chứ log ứng dụng
# folder plugins: chứa plugins của ứng dụng
# folder dags: chứa các file dag được viết bằng python (chi tiết xem chỗ khác)
```

### Setup environment

```bash
# Tạo file .env với UID của airflow
echo AIRFLOW_UID=50000 > .env
```

## Initialize and Start

```bash
# This initializes the Airflow metadatabase and creates the admin user.
docker compose up airflow-init

# start containers
docker compose up
```

## Open webserver

- Mở link: http://localhost:8080
- Đăng nhập bằng user:
  - user: airflow
  - pass: airflow

## Stop and Restart

```bash
# stop containers
docker compose down

# start in detached mode
docker compose up -d
```

## Airflow-Cli

```bash
# lấy file script chạy một số lệnh của tool airflow cli
curl -LfO "https://airflow.apache.org/docs/apache-airflow/3.0.6/airflow.sh"

# kiểm tra thông tin airflow
./airflow.sh info
```

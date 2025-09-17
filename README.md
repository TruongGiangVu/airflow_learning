# Airflow

## General

- Công cụ để chạy ETL
- Viết bằng Python
- Không phải low-code
- Là orchestration tool (điều phối tập trung), hệ thống quản lý workflow (workflow management)
- Open-source
- "Configuration as Code"

### Used For

- Chạy ETL pipeline
- Data Ingestion pipeline (thu thập dữ liệu)
- Liên quan tới ML, DL, AI

## Concepts

### DAG (Directed Acyclic Graph)

- Gồm nhiều task
- Thực hiện nhiều task theo 1 flow

```bash
# Tas1 với task2 chạy song song -> xong hết mới tới lượt task4
[task1, task2] >> task4

# Tas3 chạy trước -> xong rồi mới tới lượt task4
task3 >> task4

## Task4 phải chờ cả 3 task1, task2, task3 xong thì mới chạy
```

- Cách chạy
  - manually | automatically
  - scheduled in the future
  - periodically

### Task

- Thực hiện 1 công việc gì đó
- 3 types of Task
  - Operators
  - Sensors:
  - TaskFlow

### Operators

- Là template để định nghĩ 1 task
  | Built in | Provider package |
  | -------- | ---------------- |
  | BashOperator | OracleOperator |
  | PythonOperator | SimpleHttpOperator |
  | EmailOperator | DockerOperator |
  | | KubernetesPodOperator |
  | | ... |

### Sensors

- Được cấu hình thực hiện 1 cái gì đó, hay đợi 1 cái gì đó xảy ra
- Các loại sensor
  - FileSensor: chờ khi có file đó xuất hiện
  - DateTimeSensor: chờ tới date time nào đó thì chạy
  - SqlSensor: chạy lệnh sql lặp lại tới khi nào đó
  - ExternalSensor: chờ 1 DAG hoặc 1 task khác ...
  - ...

### TaskFlow

Incoming

## Architecture

- Metadata database: lưu trữ system data
- DAG Directory: lưu các file dag
- Webserver: web ứng dụng
- Schedular: theo dõi và thực thi executors
- Executors: gọi và DAG

### Executors

| Local      | Remote     |
| ---------- | ---------- |
| Debug      | Celery     |
| Local      | Kubernetes |
| Sequential |            |

## References

- https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html
- https://chatgpt.com/share/68ca0ca9-e484-8008-9bed-a5a81600d6d9

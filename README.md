# Nginx 日志分析系统（基于 ELK + Kafka）

本项目实现了一个完整的日志收集与分析系统，使用 ELK Stack、Kafka 及 Filebeat 从 Nginx 实时采集 Access 和 Error 日志，最终在 Kibana 中进行可视化分析。

---

## 🔧 技术架构

- **Nginx**：日志源
- **Filebeat**：日志收集器，发送日志到 Kafka
- **Kafka**：日志传输队列
- **Logstash**：从 Kafka 消费日志并发送到 Elasticsearch
- **Elasticsearch**：日志索引和存储
- **Kibana**：日志查询与可视化

---

## 🚀 启动方式

请确保安装了 Docker 和 Docker Compose，然后运行：

docker-compose up -d

📌 日志处理流程

Nginx --> Filebeat --> Kafka --> Logstash --> Elasticsearch --> Kibana
Nginx 产生日志

Filebeat 读取 access.log 与 error.log，发送到 Kafka topic（如 nginx-access、nginx-error）

Logstash 消费 Kafka topic 并将数据结构化后发送到 Elasticsearch

Kibana 查询和展示日志信息

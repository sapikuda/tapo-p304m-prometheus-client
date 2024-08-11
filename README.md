# Tapo P304M Prometheus Client

Prometheus Client for TP-Link Tapo P304M Smart Wi-Fi Power Strip.

This project provides a Prometheus client implementation for the TP-Link Tapo P304M Smart Wi-Fi Power Strip, allowing for real-time monitoring and metrics collection. The client is designed to interface with the Tapo P304M, extracting critical data such as power consumption, device status, and individual outlet usage. This information is then formatted and exposed as Prometheus metrics, enabling seamless integration into existing monitoring and alerting systems.

> This code worked on [TP-Link Tapo P304M](https://www.tp-link.com/sg/home-networking/smart-plug/tapo-p304m/) with firmware version 1.0.3 Build 240605 Rel.091502.

## How to use it?

### Run the Code

This is project is based on Python Prometheus Client.

To run from the source code, just run the:

```python3 prometheus.py```

It requires following dependencies:

```requirement.txt
pycryptodome>=3.20.0
pkcs7>=0.1.2
requests>=2.32.3
prometheus_client>=0.20.0
Flask>=3.0.3
Werkzeug>=3.0.3
waitress>=3.0.0
```

> WARNING! The application must run on the same network as the sockets.

## Prometheus Metrics

For prometheus, it is necessary to define the target in the `prometheus.yml` settings

Example:

```yaml
  - job_name: tapo_p304m
    metrics_path: '/metrics'
    scrape_interval: 15s
    static_configs:
      - targets:
          - '192.168.68.62:8882'

```

Metrics are available at [http://localhost:8882/metrics](http://localhost:8882/metrics).

All metrics begin with the prefix tapo_p304m_. Current list:

| Name of Netric                |
|-------------------------------|
| tapo_p304m_device_info        |
| tapo_p304m_device_usage       |
| tapo_p304m_plugs              |
FROM grafana/grafana:5.0.0
ENV GF_DS_PROMETHEUS_SERVER Prometheus Server
ENV DS_PROMETHEUS_SERVER Prometheus Server
COPY prometheus_datasource.yaml /etc/grafana/provisioning/datasources/
COPY dashboard.yml /etc/grafana/provisioning/dashboards/
COPY dashboards/*json /var/lib/grafana/dashboards/

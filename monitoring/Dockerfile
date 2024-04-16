FROM ubuntu

RUN apt-get update && \
    apt-get install -y wget curl && \
    rm -rf /var/lib/apt/lists/*

RUN wget -q -O /tmp/grafana.deb https://dl.grafana.com/oss/release/grafana_8.0.0_amd64.deb && \
    dpkg -i /tmp/grafana.deb && \
    rm -f /tmp/grafana.deb

RUN wget -q -O /tmp/prometheus.tar.gz https://github.com/prometheus/prometheus/releases/download/v2.30.0/prometheus-2.30.0.linux-amd64.tar.gz && \
    tar -xzf /tmp/prometheus.tar.gz -C /tmp && \
    mv /tmp/prometheus-2.30.0.linux-amd64 /opt/prometheus && \
    rm -f /tmp/prometheus.tar.gz

COPY grafana.ini /etc/grafana/grafana.ini
COPY prometheus.yml /opt/prometheus/prometheus.yml

EXPOSE 3000 9090

CMD service grafana-server start && /opt/prometheus/prometheus --config.file=/opt/prometheus/prometheus.yml

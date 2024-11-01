FROM prom/prometheus:v2.54.1 AS base

FROM registry.access.redhat.com/ubi9/ubi

COPY LICENSE /licenses/LICENSE

COPY --from=base /etc/prometheus /etc/prometheus
COPY --from=base /bin/prometheus /bin/promtool /bin/

WORKDIR /prometheus
RUN chown -R nobody:nobody /etc/prometheus /prometheus

USER 65534:65534
EXPOSE     9090
VOLUME "/prometheus"
ENTRYPOINT [ "/bin/prometheus" ]
CMD        [ "--config.file=/etc/prometheus/prometheus.yml", "--storage.tsdb.path=/prometheus" ]

FROM prom/prometheus:v2.54.1 AS base

FROM registry.access.redhat.com/ubi9/ubi
USER 65534:65534
WORKDIR /prometheus
COPY --from=base /LICENSE /licenses/LICENSE
COPY --from=base /etc/prometheus /etc/prometheus
COPY --from=base /bin/prometheus /bin/prometheus
COPY --from=base /bin/promtool /bin/promtool
EXPOSE     9090
VOLUME     [ "/prometheus" ]
ENTRYPOINT [ "/bin/prometheus" ]
CMD        [ "--config.file=/etc/prometheus/prometheus.yml", "--storage.tsdb.path=/prometheus" ]

FROM clickhouse/clickhouse-server:24.8.4 AS base

FROM registry.access.redhat.com/ubi9/ubi

USER 65534:65534

COPY LICENSE /licenses/LICENSE
COPY --from=base /etc/clickhouse* /etc/
COPY --from=base /usr/bin/clickhouse* /usr/bin/
COPY --from=base /var/lib/clickhouse* /var/lib/
COPY --from=base /var/log/clickhouse* /var/log/
COPY --from=base /docker-entrypoint-initdb.d /entrypoint.sh /

EXPOSE 9000 8123 9009

VOLUME "/var/lib/clickhouse"

ENV CLICKHOUSE_CONFIG /etc/clickhouse-server/config.xml

ENTRYPOINT ["/entrypoint.sh"]

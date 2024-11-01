FROM clickhouse/clickhouse-server:24.8.4 AS base

FROM registry.access.redhat.com/ubi9/ubi

COPY LICENSE /licenses/LICENSE

COPY --from=base /etc/clickhouse-server /etc/clickhouse-server
COPY --from=base /etc/clickhouse-keeper /etc/clickhouse-keeper
COPY --from=base /etc/clickhouse-client /etc/clickhouse-client
COPY --from=base /usr/bin/clickhouse /usr/bin/clickhouse-server /usr/bin/clickhouse-keeper /usr/bin/clickhouse-client /usr/bin/
COPY --from=base /entrypoint.sh /entrypoint.sh

RUN mkdir /var/lib/clickhouse /var/log/clickhouse-server /docker-entrypoint-initdb.d \
    && chown -R nobody:nobody /etc/clickhouse-* /var/lib/clickhouse /var/log/clickhouse-server /docker-entrypoint-initdb.d

USER 65534:65534
EXPOSE 9000 8123 9009
VOLUME "/var/lib/clickhouse"
ENV CLICKHOUSE_CONFIG=/etc/clickhouse-server/config.xml
ENV CLICKHOUSE_UID=nobody
ENV CLICKHOUSE_GID=nobody
ENTRYPOINT ["/entrypoint.sh"]

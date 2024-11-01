FROM clickhouse/clickhouse-server:24.8.4 AS base

FROM registry.access.redhat.com/ubi9/ubi

COPY LICENSE /licenses/LICENSE

COPY --from=base /etc/clickhouse-server /etc/clickhouse-client /etc/
COPY --from=base /usr/bin/clickhouse* /usr/bin/
COPY --from=base /entrypoint.sh /entrypoint.sh

RUN mkdir /var/lib/clickhouse /var/log/clickhouse-server /docker-entrypoint-initdb.d \
    && chown -R nobody:nobody /var/lib/clickhouse /var/log/clickhouse-server /docker-entrypoint-initdb.d

USER 65534:65534
EXPOSE 9000 8123 9009
VOLUME "/var/lib/clickhouse"
ENV CLICKHOUSE_CONFIG=/etc/clickhouse-server/config.xml
ENTRYPOINT ["/entrypoint.sh"]

FROM registry.k8s.io/kube-state-metrics/kube-state-metrics:v2.13.0 AS base

FROM registry.access.redhat.com/ubi9/ubi

COPY LICENSE /licenses/LICENSE

COPY --from=base /kube-state-metrics /kube-state-metrics

USER 65534:65534
EXPOSE 8080 8081
ENTRYPOINT ["/kube-state-metrics", "--port=8080", "--telemetry-port=8081"]

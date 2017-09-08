![logo](assets/prometheus.png)

---

## Our Setup at HC

+++

## Our Setup at HC

- one central server for collecting metrics, alerting, and dashboarding

+++

## Our Setup at HC

- one central server for collecting metrics, alerting, and dashboarding
- http://prometheus.prod.hcg.cloud

+++

## Our Setup at HC

- one central server for collecting metrics, alerting, and dashboarding
- http://prometheus.prod.hcg.cloud
- http://grafana.prod.hcg.cloud

---

## Production Monitoring and On-Call

- auto-discovery in production
- symptom-based alerting
- few cause-based alerts

+++

## A Sample Alert

```
ALERT RoutecontrolHcErrorRate
  IF nginx_http_errors_per_request:rate2m > 0.05 AND on (host, page_type)
     sum_over_time(nginx_http_requests_total{status=~"2.."}[6h]) > 0
  FOR 10m
  LABELS {
    severity = "emergency",
    team = "opseng",
  }
  ANNOTATIONS {
    summary = "High error rate ({{ $labels.status }}) for {{ $labels.page_type }}
               on {{ $labels.host }}"
  }
```
@[1]
@[2-3](alert condition)
@[4](duration)
@[5-8](labels are used by alertmanager to route alerts)
@[9-12](descriptive error message)

---

## Recording Rules for Expensive Aggregations

```
host_page_type:nginx_http_request_duration_seconds:rate2m_quantile90 =
histogram_quantile(0.90,
  sum(
    rate(
      nginx_http_request_duration_seconds_bucket[2m]
    )
  ) by (host, le, page_type)
)

```
@[1](new variable name)
@[2-8](calculate 90th percentile request duration)

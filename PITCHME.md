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
  IF host_page_type_status:nginx_http_errors_per_request:rate2m{application="holidaycheck", collector="routecontrol"} > 0.05
     AND on (host, page_type) sum_over_time(nginx_http_requests_total{instance_name=~"prod-opseng-routecontrol.*", host=~"(.*holidaycheck.*|admin.hc.ag)", status=~"2.."}[6h]) > 0
  FOR 10m
  LABELS {
    severity = "emergency",
    team = "opseng",
  }
  ANNOTATIONS {
    summary = "High error rate ({{ $labels.status }}) for {{ $labels.page_type }} on {{ $labels.host }}"
  }
```

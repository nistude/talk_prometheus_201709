![logo](assets/prometheus.png)

---

## Basic Building Blocks

- metrics |
  - `nginx_http_requests_total`
- labels |
  - `{host="www.holidaycheck.ch",
      instance_name="prod-opseng-routecontrolb-nfs0",
      job="nginx-request-metrics-ch",
      page_type="api public-profiles",
      status="304"}`
- timeseries |
  - metrics + labels

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


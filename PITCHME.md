![prometheus logo](assets/prometheus.png)
![grafana logo](assets/grafana.png)

---

## Basic Building Blocks

- labels all the way down |
  - `{host="www.holidaycheck.ch",
      instance_name="prod-opseng-routecontrolb-nfs0",
      job="nginx-request-metrics-ch",
      page_type="api public-profiles",
      status="304"}`
- metric aka `__name__` label |
  - `nginx_http_requests_total`
- 1 timeseries per label set |

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


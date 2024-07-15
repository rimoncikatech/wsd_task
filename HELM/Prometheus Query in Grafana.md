To show the usage trend of an application metric that is a counter in Grafana using Prometheus, you typically use <br />
 the rate() function. For example, if your metric is requests_total: <br />

 ```
 rate(requests_total[5m])
```

This query calculates the per-second rate of increase of the requests_total metric over the last 5 minutes, which <br/> is useful for displaying trends over time.

### Explain How Prometheus Works <br />
Prometheus  works by scraping metrics from configured endpoints at regular intervals (configured via scraping intervals in its configuration). <br />

1. Prometheus Server: Responsible for querying targets, storing metrics, and evaluating rules.
Metrics Scraping: Pulls metrics from instrumented jobs (applications or services) using HTTP endpoints (usually /metrics). <br />

2. Data Storage: Stores metrics in a time-series database, typically using a local on-disk storage. <br />

3. Alerting: Evaluates rules defined in Prometheus' configuration and triggers alerts based on defined conditions.
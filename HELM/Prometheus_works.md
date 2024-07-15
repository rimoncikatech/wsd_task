
1) Explain How Prometheus Works
Prometheus  works by scraping metrics from configured endpoints at regular intervals (configured via scraping intervals in its configuration). Key components include:

Prometheus Server: Responsible for querying targets, storing metrics, and evaluating rules.
Metrics Scraping: Pulls metrics from instrumented jobs (applications or services) using HTTP endpoints (usually /metrics).
Data Storage: Stores metrics in a time-series database, typically using a local on-disk storage.
Alerting: Evaluates rules defined in Prometheus' configuration and triggers alerts based on defined conditions.
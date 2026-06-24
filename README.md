# LLM Observability & Eval Dashboard

Self-hosted observability platform for production LLM applications.

## What it does
- Ingests OpenTelemetry GenAI spans from OpenAI, Anthropic, Google GenAI, LangChain, LlamaIndex, and vLLM
- Stores spans in ClickHouse for columnar analytics; metadata in Postgres
- Runs scheduled eval jobs (DeepEval, RAGAS, custom LLM-judge) over sampled traces
- Detects prompt-distribution drift via PSI / KL divergence on embeddings
- Alerts via Prometheus Alertmanager → Slack / PagerDuty
- Dashboard: Next.js 15 + Recharts (cost/user, latency, toxicity trends, drift)

## Stack
| Layer | Technology |
|---|---|
| Ingest | OpenTelemetry SDK + GenAI semconv, OTLP HTTP |
| Collector | OTel Collector with tail-sampling |
| Storage | ClickHouse (spans), Postgres (metadata), S3 (archive) |
| Evals | DeepEval, RAGAS 0.2, custom LLM-judge |
| Drift | sentence-transformers + PSI/KL weekly job |
| Alerting | Prometheus Alertmanager → Slack / PagerDuty |
| UI | Next.js 15 App Router + Recharts |

# 📊 Node Exporter Full - Monitoring Report Workflow for n8n

This `n8n` workflow automatically retrieves system monitoring data from Grafana (Node Exporter dashboard), processes it with AI, and sends a summary report via email.

---

## 🧩 Features

- ✅ Pulls dashboard data from Grafana using its API
- 🧠 Uses AI (Gemini) to analyze metrics and logs
- 🔧 Integrates with MCP-Grafana tools (Prometheus, Loki, Alert rules)
- 📬 Sends a professional monitoring report via Gmail
- 📅 Can be scheduled to run periodically (e.g. every X minutes)

---

## 🛠️ Setup Instructions

### 1. Import Workflow
Import the `Node_Exporter_Full_CLEANED_FOR_GITHUB.json` into your n8n instance.

### 2. Set Up Required Credentials
Create the following credentials in your n8n environment:

| Credential Name                    | Type                  | Purpose                          |
|------------------------------------|------------------------|----------------------------------|
| `Grafana account`                 | HTTP Basic/Auth Token  | Access to Grafana API            |
| `Google Gemini(PaLM) Api account` | Google API Key / OAuth | Access Gemini model              |
| `Gmail account`                   | Gmail OAuth2           | Send email reports               |

> You can rename these credentials or update the node settings after importing.

---

## ⚙️ Environment Requirements

- n8n >= `1.6.0`
- Access to:
  - Grafana dashboard (Node Exporter Full)
  - MCP-Grafana backend (via MCP Client Tool)
  - Google Gemini API
  - SMTP/Email for sending reports

---

## 🧪 Optional (Advanced)

To ensure AI models and MCP tools are ready before execution, consider adding a **health check step** using:

- `HTTP Request` to Gemini `/models`
- `HTTP Request` to MCP Client `/sse` or `/health`

Let us know if you'd like a health-check version of the workflow.

---

## 📄 Output Format

The final email report will include:

- Subject: `[Dashboard Name] - [Date]`
- Key Metrics Summary
- System Status
- Alerts (if any)
- Recommendations
- Focus Areas for Next Check

---

## 📥 Sample Email Output

```
Subject: Node Exporter Full - 2025-07-07

- CPU Usage: 72%
- Memory Usage: 81%
- Disk Root FS: 91%

⚠️ Alerts:
- Critical: Memory usage exceeded 80%
- Warning: Disk usage over 85%

Recommendations:
- Investigate memory spike on node-01
- Clean up root filesystem or extend volume
```

---

## 📜 License

MIT License — feel free to copy, modify, or integrate.

# Apigee-API-Gateway-Automated-Daily-Reporting-System

🔷 Description:
Designed and implemented a fully automated daily reporting pipeline for an Apigee API Gateway running on Google Cloud Platform (GCP). The system runs on a scheduled cron job, authenticates securely using a GCP service account, queries the Apigee Management Stats API to retrieve the previous day's traffic data across all API proxies, and delivers a complete health report to the operations team every morning — with no manual intervention.

The report is generated in two formats simultaneously: a styled HTML email body for quick visual reading, and a CSV file attachment for data analysis and archiving.

🔷 Key Features:
• Per-proxy breakdown of Total Requests, Successes, and Errors
• Granular HTTP status code tracking: 400, 401, 403, 404, 409, 412, 429, 500, 502, 503, 504
• Automatic aggregation into 4xx (Business Error Rate) and 5xx (Server Error Rate)
• Success Rate calculation per proxy
• Dual-format output: HTML (inline email) + CSV (attachment)
• Secure GCP authentication via service account key + gcloud CLI
• MIME multipart email dispatch via sendmail

🔷 Technical Challenges:
The Apigee Stats API returns dimension data in inconsistent JSON structures depending on the query type — including individualNames arrays, nested sub-dimensions, and flat composite dimension names (e.g. "ProxyName,200"). A robust Python parser was built to handle all three formats reliably across any number of proxies and status codes.

🔷 Tech Stack:
Bash · Python 3 · Google Cloud Platform · Apigee Management API · gcloud CLI · GCP Service Account Auth · sendmail · HTML · CSV

🔷 Impact:
Eliminated daily manual API health checks for the operations team. The team now receives a full per-proxy analytics digest every morning, enabling faster incident detection and trend analysis across 10+ production API proxies processing millions of daily requests.

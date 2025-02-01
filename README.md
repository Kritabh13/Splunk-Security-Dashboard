# Splunk-Security-Dashboard
A Splunk dashboard for monitoring security logs
# Splunk Security Monitoring Dashboard

## 📌 Overview
This project is a **Splunk Security Monitoring Dashboard** designed to track and visualize security-related events, such as:
- **Login Attempts (Successful vs. Failed)**
- **Top 10 Sources of Network Traffic**
- **Alerts for Suspicious Activity**

## 🚀 Features
- **Real-time security monitoring** using Splunk.
- **Pre-built visualizations** for quick insights.
- **Automated alerts** for failed login attempts.
- **CSV-based log data ingestion**.

## 📂 Project Structure
```
📁 Splunk-Security-Dashboard
│── 📄 README.md (This file)
│── 📄 sample_data.csv (Sample log file for testing)
│── 📄 queries.txt (Splunk search queries used in the dashboard)
│── 📄 dashboard.pdf (Exported Splunk dashboard configuration)
│── 📁 screenshots (Contains images of dashboard visualizations)
```

## 🛠 Setup Instructions
### 1️⃣ Install Splunk
Download and install **Splunk Enterprise** from [Splunk’s official website](https://www.splunk.com/en_us/download.html).

### 2️⃣ Ingest Data
1. Navigate to **Settings > Add Data > Upload File**.
2. Upload the `sample_data.csv` file.
3. Set the **Sourcetype** to `csv` and create an **index** (e.g., `security_index`).

### 3️⃣ Run Splunk Queries
Use the **Search & Reporting App** in Splunk to run these queries:
#### **Login Attempts Breakdown**
```spl
index="security_index" sourcetype=csv event_type=login_attempt 
| stats count by status
```
#### **Top 10 IP Addresses Generating Traffic**
```spl
index="security_index" sourcetype=csv event_type=file_access 
| top limit=10 ip_address
```
#### **Failed Logins Alert**
```spl
index="security_index" sourcetype=csv event_type=login_attempt status=failed 
| stats count by user
| where count > 5
```

### 4️⃣ Import Dashboard JSON
1. Navigate to **Dashboards**.
2. Click **Create New Dashboard** > **Import JSON**.
3. Upload `dashboard.json`.

### 5️⃣ Set Up Alerts
- Go to **Search & Reporting**.
- Run the **Failed Logins Alert** query.
- Click **Save As > Alert** and configure notifications.

## 📸 Screenshots
![Dashboard Preview](screenshots/dashboard.png)

## 🤝 Contributing
Feel free to **fork this repository**, open an **issue**, or submit a **pull request** to improve the project!

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

### ✨ Follow Me for More Projects
🔗 [LinkedIn](https://linkedin.com/) | 🔗 [GitHub](https://github.com/) | 🔗 [Medium](https://medium.com/)

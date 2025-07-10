# Brute Force Detection with Splunk

This project simulates a brute-force SSH login attack and shows how to detect it using Splunk's search and dashboard capabilities.

## 🔍 Use Case
Detect multiple failed SSH login attempts from the same IP address (a brute-force pattern).

## 🧰 Tools Used
- Splunk Enterprise (Free Trial)
- Sample Linux auth logs
- SPL (Search Processing Language)

## 📊 What’s Included
- Sample SSH log file (`sample_logs.txt`)
- SPL search query to identify suspicious IPs
- Saved dashboard panel with table/chart view

## 🛠 How It Works
1. Upload `sample_logs.txt` to Splunk.
2. Run this SPL query:
   ```spl
   index=brute_force_demo "Failed password"
   | rex "from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
   | stats count by src_ip
   | where count > 2





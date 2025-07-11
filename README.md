# Brute Force Detection with Splunk

This project simulates a brute-force SSH login attack and shows how to detect it using Splunk's search and dashboard capabilities.

## Use Case
Detect multiple failed SSH login attempts from the same IP address (a brute-force pattern).

## Tools Used
- Splunk Enterprise (Free Trial)
- Sample Linux auth logs
- SPL (Search Processing Language)

## What’s Included
- Sample SSH log file (`sample_logs.txt`)
- SPL search query to identify suspicious IPs
- Saved dashboard panel with table/chart view

## How It Works
1. Upload `sample_logs.txt` to Splunk.
2. Run this SPL query:
   ```spl
   index=brute_force_demo "Failed password"
   | rex "from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
   | stats count by src_ip
   | where count > 2

Output

IPs with more than 2 failed login attempts
Table or chart visualizing brute-force attack sources

<img width="759" height="401" alt="Screenshot 2025-07-10 at 7 56 01 PM" src="https://github.com/user-attachments/assets/09903a85-1187-4d66-b5fd-1b8dd579e627" />





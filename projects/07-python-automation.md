# Project 7 — Python Automation for Security

**Skills:** Python · File parsing · Algorithms · Allow/deny lists

## 📌 Scenario
The security team maintains an **allow list** of IP addresses permitted to access a restricted
subnetwork. I wrote a Python script to automatically remove IPs that appear on a **remove list**
(revoked access), instead of editing the file by hand.

## 🐍 The Script
```python
# update_allow_list.py
# Removes revoked IP addresses from an allow-list file.

import_file = "allow_list.txt"
remove_list = ["192.168.97.225", "192.168.158.170", "192.168.201.40", "192.168.216.176"]

# 1. Read the allow list into a string
with open(import_file, "r") as file:
    ip_addresses = file.read()

# 2. Convert the string into a list
ip_addresses = ip_addresses.split()

# 3. Remove any IP that is on the remove list
for element in ip_addresses[:]:            # iterate over a copy
    if element in remove_list:
        ip_addresses.remove(element)

# 4. Convert back to a string and write it out
ip_addresses = "\n".join(ip_addresses)
with open(import_file, "w") as file:
    file.write(ip_addresses)

print("Allow list updated.")
```

## 🔑 Concepts Demonstrated
- **File I/O** with context managers (`with open(...)`)
- **String ↔ list** conversion (`.split()`, `.join()`)
- **Iteration + conditionals** to filter data
- **Access control automation** — reducing human error

## 🧾 Outcome
Automated an access-control task that scales to thousands of entries, ensuring revoked IPs lose
access consistently and immediately — a small but real example of security automation.

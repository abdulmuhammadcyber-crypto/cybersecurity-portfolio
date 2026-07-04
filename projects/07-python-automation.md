# Project 7 — Python Automation for Security

Skills: Python, file parsing, algorithms, allow and deny lists.

## Scenario

The security team maintains an allow list of IP addresses permitted to access a restricted subnetwork. I wrote a Python script to automatically remove IP addresses that appear on a remove list of revoked access, instead of editing the file by hand.

## The Script

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

# 3. Remove any IP address that is on the remove list
for element in ip_addresses[:]:            # iterate over a copy
    if element in remove_list:
        ip_addresses.remove(element)

# 4. Convert back to a string and write it out
ip_addresses = "\n".join(ip_addresses)
with open(import_file, "w") as file:
    file.write(ip_addresses)

print("Allow list updated.")
```

## Concepts Demonstrated

- File input and output using context managers with the open function
- Converting between strings and lists using split and join
- Iteration and conditionals to filter data
- Automating an access-control task to reduce human error

## Outcome

I automated an access-control task that scales to thousands of entries, ensuring revoked IP addresses lose access consistently and immediately. This is a small but practical example of security automation.

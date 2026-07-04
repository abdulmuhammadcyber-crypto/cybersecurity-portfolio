# Project 4 — Linux File Permissions Hardening

**Skills:** Linux · Bash · `chmod`/`ls -l` · Principle of least privilege

## 📌 Scenario
As a security analyst at a healthcare company, I audited file permissions in a team's project
directory to ensure they follow the organization's **least-privilege** policy.

## 🔍 Auditing Permissions
```bash
ls -la /home/researcher2/projects
```
Example output:
```
drwxr-xr-x  2 researcher2 research_team  4096 project_folder
-rw-rw-rw-  1 researcher2 research_team   ...  project_k.txt   <-- world-writable (bad)
-rw-r-----  1 researcher2 research_team   ...  project_t.txt
-rw-rw-r--  1 researcher2 research_team   ...  .project_x.txt  <-- hidden, group-writable (bad)
drwx--x--x  2 researcher2 research_team   ...  drafts
```

## ⚠️ Findings & Fixes

| File | Problem | Command | Result |
|---|---|---|---|
| `project_k.txt` | Others have **write** access | `chmod o-w project_k.txt` | Remove world write |
| `.project_x.txt` | Group + owner should be read-only | `chmod u-w,g-w .project_x.txt` | Read-only |
| `project_m.txt` | Group has read; should not | `chmod g-r project_m.txt` | Restrict group |
| `drafts/` | Group should not enter dir | `chmod g-x drafts` | Owner-only access |

## ✅ Verification
```bash
ls -la /home/researcher2/projects   # confirm updated permission bits
```

## 🧾 Outcome
Enforced least privilege by removing excessive read/write/execute permissions, reducing the risk
of unauthorized access to sensitive research data (protecting **confidentiality** and **integrity**).

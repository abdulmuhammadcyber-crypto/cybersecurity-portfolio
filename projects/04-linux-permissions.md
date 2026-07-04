# Project 4: Linux File Permissions Hardening

Skills: Linux, Bash, chmod and ls -l, principle of least privilege.

## Scenario

As a security analyst at a healthcare company, I audited file permissions in a team's project directory to ensure they followed the organization's least-privilege policy.

## Auditing Permissions

```bash
ls -la /home/researcher2/projects
```

Example output:

```
drwxr-xr-x  2 researcher2 research_team  4096 project_folder
-rw-rw-rw-  1 researcher2 research_team   ...  project_k.txt      # world-writable, needs fixing
-rw-r-----  1 researcher2 research_team   ...  project_t.txt
-rw-rw-r--  1 researcher2 research_team   ...  .project_x.txt     # hidden, group-writable, needs fixing
drwx--x--x  2 researcher2 research_team   ...  drafts
```

## Findings and Fixes

| File | Problem | Command | Result |
|---|---|---|---|
| project_k.txt | Others have write access | chmod o-w project_k.txt | Remove world write |
| .project_x.txt | Group and owner should be read-only | chmod u-w,g-w .project_x.txt | Read only |
| project_m.txt | Group has read and should not | chmod g-r project_m.txt | Restrict group |
| drafts | Group should not enter the directory | chmod g-x drafts | Owner-only access |

## Verification

```bash
ls -la /home/researcher2/projects   # confirm the updated permission bits
```

## Outcome

I enforced least privilege by removing excessive read, write, and execute permissions, reducing the risk of unauthorized access to sensitive research data and protecting confidentiality and integrity.

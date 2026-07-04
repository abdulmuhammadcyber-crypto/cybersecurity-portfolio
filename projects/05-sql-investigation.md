# Project 5: SQL for Security Investigations

Skills: SQL, filtering with WHERE, AND, OR, NOT, and LIKE, joins, log analysis.

## Scenario

Following suspicious activity, I queried the organization's log_in_attempts and employees databases to investigate a potential compromise and update access.

## Investigations

### 1. Failed logins after business hours

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
```

Purpose: find failed after-hours attempts that may indicate brute-force or unauthorized access.

### 2. Logins on suspicious days

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

### 3. Logins outside a trusted location

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country IN ('USA', 'US');
```

### 4. Employees needing security updates by department and office

```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East-%';
```

### 5. Join login attempts to employee identity

```sql
SELECT e.employee_id, e.username, l.login_time, l.success
FROM employees AS e
INNER JOIN log_in_attempts AS l
  ON e.username = l.username
WHERE l.success = 0;
```

## Outcome

I used SQL filtering and joins to pinpoint anomalous authentication activity and to scope which employee machines required patching, turning raw logs into actionable investigation results.

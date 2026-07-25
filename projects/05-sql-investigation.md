# Apply Filters to SQL Queries

Skills: SQL filtering with WHERE, AND, OR, NOT, LIKE, pattern matching, date and time filtering, log analysis.

## Project description

As a security professional at a large organization, part of my job is to investigate potential security issues and help keep systems secure. In this project I examined the organization's employees and log_in_attempts tables to look into suspicious login activity and to identify which employee machines needed security updates. I used SQL filters to retrieve specific records from each dataset, combining conditions with operators such as AND, OR, and NOT and matching text patterns with LIKE. The result was a set of focused queries that turned large tables of raw data into the exact records needed for each investigation.

## Retrieve after hours failed login attempts

I discovered a potential security incident that took place after business hours, so I needed to review failed login attempts that happened after 18:00. The login_time column holds the time of each attempt and the success column holds a 0 when an attempt fails.

```sql
SELECT *
FROM log_in_attempts
WHERE login_time > '18:00' AND success = 0;
```

This query returns every record from the log_in_attempts table where both conditions are true. The first condition, login_time > '18:00', keeps only attempts made after six in the evening. The second condition, success = 0, keeps only the attempts that failed. Because I joined the two conditions with AND, a row is returned only when it satisfies both, which gives me exactly the failed after hours attempts that could point to unauthorized access.

## Retrieve login attempts on specific dates

A suspicious event occurred on 2022-05-09, so I wanted to review all login attempts from that day and the day before it. The date of each attempt is stored in the login_date column.

```sql
SELECT *
FROM log_in_attempts
WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';
```

Here I used the OR operator because I wanted attempts from either of two dates rather than both at once. A single row can only carry one date, so OR is the correct choice: the query returns a record if its login_date matches 2022-05-09 or 2022-05-08. This gave me a complete picture of activity around the suspicious event.

## Retrieve login attempts outside of Mexico

The team determined that the suspicious activity did not originate in Mexico, so I needed the login attempts that happened everywhere except Mexico. The country column stores Mexico as both MEX and MEXICO, so I used LIKE with the percent sign to match both, and NOT to exclude them.

```sql
SELECT *
FROM log_in_attempts
WHERE NOT country LIKE 'MEX%';
```

The pattern 'MEX%' matches any value that starts with the letters MEX, which covers both MEX and MEXICO. The percent sign is a wildcard that stands in for any number of characters after MEX. Placing NOT in front of the LIKE condition reverses it, so the query returns every login attempt whose country does not begin with MEX. This let me focus on activity from outside Mexico without having to list every other country by hand.

## Retrieve employees in Marketing

My team planned security updates for machines in the Marketing department located in the East building. Employee records are in the employees table, with the department in the department column and the location in the office column. Office values look like East-170, East-320, and North-434, so I filtered the building with LIKE.

```sql
SELECT *
FROM employees
WHERE department = 'Marketing' AND office LIKE 'East%';
```

This query combines an exact match on the department with a pattern match on the office. The condition department = 'Marketing' keeps only Marketing employees, and office LIKE 'East%' keeps only the offices whose value starts with East, regardless of the room number that follows. Joining the two with AND returns only the Marketing employees who work in the East building, which is the precise group whose machines needed the update.

## Retrieve employees in Finance or Sales

Next my team needed to update machines for employees in the Sales and Finance departments. Because an employee belongs to one department at a time, I used OR to capture members of either group.

```sql
SELECT *
FROM employees
WHERE department = 'Sales' OR department = 'Finance';
```

The query returns a record when the department is Sales or when it is Finance. Using OR here is important: an AND between the two department conditions would return nothing, since no single row can be both Sales and Finance at the same time. This produced a single list of all the employees in either department.

## Retrieve all employees not in IT

The last update was already applied to the Information Technology department, so I needed every employee outside of that department. The department column stores this team as Information Technology.

```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```

The NOT operator reverses the condition that follows it. On its own, department = 'Information Technology' would return only IT staff, so placing NOT in front of it returns everyone whose department is not Information Technology. This gave me the full set of employees who still needed the security update while cleanly excluding the team that already had it.

## Summary

Across these tasks I used SQL filters to investigate suspicious authentication activity and to scope a series of security updates. I filtered on time and date to isolate after hours failures and activity around a suspicious event, used LIKE with the percent wildcard to match country and office values that were stored in more than one form, and combined conditions with AND and OR to narrow results to an exact group. I also used NOT to exclude records, such as login attempts from Mexico and employees already covered by the IT update. Together these queries show how filtering turns large security tables into the specific records an investigation actually needs.

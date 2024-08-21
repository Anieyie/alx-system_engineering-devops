# Postmortem Report

## Issue Summary

- **Duration:** 2024-08-20 10:00 AM - 2024-08-20 11:30 AM (UTC)
- **Impact:** 25% of users experienced slow load times; critical services like checkout were unavailable.
- **Root Cause:** Database connection pool was exhausted due to inefficient query handling.

## Timeline

- **10:00 AM:** Issue detected through an alert triggered by monitoring systems.
- **10:05 AM:** The on-call engineer begins investigating high database latency.
- **10:15 AM:** Assumption: The issue might be due to a spike in traffic. Misleading path explored by adding more resources to the web server.
- **10:30 AM:** Database team notified and escalated the issue.
- **10:45 AM:** Identified that the database connection pool was exhausted.
- **11:00 AM:** Began optimizing the slow query and increasing the connection pool size.
- **11:30 AM:** The issue was resolved, and services returned to normal.

## Root Cause and Resolution

- **Root Cause:** An inefficient query caused the database connection pool to be exhausted, leading to a backlog of queries and degraded performance.
- **Resolution:** Optimized the query by adding appropriate indexes and increased the connection pool size to handle higher loads.

## Corrective and Preventative Measures

- **Improvements:** 
  - Regularly review and optimize database queries.
  - Implement better monitoring on database connection pool usage.
  - Increase the size of the connection pool and set up alerts when it reaches a threshold.

- **TODO List:**
  - [ ] Patch the database with optimized queries.
  - [ ] Add monitoring for database connection pool usage.
  - [ ] Schedule a review of the database performance every quarter.

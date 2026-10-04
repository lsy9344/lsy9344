# Delivery Operations Monitoring Platform

**Commercial product · Private source · MRR: USD 1,000 (October 2026)**

I built and operate a delivery-operations platform for teams that need timely visibility into delivery performance without repeatedly copying information from browser dashboards into group messages.

## Business problem

Delivery-center managers need to see performance and cancellation signals, recognize exceptions, and communicate actions to their teams. Manual collection is repetitive, easy to duplicate, and difficult to recover when a browser session, schedule, or network request fails.

The product turns those recurring steps into a controlled workflow. It collects operational data from authenticated browser sessions, checks whether the result belongs to the expected center and time window, and sends scheduled updates through team communication channels. The result is faster operational awareness with fewer inconsistent handoffs.

## Product architecture

The system uses a hybrid design:

- A local Windows agent performs authenticated browser work and messaging close to the operator’s existing environment.
- A central API coordinates tenants, agents, schedules, administration and portal access.
- A durable queue and scheduler assign work, prevent duplicate jobs, recover stale leases, and avoid sending a backlog after an outage.
- Scheduled messaging keeps routine updates moving without requiring a manager to repeat the same browser and copy-and-paste process.

This separation keeps browser-specific work local while giving the service a shared place to manage schedules, status and operational rules.

## Reliability and data quality

The product is designed to protect decisions from incomplete or ambiguous data. Collection can reject results when the center identity cannot be verified or when a completeness limit is exceeded. Scheduling uses tenant lifecycle gates, agent affinity, capacity controls and platform circuit breakers. The queue handles expired leases and stale scheduled work through explicit recovery paths.

## Business value

The product gives delivery teams a repeatable operating rhythm: collect, verify, communicate and review. It reduces repetitive coordination, makes exceptions easier to notice, and creates a path from internal automation to controlled customer and rider views.

## Technology

Python, Playwright, Windows automation, FastAPI, SQLAlchemy async, PostgreSQL, Alembic, Jinja2/HTMX, Docker, pytest, mypy and Ruff.

The source is private because it contains operational workflows and business-specific integrations. The architecture, reliability approach and product outcomes can be discussed in a technical interview.

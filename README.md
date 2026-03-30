# WARROOM

**Break it before your users do.**

**LIVE DEMO:** https://warroom-eta.vercel.app/

Click "Start Hosted Demo Mode" to see it in action.

##  Achievement

Winner - Consumer AI Track, Resolution Hack

WARROOM answers one question: what happens when your app breaks?

Simulate the failure, watch the fallout, and plan the fix before anyone notices.

## Why WARROOM Exists

Modern apps ship fast, lean on AI-generated code, and depend on fragile services. Under stress they rarely fail gracefully.

WARROOM keeps teams honest by forcing failure in a controlled environment so they know the cost before it hits customers.

Instead of guessing, WARROOM lets you:

- simulate failure scenarios
- observe real impact on your system
- understand the blast radius instantly
- take action before users are affected

## Who This Is For

### Solo Builders and Founders

If you are building quickly and deploying frequently, WARROOM helps you validate that your system will not break under real-world conditions.

### Developers Using AI-Generated Code

AI tools can generate working code, but not always resilient systems. WARROOM helps ensure that your application behaves correctly when dependencies fail or degrade.

### Teams Preparing for Scale

Before increasing traffic or launching features, WARROOM allows you to stress test critical paths and identify weak points early.

## What WARROOM Does

WARROOM provides a full loop from failure simulation to action:

1. Simulate failures
2. Observe system behavior
3. Understand impact in plain English
4. Get actionable next steps

## Core Features

### Failure Simulation

Trigger container-level failure drills, including:

- Database outage (`DB Down`)
- Latency injection (`Latency Spike`)
- Traffic surge (`Request Flood`)

Each drill manipulates containers, networking, and proxies so the failure is real and repeatable.

### Real-Time System Visibility

WARROOM watches the system and reports:

- application and database status
- success rate vs. failure rate
- response latency (`p95`)
- first-failure timing
- event timeline

Metrics come from live responses captured during the drill.

### MCP-Based Control Plane

The control layer issues container stops, latency injections, and load bursts with full traceability.

### Live Interpretation Layer

Signals become plain English:

- what is happening
- why it matters
- how customers are affected

### Technical Verdict

Post-drill diagnostics summarize:

- what failed
- severity of the failure
- evidence and timeline
- likely cause

### Action Plan for Recovery and Improvement

WARROOM serves up next steps:

- what to fix immediately
- code changes to implement
- long-term resilience work

## Example Scenarios

### Database Outage

Take the database offline and see checkout fail, critical flows degrade, and customer‑facing paths stop.

### Latency Injection

Add delay to database calls and watch response times climb as the user experience degrades.

### Traffic Surge

Flood the system with traffic, observe saturation, latency spikes, and the moment failure thresholds trigger.

## How to Run

### Start the System

```bash
podman compose up
```

### Verify Services

```bash
curl http://localhost:5001/health
curl -X POST http://localhost:5001/checkout -H "Content-Type: application/json" -d '{}'
```

### Run Backend

```bash
cd backend
uvicorn main:app --reload
```

### Run MCP Server

```bash
cd mcp-server
source .venv/bin/activate
uvicorn server:app --port 9100
```

### Open Frontend

```bash
open frontend/index.html
```

## Architecture Overview

- Frontend: HTML, JavaScript, CSS
- Backend: FastAPI
- Control Plane: MCP server (Podman + Toxiproxy)
- Demo Application: Flask + Postgres
- Infrastructure: container-based environment

## 🧪 Demo vs Full System

**Hosted Demo Mode** runs entirely in the browser with curated signals, so the story plays publicly without touching your backend. It is safe for recruiters and founders to explore.

**Local Mode** is the full chaos stack: Podman + MCP + Toxiproxy execute real failure simulations against your services for an accurate blast-radius view.

## Future Direction

- deeper AI-assisted failure analysis
- automated resilience scoring
- CI/CD integration hooks
- support for more failure types and environments

## Summary

WARROOM combines:

- failure simulation
- real-time observability
- human-readable interpretation
- action planning

This delivers one workflow from **failure → understanding → resolution** while keeping recruiters and engineers aligned.

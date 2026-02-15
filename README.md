# Modern SaaS Product Analytics (Event-Driven)

This repository documents a step-by-step journey into modern, event-driven product analytics using Segment-style SaaS data.

The goal of this project is to build strong foundations in product analytics — starting from raw event logs and progressively moving toward meaningful product insights such as activation, engagement, funnels, and retention, following industry-standard methodologies used in 2025–2026.

---

## Project Philosophy

This project prioritizes:
- Correct understanding of event data before metrics
- Clear definitions before calculations
- Product thinking over premature optimization
- Slow, intentional analysis with daily progress

Each notebook focuses on **one core concept**, mirroring how real product analytics work is done in practice.

---

## Dataset Overview

The project uses Segment-style JSON event data representing:
- User identification events (`identify`)
- Behavioral tracking events (`track`)
- Anonymous to known user transitions
- Timestamped user actions with nested metadata

The dataset structure mirrors real-world SaaS analytics pipelines used by tools such as Segment, Mixpanel, and Amplitude.

---

## Progress So Far (Days 1–5)

### Day 1 — Understanding Event Data
- Loaded and inspected raw JSON event logs
- Learned the anatomy of an event (type, user identity, properties, context)
- Differentiated user traits from event properties

### Day 2 — Users, Identity, and Time
- Explored anonymous vs known users
- Understood identity resolution using `anonymousId` and `userId`
- Ordered events chronologically and reasoned about user timelines

### Day 3 — Sessions and User Timelines
- Implemented time-based sessionization
- Assigned session IDs using inactivity thresholds
- Built readable user timelines from raw events

### Day 4 — Activation and Meaningful Events
- Identified which events represent real product value
- Defined activation as a behavioral milestone
- Isolated first activation events per user

### Day 5 — Event Taxonomy and Metric Definitions
- Created a clear event taxonomy
- Defined core product metrics in plain language
- Validated metric logic before computation

### Day 6 — Real-World Dataset Ingestion
- Inspected raw HDFS logs
- Reverse-engineered schema
- Wrote custom regex parser
- Structured 2000 raw logs into a DataFrame
- Created unified timestamp column

### Day 7 — Sessionization
- Sorted events by component and timestamp
- Calculated time gaps
- Defined session boundary (5-minute inactivity rule)
- Assigned session IDs
- Generated session-level metrics:
   - Session duration
   - Event count
 
### Day 8 — Reliability & Instability Analysis
- Discovered:
   - 1920 INFO events
   - 80 WARN events
   - 0 ERROR events
- Key Findings:
   - 4% of all events are WARN-level.
   - All WARN events originate from a single component:
   - dfs.DataNode$DataXceiver
   - ~17.6% of that component’s events are WARN.
   - Indicates localized operational instability rather than systemic failure.
- Performed:
   - WARN rate analysis per component
   - Session-level instability detection
   - Preliminary sequence inspection before WARN events
---

## Methodology

The analysis follows modern product analytics principles:
- Event-driven data modeling
- Explicit activation definitions
- Session-based user behavior analysis
- Clear metric ownership and meaning

Metrics are defined before being calculated to ensure analytical correctness and business relevance.

---

## What’s Next

Starting **Day 9**, the project transitions to:
- Temporal clustering analysis of WARN events
- Sequence modeling before instability
- Anomaly detection
- Visualization of reliability patterns

The foundations established in Days 1–5 will be applied at scale.

---

## Tools Used

- Python 3
- Jupyter Notebook
- pandas
- JSON-based event data

---

## Author Notes

This repository is intentionally built incrementally, with daily commits and documented reasoning, to reflect how strong product analytics skills are developed in real-world environments.

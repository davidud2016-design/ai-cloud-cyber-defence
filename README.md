
AI-driven automated detection and response for cloud-scale cyber
# AI-Driven Cloud Cyber Defence

This project demonstrates the design of an AI-driven cyber defence system
capable of detecting and responding to emerging threats across large-scale
cloud environments (AWS, Azure, GCP).

The focus is on practical security engineering:
1. Behaviour-based detection instead of static rules
2. Risk-based decisioning rather than alert flooding
3. Automated but explainable response mechanisms
4. Continuous learning from analyst feedback

This repository uses pseudocode and architectural patterns rather than
production secrets, and is intended to demonstrate a technical approach,
system design, and hands-on contribution.

---

## High-Level Architecture

Telemetry → Detection → Analysis → Decision → Response → Learning

See `architecture/end_to_end_architecture.txt` for the full flow.

---

## Key Capabilities

- Cloud-native telemetry ingestion
- Behavioural baselining and anomaly detection
- Attack sequence and correlation analysis
- Identity-centric risk scoring (Zero Trust aligned)
- Automated response and containment
- Feedback-driven model improvement

---



## Cloud Platform Alignment

| Capability | AWS | Azure | GCP |
|-----------------------|----------------------|--------------------------|-------------------------|
| Telemetry Ingestion | CloudTrail, Kinesis | Event Hub, Activity Logs | Pub/Sub, Audit Logs |
| ML Inference | SageMaker | Azure ML | Vertex AI |
| Identity Control | IAM, Cognito | Entra ID | Cloud Identity |
| Response Automation | Step Functions | Logic Apps | Workflows |

## Telemetry Ingestion

This module represents the cloud-native ingestion layer responsible for
collecting security-relevant telemetry from AWS, Azure, and GCP.

Responsibilities:
- Normalise heterogeneous cloud event schemas
- Enrich events with identity, asset, and geographic context
- Publish events to a real-time stream for downstream AI analysis

This layer is designed to operate at high volume and low latency.


## Detection Layer

This module contains behaviour-based detection logic designed to identify
deviations from normal activity across identities, services, and workloads.

Key concepts:
- Entity-centric behavioural baselining
- Unsupervised and semi-supervised anomaly detection
- Low false-positive bias through contextual modelling

Detections produced here are forwarded to the risk scoring engine for
correlation and prioritisation.

## Event Sequence & Attack-Chain Analysis
 -------------------------------------
 Purpose:
 Detect multi-stage attack behaviour by correlating
 security events over time for a given entity.

 Sequence Construction Phase
GROUP security_events BY entity WITHIN time_window

 Sequence Analysis Phase
FOR each event_sequence:
    analyse event order and timing

    IF sequence matches known attack pattern:
        generate correlated security alert
        Attach supporting events for investigation
 -------------------------------------
## Purpose:
- Detect multi-stage attack behaviour by correlating
- security events over time for a given entity.

- Sequence Construction Phase
GROUP security_events BY entity WITHIN time_window

- Sequence Analysis Phase
FOR each event_sequence:
    analyse event order and timing

    IF sequence matches known attack pattern:
        generate correlated security alert
        attach supporting events for investigation

## Risk Scoring Engine

This module aggregates detection outputs from anomaly detection,
sequence analysis, and identity risk models to prioritise threats.

The risk score determines:
- Which threats are escalated automatically
- Which threats require analyst review
- Which threats are logged for learning

This approach reduces alert fatigue while maintaining high
security coverage.

## Automated Response

This module represents the response and containment layer
of the cyber defence system.

Responses are:
- Risk-based and severity-driven
- Designed to minimise blast radius
- Integrated with identity and cloud controls

Human oversight is retained for critical decisions.

## Feedback & Continuous Learning

This module represents the learning loop that enables
continuous improvement of detection quality.

Analyst feedback is treated as ground truth to:
- Refine behavioural baselines
- Tune detection thresholds
- Improve risk scoring accuracy

This ensures the system adapts to evolving threats
and changing environments.


## Disclaimer

This project is for architectural and educational purposes and does not
contain production credentials, customer data, or sensitive detection logic.

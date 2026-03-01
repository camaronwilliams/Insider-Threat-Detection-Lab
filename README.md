# Insider-Threat-Detection-Lab
# Lab – Insider Threat Detection

## Goal
Identify anomalous user activity and risk escalation indicators and classify for further investigation.

## Data sources
- Windows authentication events (4624, 4625)
- Privileged logon activity (4672)
- Simulated/sanitized data

## Detection logic (plain English)
Score insider risk using multiple signals within the same time window. Escalation occurs when indicators chain together:
- Failures → success
- After-hours activity
- New host/IP usage
- Privileged activity shortly after suspicious authentication

## Risk scoring (example)
- Fail→Success: +40  
- After-hours: +20  
- New host/IP: +25  
- Privileged activity: +30  
- Threshold: 70+ = escalate for deeper investigation

## Tuning / noise reduction
- Increase thresholds for noisy users/service accounts
- Add allowlists for approved admin/on-call workflows
- Add throttling/suppression to prevent repeat alerts
- Enrich with user/asset context when available

## Evidence
See `screenshots/` for the risk table output and the per-user timeline pivot.

## Next steps (in a real environment)
- Validate business context (on-call/travel/role change)
- Confirm asset sensitivity and scope
- Check for follow-on actions (file access, uploads, suspicious tooling)
- Preserve evidence and document findings

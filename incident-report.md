# Incident Report Analysis

**Case file:** 001 — ICMP Flood DoS Attack  
**Context:** Simulated multimedia services company  
**Course:** Google Cybersecurity Professional Certificate — Course 3  
**Method:** NIST Cybersecurity Framework (five-function course model)  
**Status:** Working draft for learner review

## 1. Security event summary

A multimedia company offering web design, graphic design, and social media marketing services experienced a denial-of-service (DoS) attack. A malicious actor flooded the internal network with Internet Control Message Protocol (ICMP) packets. Network services became unresponsive, preventing normal internal traffic from reaching network resources for approximately two hours.

The incident management team blocked incoming ICMP packets, took non-critical services offline, and restored critical network services. A subsequent investigation identified an unconfigured firewall as the weakness that permitted excessive incoming traffic. The security team then introduced ICMP rate limiting, source-IP verification, traffic monitoring, and IDS/IPS filtering.

**Observed impact:** Disruption of network availability. No data theft, account compromise, or additional damage is established in the scenario.

## 2. Identify

**Attack:** ICMP packet flood resulting in a denial of service. The case does not establish a distributed attack, so it should not be labeled DDoS.

**Assets affected:** Internal network and services that depend on network connectivity; exact hosts and service dependencies are not identified.

**Vulnerability:** Inadequate firewall configuration allowed the incoming ICMP flood to overwhelm the network.

**Recommended assessment:** Review internet-facing paths, configuration baselines, firewall policies, critical assets, and the business functions most sensitive to downtime. Document legitimate ICMP requirements before making permanent restrictions.

## 3. Protect

**Controls implemented in the scenario:**

- Incoming ICMP rate-limiting rule.
- Source IP address verification to help detect spoofing.
- Network monitoring software.
- IDS/IPS filtering for suspicious ICMP characteristics.

**Additional recommendations:** Implement a documented firewall change and approval process; periodically audit rules and thresholds; enforce least-privilege access to configuration changes; and determine whether the internet service provider or upstream protections are needed for traffic volumes exceeding local network capacity. Avoid indiscriminately disabling all ICMP, which can interfere with legitimate diagnostics and network operations.

## 4. Detect

Establish baselines for ordinary ICMP volume and overall network performance. Configure alerts for unusual bursts, abnormal packet rates, spikes from unexpected sources, and anomalous network utilization. Centralize firewall, router, IDS/IPS, and network performance logs in a monitoring platform or SIEM where available. Record timestamps, duration, affected services, and alert details. Tune rules to reduce false positives without hiding meaningful activity.

## 5. Respond

**Actions taken:** The response team blocked inbound ICMP packets, suspended non-critical services, and restored critical network functionality.

**Future procedure:**

1. Validate whether anomalous traffic is malicious or an operational issue.
2. Notify the incident lead and classify impact to availability.
3. Preserve relevant logs and packet captures if available before evidence is overwritten.
4. Apply narrowly scoped filtering or rate limits and, if needed, engage the internet service provider for upstream filtering.
5. Track each action, decision, system impact, and stakeholder communication.
6. Reassess traffic and service status before ending containment.

## 6. Recover

Restore critical network services first; verify connectivity, service availability, and user access; then restore non-critical services in a controlled manner. Ensure mitigation rules do not block valid traffic. Continue heightened monitoring for renewed flooding. Document service restoration times and hold a lessons-learned review to improve baselines, detection rules, incident playbooks, and recovery procedures.

## 7. Recommended controls and validation

| Control | Priority | Example verification evidence |
| --- | --- | --- |
| ICMP rate-limiting rules | High | Approved configuration and authorized test results showing excessive traffic is limited while legitimate operations continue |
| Firewall configuration review | High | Reviewed rule set and documented approval of required inbound traffic |
| Monitoring and IDS/IPS tuning | High | Documented thresholds, sample alerts, and escalation instructions |
| Response and recovery exercise | Medium | Tabletop exercise notes, restoration checklist, and remediation tracking |

## 8. Evidence gaps and cautions

The fictional case gives no raw logs, source IP addresses, captures, measured network load, confirmed root-cause artifacts, full asset inventory, or quantified financial losses. Analysts must not infer attacker identity or customer data loss from the provided description. Source-IP checks can identify inconsistencies but do not independently prove identity; local firewall rules may be insufficient if malicious traffic saturates an upstream connection.

## 9. Learning reflection

This case illustrates that incident response should be paired with prevention, monitoring, documentation, and validation. Incident reports need to clearly separate observations from proposed controls and avoid unsupported claims.

---

*Educational case study based on the Google Cybersecurity Professional Certificate's Course 3 portfolio scenario. No real environment was tested.*

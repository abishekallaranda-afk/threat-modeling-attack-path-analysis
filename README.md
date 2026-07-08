# Threat Modeling & Attack Path Analysis

Adversary behavior modeling and early threat detection using reconnaissance datasets, structured around common attack-path frameworks.

## Objective

Reactive alerting alone misses slow-moving, low-and-slow attacks. This project models plausible attacker paths through an environment — from initial reconnaissance to objective — to identify detection gaps before they're exploited.

## Approach

1. **Asset & entry-point mapping** — catalogued external-facing assets and likely reconnaissance targets (DNS records, exposed services, public-facing applications).
2. **Threat actor modeling** — used a kill-chain / MITRE ATT&CK-style framework to map plausible attacker techniques at each stage (reconnaissance → initial access → lateral movement → objective).
3. **Attack path construction** — built attack-path diagrams showing how an adversary could chain together low-severity findings (e.g., an exposed service + weak credential policy + excessive privilege) into a high-impact compromise.
4. **Detection gap analysis** — for each step in the modeled attack path, checked whether existing monitoring (SIEM correlation rules, endpoint telemetry) would actually generate an alert.
5. **Reconnaissance dataset review** — analyzed passive recon data (DNS, WHOIS, exposed ports/services) to identify what an external attacker could learn about the environment before ever sending a packet.

## Example Attack Path (Illustrative)

```
1. Recon: Passive DNS enumeration reveals exposed admin subdomain
2. Initial Access: Weak/default credentials on exposed admin panel
3. Privilege Escalation: Over-permissioned service account discovered
4. Lateral Movement: RDP/SSH reuse across segmented hosts
5. Objective: Access to sensitive data store
```
*(Illustrative example built for training/demonstration purposes — not a real environment.)*

## Outcomes

- Identified detection gaps where a modeled attack path would not have triggered any existing alert
- Informed prioritization of new correlation rules to close the highest-risk gaps first
- Reinforced a proactive, adversary-perspective approach alongside reactive SOC alert triage

## Tools

MITRE ATT&CK framework, passive reconnaissance tools (DNS/WHOIS lookups), Splunk (detection gap validation)

---
*Note: This write-up describes methodology and illustrative examples only. No proprietary employer data or real environment details are included.*

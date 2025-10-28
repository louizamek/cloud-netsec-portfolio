# 01 — On-Prem Security Lab
**Goal:** build a tiny home “SOC” to observe real network traffic and security alerts.

## What’s inside
- **pfSense** – router/firewall to segment the lab
- **Suricata** – IDS/IPS that inspects packets with rules
- **Zeek** – network metadata (who talked to who, DNS/HTTP details)
- **Wazuh** – SIEM/EDR to collect logs and raise alerts

## Architecture (simple)
Client VM  ──>  LAN  ──>  pfSense  ──>  WAN/Internet
                    │
               (mirror/SPAN)
                    │
       Suricata + Zeek sensor
                    │
                Wazuh mgr

## How to use this folder
- `diagrams/` — draw.io diagram (.drawio + .png)
- `suricata/` — config + rules
- `zeek/` — local.zeek config + sample logs
- `wazuh/` — docker-compose or install notes
- `samples/` — pcaps and example logs (sanitized)

## Tasks (checklist)
- [ ] Diagram: add **topology.drawio** + **topology.png** in `diagrams/`
- [ ] Suricata: minimal `suricata.yaml` + `rules/custom.rules` (1 custom rule)
- [ ] Zeek: `local.zeek` enabling dns/http; run Zeek on a small pcap
- [ ] Wazuh: start manager; forward Suricata & Zeek logs
- [ ] Evidence: save 1 pcap + 3 example logs to `samples/`
- [ ] Findings: write 3 bullets under **Results** below

## Results (fill as you go)
- Example: “Suricata alerted on Nmap SYN scan from 10.0.0.5 to 10.0.0.10”
- Example: “Zeek DNS logs show queries to suspicious domain `test.bad`”
- Example: “Wazuh rule 5710 fired on Suricata high-priority event”

# LabubaRAT / LabubaPanel — C2 Intelligence

> July 15, 2026 · Ares-sys
> Source: Blackpoint Cyber (Jul 14, 2026) + own recon

---

## SAMPLE

| Field | Value |
|-------|-------|
| Name | nvidia-sysruntime.exe |
| Type | Rust RAT, Windows x64 GUI, unsigned |
| Compiled | 2026-06-17 23:16:55 UTC |
| Build user | `funt` (C:\Users\funt\.cargo\registry\...) |
| PDB | nvidia_container.pdb |
| SHA256 | 8c4e4804f21649e5ddc6a5670f3b3828a43bff304f02f184f9842c2569570f3d |
| Mutex | Local\NVIDIAContainerMonitor_SingleInstance |
| Local DB | nvctr_sys.db (SQLite) |
| Config namespace | ZM_ prefixed |
| Status | NOT available on VT/MB/Triage yet (Jul 15) |

---

## CAPABILITIES

- Execution: shell, PowerShell, JavaScript
- Exfiltration: upload/download files, screenshots
- Proxy: SOCKS5
- Persistence: HKCU Run (user-level)
- Communication: HTTPS polling + WebView2 + DNS tunneling
- Evasion: profiles 16 security products (CrowdStrike, S1, CB, Sophos, MB, Bitdefender, ESET, Kaspersky, McAfee, Symantec, Trend Micro, Defender)
- Model: MaaS (malware-as-a-service)

---

## C2 — LABUBAPANEL

| Field | Value |
|-------|-------|
| URL | https://pipicka.xyz/ |
| Title | LabubaPanel |
| Cloudflare IPs | 188.114.96.3, 188.114.97.3, 172.67.155.109 |
| Domain created | June 1, 2026 |
| Registrar | Global Domain Group LLC (bulletproof) |
| Nameservers | anastasia.ns.cloudflare.com, troy.ns.cloudflare.com |
| TLS | WE1 (Google Trust), issued Jun 1 2026, expires Sep 2026 |
| Frontend | React + Vite + Inter font |
| Backend | Python FastAPI (`{"detail":"Not Found"}`) |
| Assets | JS/CSS → 502 (origin down or not deployed) |
| Favicon | /images/app-icon.png (88KB, 934x972 PNG) |
| Analytics | Cloudflare Browser Insights |
| Google Fonts | fonts.googleapis.com (Inter 300-800) |

---

## ENDPOINTS TESTED

All return FastAPI 404 or SPA catch-all:

/api/, /api/v1/, /api/auth, /api/login, /api/agents, /api/tasks, /api/panel
/admin, /docs, /openapi.json, /swagger
/api/v1/agent/register (POST), /api/v1/enroll (POST)

→ Real API only extractable from JS bundle (currently down)

---

## NEXT STEPS

1. Monitor JS bundle — when it returns, extract endpoints
2. Subdomain discovery: api.pipicka.xyz, panel.pipicka.xyz, c2.pipicka.xyz
3. Historical DNS (SecurityTrails) for pre-Cloudflare IPs
4. Favicon hash on Shodan to find other Labuba panels
5. Historical WHOIS of domain and registrant
6. Wait for MalwareBazaar/Triage to have the sample

---

## IoCs

```
SHA256: 8c4e4804f21649e5ddc6a5670f3b3828a43bff304f02f184f9842c2569570f3d
SHA256: b7443b0ab48d2f5786d1b6f3a580f02621e9ae5a3877ee3a44e01df13d984328
MD5: d8bf355a198fb5db3ea65cfdfcdfbd19
Domain: pipicka[.]xyz
IPs: 188.114.96[.]3, 188.114.97[.]3, 172.67.155[.]109
Mutex: Local\NVIDIAContainerMonitor_SingleInstance
Build user: funt
```

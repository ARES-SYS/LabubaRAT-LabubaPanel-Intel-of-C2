d# LabubaRAT / LabubaPanel — Intel de C2

> 15 Julio 2026 · Ares-sys
> Fuente: Blackpoint Cyber (14 Jul 2026) + recon propio

---

## MUESTRA

| Campo | Valor |
|-------|-------|
| Nombre | nvidia-sysruntime.exe |
| Tipo | Rust RAT, Windows x64 GUI, unsigned |
| Compilado | 2026-06-17 23:16:55 UTC |
| Build user | `funt` (C:\Users\funt\.cargo\registry\...) |
| PDB | nvidia_container.pdb |
| SHA256 | 8c4e4804f21649e5ddc6a5670f3b3828a43bff304f02f184f9842c2569570f3d |
| Mutex | Local\NVIDIAContainerMonitor_SingleInstance |
| DB local | nvctr_sys.db (SQLite) |
| Config namespace | ZM_ prefixed |
| Estado | NO disponible en VT/MB/Triage aún (15 Jul) |

---

## CAPACIDADES

- Ejecución: shell, PowerShell, JavaScript
- Exfiltración: upload/download files, screenshots
- Proxy: SOCKS5
- Persistencia: HKCU Run (user-level)
- Comunicación: HTTPS polling + WebView2 + DNS tunneling
- Evasión: perfila 16 security products (CrowdStrike, S1, CB, Sophos, MB, Bitdefender, ESET, Kaspersky, McAfee, Symantec, Trend Micro, Defender)
- Modelo: MaaS (malware-as-a-service)

---

## C2 — LABUBAPANEL

| Campo | Valor |
|-------|-------|
| URL | https://pipicka.xyz/ |
| Title | LabubaPanel |
| IPs Cloudflare | 188.114.96.3, 188.114.97.3, 172.67.155.109 |
| Dominio creado | 1 Junio 2026 |
| Registrar | Global Domain Group LLC (bulletproof) |
| Nameservers | anastasia.ns.cloudflare.com, troy.ns.cloudflare.com |
| TLS | WE1 (Google Trust), issued 1 Jun 2026, expires Sep 2026 |
| Frontend | React + Vite + Inter font |
| Backend | Python FastAPI (`{"detail":"Not Found"}`) |
| Assets | JS/CSS → 502 (origin caído o no desplegado) |
| Favicon | /images/app-icon.png (88KB, 934x972 PNG) |
| Analytics | Cloudflare Browser Insights |
| Google Fonts | fonts.googleapis.com (Inter 300-800) |

---

## ENDPOINTS PROBADOS

Todos devuelven 404 FastAPI o SPA catch-all:

/api/, /api/v1/, /api/auth, /api/login, /api/agents, /api/tasks, /api/panel
/admin, /docs, /openapi.json, /swagger
/api/v1/agent/register (POST), /api/v1/enroll (POST)

→ API real solo extraíble del JS bundle (caído)

---

## PRÓXIMOS PASOS

1. Monitorear JS bundle — cuando vuelva, extraer endpoints
2. Subdomain discovery: api.pipicka.xyz, panel.pipicka.xyz, c2.pipicka.xyz
3. Historical DNS (SecurityTrails) para IPs previas a Cloudflare
4. Favicon hash en Shodan para encontrar otros panels Labuba
5. WHOIS histórico del dominio y registrant
6. Esperar que MalwareBazaar/Triage tengan el sample

---

## IoCs

```
SHA256: 8c4e4804f21649e5ddc6a5670f3b3828a43bff304f02f184f9842c2569570f3d
SHA256: b7443b0ab48d2f5786d1b6f3a580f02621e9ae5a3877ee3a44e01df13d984328
MD5: d8bf355a198fb5db3ea65cfdfcdfbd19
Dominio: pipicka[.]xyz
IPs: 188.114.96[.]3, 188.114.97[.]3, 172.67.155[.]109
Mutex: Local\NVIDIAContainerMonitor_SingleInstance
Build user: funt
```

# Cory's Homelab

A self-hosted homelab built for learning, experimentation, media, game servers, monitoring, and hosting web services.

<p align="center">
  <!-- Replace with homelab/dashboard photo -->
  <img src="imgs/homelab.png" width="48%" alt="Homelab">
  <img src="imgs/dashboard.png" width="48%" alt="Homelab Dashboard">
</p>

## Hardware

| Machine | Hardware | Role |
|---|---|---|
| **Pi** | Raspberry Pi 4 · 4 GB | Monitoring, DNS & dashboard |
| **cp1** | Dell OptiPlex 5050 · i5-7600T · 16 GB | Minecraft, websites & web services |
| **cp2** | Dell OptiPlex 5050 · i5-7500T · 16 GB | Jellyfin media server |

All systems run **Ubuntu Server** and are connected over Gigabit Ethernet.

## Services

### Pi
- Pi-hole
- Prometheus
- Grafana
- Uptime Kuma
- Custom Homelab Dashboard
- HDMI status display
- Tailscale

### cp1
- Custom Minecraft Server Manager
- Vanilla / Fabric / Forge servers
- Automatic & manual Minecraft backups
- Public Minecraft hosting
- Web services
- RaceTrace backend
- ngrok
- Node Exporter
- Tailscale

### cp2
- Jellyfin
- Intel Quick Sync / VA-API hardware transcoding
- Movies, TV & music storage
- Node Exporter
- Tailscale

## Minecraft

The custom Minecraft manager provides:

- Create/delete servers
- Vanilla, Fabric & Forge support
- Multiple Minecraft versions
- RAM allocation
- Start/stop controls
- Live console & commands
- `server.properties` editor
- Multiple simultaneous servers
- Automatic and manual backups

Live server data is stored on NVMe, while backups are stored separately on HDD.

## Networking

```text
Internet
   │
   ├── HTTP :80 ───────────────► cp1 Web Services
   ├── Minecraft :25565+ ──────► cp1 Minecraft Servers
   └── ngrok ──────────────────► Selected Web Services

Tailscale
   │
   ├── Homelab Dashboard
   ├── Minecraft Manager
   ├── Grafana / Prometheus
   ├── Uptime Kuma
   ├── Jellyfin
   └── SSH
```

Administrative services remain private through **Tailscale**, while selected game servers and web services can be exposed publicly.

## Storage

```text
cp1
├── NVMe ── Minecraft servers / applications
└── HDD  ── Minecraft backups

cp2
├── NVMe ── Ubuntu / Jellyfin
└── HDD  ── Movies / TV / Music
```

## Monitoring

Prometheus + Node Exporter collect metrics from every machine.

Grafana, Uptime Kuma, and the custom dashboard provide:

- CPU & RAM usage
- Disk usage
- Server uptime
- Service status
- Minecraft status
- Jellyfin status
- Network/service availability

---

Built as an ongoing project to learn **Linux, networking, server administration, monitoring, self-hosting, and infrastructure development**.

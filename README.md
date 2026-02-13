# NetLab Architect

**Free, open-source homelab network diagram builder with realistic device configuration.**

A drag-and-drop visual network topology tool built for homelabbers, sysadmins, and networking enthusiasts. Think Cisco Packet Tracer meets draw.io — but purpose-built for homelab documentation.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)
![Zero Dependencies](https://img.shields.io/badge/dependencies-zero-green.svg)

<a href="https://www.buymeacoffee.com/netlabarchitect" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="40"></a>

---

## Features

### Visual Diagram Builder
- **Drag & drop** 40+ network components onto an infinite canvas
- **Smooth panning & zooming** — scroll to zoom, click-drag to pan
- **Bezier curve connections** with proper routing between nodes
- **SVG device icons** — crisp at any zoom level
- **Snap-to-grid** for clean, aligned diagrams

### Realistic Device Configuration (Packet Tracer-style)
- **70+ real-world devices** from Cisco, Ubiquiti, MikroTik, TP-Link, Fortinet, Netgate, Dell, HPE, Synology, QNAP, and more
- **Device selector modal** — search and filter by brand, see port previews before placing
- **Front panel SVG rendering** — see actual port layouts on every device (thumbnail on canvas, interactive in properties panel)
- **Per-port configuration** — click any port to configure:
  - Status (Up / Down / Disabled)
  - IP Address & Subnet
  - VLAN Mode (Access / Trunk), VLAN ID, Allowed VLANs
  - Speed, Duplex, PoE toggle
  - Description and connection info
- **Port-specific connections** — assign physical ports when connecting devices, with port labels on connection lines

### Device Database

| Category | Count | Brands |
|----------|-------|--------|
| **Routers** | 11 | Cisco ISR, Ubiquiti EdgeRouter, MikroTik, TP-Link, Netgate |
| **Switches** | 14 | Cisco CBS, Ubiquiti USW, MikroTik CRS, NETGEAR, TP-Link |
| **Firewalls** | 8 | Netgate (pfSense), Fortinet FortiGate, Ubiquiti UDM |
| **Access Points** | 8 | Ubiquiti U6, TP-Link EAP, MikroTik cAP, Ruckus |
| **Servers** | 7 | Dell PowerEdge, HPE ProLiant, Supermicro, Lenovo ThinkSystem |
| **NAS** | 8 | Synology DS/RS, QNAP TS, Asustor |
| **Mini PCs** | 6 | Intel NUC, Beelink, Lenovo ThinkCentre, HP EliteDesk |
| **UPS** | 3 | APC, CyberPower |

### Network Components
| Category | Components |
|----------|-----------|
| **Network** | Modem, Router, Firewall, Switch, Access Point, VLAN |
| **Compute** | Server, Proxmox VE, VM, LXC/Docker Container, Mini PC, Raspberry Pi |
| **Storage** | NAS, SSD/HDD |
| **Services** | DNS, VPN, Reverse Proxy, Docker Host, Home Assistant, n8n, Pi-hole |
| **Endpoints** | Laptop, Desktop, Phone, Smart Device, IP Camera, Printer, Smart TV |
| **Infrastructure** | Internet/ISP, Cloud, Server Rack, UPS, Patch Panel, Text Labels |

### Cable Types
Cat 5e, Cat 6, Cat 6a, Cat 7, Cat 8, Fiber SM, Fiber MM, SFP+, USB, WiFi, Bluetooth, Zigbee — each with unique visual styling.

### Built-in IP Subnet / CIDR Calculator
- Enter any IPv4 address + CIDR prefix
- Instantly see: network address, broadcast, first/last host, usable hosts, wildcard mask, IP class, binary mask

### Smart Features
- **Auto Layout** — one-click arrange all nodes by category
- **Undo / Redo** (Ctrl+Z / Ctrl+Y) with 50-step history
- **Copy / Paste / Duplicate** nodes (Ctrl+C/V/D)
- **Right-click context menu** for quick actions
- **Search & filter** components in sidebar
- **Auto-save** to localStorage — your diagram persists across sessions
- **Minimap** for navigating large diagrams

### Themes
- **Dark Mode** — default, easy on the eyes for late-night lab sessions
- **Light Mode** — clearly labeled toggle button in the toolbar

### Export Options
- **JSON** — save/load full diagram with all device and port data
- **PNG** — high-res 2x export for documentation
- **PDF** — via browser print dialog

### Multiple Views
- **Physical** — hardware topology and connections
- **Logical** — network segmentation and services
- **IP Map** — address-focused view

---

## Quick Start

### Option 1: Just Open It
Download `public/index.html` and open in any browser. That's it. **Zero dependencies.**

### Option 2: Serve Locally
```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/netlab-architect.git
cd netlab-architect

# Serve with any static file server (pick one):
npx serve public
# or
python3 -m http.server 8080 -d public
# or
php -S localhost:8080 -t public
```
Then open http://localhost:8080.

### Option 3: Docker
```bash
# Using docker-compose (recommended)
git clone https://github.com/YOUR_USERNAME/netlab-architect.git
cd netlab-architect
docker compose up -d

# Or standalone
docker run -d -p 8080:80 -v $(pwd)/public:/usr/share/nginx/html:ro nginx:alpine
```
Then open http://localhost:8080.

### Option 4: GitHub Pages
1. Fork this repo
2. Go to **Settings** > **Pages**
3. Source: **GitHub Actions**
4. The included workflow will auto-deploy on push to `main`

---

## How to Use

1. **Drag a component** from the left sidebar onto the canvas
2. **Choose a device model** — for routers, switches, firewalls, etc., a device selector pops up with real-world models (or skip with "Use Generic Device")
3. **Click a node** to open the properties panel — fill in IP, hostname, model, etc.
4. **Click ports on the front panel** (in the properties panel) to configure individual ports — set IP, VLAN, speed, PoE, etc.
5. **Connect nodes** by clicking on a port dot (on node edges) and dragging to another node's port
6. **Assign physical ports** — when connecting device-model nodes, a dialog lets you pick which physical ports to link
7. **Double-click a connection** to set label, cable type, and bandwidth
8. **Right-click a connection** to delete it
9. **Use Auto Layout** to organize nodes automatically
10. **Export** as JSON (to reload later), PNG, or PDF

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+Z` | Undo |
| `Ctrl+Y` | Redo |
| `Ctrl+S` | Save diagram (JSON) |
| `Ctrl+C` | Copy selected node |
| `Ctrl+V` | Paste node |
| `Ctrl+D` | Duplicate node |
| `Delete` | Delete selected node |
| `Escape` | Deselect all / close panels |
| `Scroll` | Zoom in/out |
| `Click+Drag` (canvas) | Pan |
| `Click+Drag` (node) | Move node |

---

## Project Structure

```
netlab-architect/
├── public/
│   └── index.html          # The entire app — single file, zero dependencies
├── .github/
│   └── workflows/
│       └── deploy.yml       # GitHub Pages auto-deploy
├── Dockerfile               # Nginx-based container
├── docker-compose.yml       # One-command Docker setup
├── LICENSE                  # MIT
└── README.md
```

---

## Contributing

Contributions are welcome! Here's how:

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -m 'Add amazing feature'`
4. Push: `git push origin feature/amazing-feature`
5. Open a Pull Request

### Feature Ideas (PRs Welcome!)
- [ ] Multi-select & group move
- [ ] Subnet visualization overlay
- [ ] Import from Nmap scan
- [ ] Custom device icons (upload SVG)
- [ ] Collaboration (real-time multi-user)
- [ ] Network simulation / ping test
- [ ] Template diagrams (home network, small office, etc.)
- [ ] Export to draw.io format
- [ ] Mobile touch support
- [ ] More devices in the database

---

## Support the Project

If NetLab Architect helps you document your homelab, consider supporting development:

<a href="https://www.buymeacoffee.com/netlabarchitect" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" height="50"></a>

Or just give the repo a star — it helps others find the project!

---

## License

MIT License — free for personal and commercial use. See [LICENSE](LICENSE) for details.

---

## Credits

Built for the homelab community.

- Inspired by Cisco Packet Tracer, draw.io, and Excalidraw
- SVG icons designed for network topology visualization
- 70+ real-world device specs sourced from manufacturer documentation
- Built as a single HTML file — no frameworks, no build tools, no dependencies

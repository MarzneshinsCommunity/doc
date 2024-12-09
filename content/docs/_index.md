---
title: Overview
linkTitle: "Documentation"
next: docs/Getting-started
---

Marzneshin is a censorship circumvention tool utilizing other censorship circumvention tools.

Marzneshin controls the [Marznodes](https://github.com/marzneshin/marznode)
connected to it; monitoring/disabling/enabling users on marznode instances while
marznode manages and interacts with vpn backends (such as xray).

{{< callout type="warning" >}}
   Please note that this is not an official document, and any issues encountered are your responsibility.
{{< /callout >}}

{{< cards  cols="1">}}
  {{< card link="getting-started" title="Getting Started" icon="document-text">}}
{{< /cards >}}

### Features

- **Web UI** Dashboard
- **Multi Nodes** support for traffic distribution, scalability, and fault tolerance
- Supports protocols **Vmess**, **VLESS**, **Trojan** and **Shadowsocks** as provided by xray
- **Multi-protocol** for a single user
- Manage users' access to inbounds separately using **services**
- **Multi-user** on a single inbound
- Limit users' data and set expire dates
- Reset traffic periodically (daily, weekly,...)
- **Subscription link** compatible with **V2ray** (e.g. V2RayNG, OneClick, Nekoray, etc.), **Clash** and **ClashMeta**
- Automated **Share link** and **QRcode** generator
- System, nodes, traffic statistics, users monitoring
- Integrated **Command Line Interface (CLI)**
- [**Multi-admin** support](https://github.com/marzneshin/marzneshin/issues/73) (WIP)
- Marzneshin is decoupled from VPN backends
- Resilient and fault tolerant node management

**Deployment and Developer Kit:**

- REST-full API
- Kubernetes and multiple deployment strategy and options (WIP)

### marznode

[marznode](https://github.com/marzneshin/marznode) is the backend needed to run proxy servers.

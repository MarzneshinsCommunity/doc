---
title: Overview
linkTitle: "Overview"
next: docs/basic-install
weight: 1
---

Marzneshin is a tool that manages [Marznodes](https://github.com/marzneshin/marznode) for censorship circumvention. It controls user access and interacts with VPN backends like xray.

{{< callout type="warning" >}}
   Please note that this is not an official document, and any issues encountered are your responsibility.
{{< /callout >}}

there is two main ways to install Marzneshin Core and Marznode.

{{< cards cols="1">}}
    {{< card link="basic-install" title="Basic Install" icon="puzzle" tag= "Recommended" tagType="error">}}
{{< /cards >}}

{{< cards cols="1">}}
    {{< card link="advanced-install" title="Advanced Install" icon="cog" tag="For Contributors and Professionals" tagType="info">}}
{{< /cards >}}

{{% details title="Features" closed="true" %}}

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

{{% /details %}}



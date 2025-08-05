# 🩺 NetDoctor – Network & Internet Troubleshooting Guide for DevOps Engineers

This knowledgebase is your all-in-one **revision + implementation guide** to troubleshoot network and internet connectivity issues as a **DevOps Engineer**. It helps you identify where things break, how to detect them quickly, and which tools to use.

---

## 🚀 Deliverables / What This Guide Covers

- ✅ Basic to advanced CLI tools for testing connectivity
- ✅ Common troubleshooting scenarios with examples
- ✅ Hands-on commands and file locations
- ✅ OSI & TCP/IP layer-wise mapping
- ✅ Cloud (AWS/GCP/Azure) specific considerations
- ✅ Docker & Kubernetes networking
- ✅ Performance, latency, firewall & DNS checks
- ✅ Monitoring, logging, and diagnostics
- ✅ Real-world case simulations for your GitHub project

---

## ✅ 1. Basic Connectivity Tests (OSI Layer 3 & 4)

| Command | Purpose |
|--------|---------|
| `ping 8.8.8.8` | Test basic network reachability |
| `traceroute google.com` | Trace path to a destination |
| `curl http://example.com` | Check HTTP connection |
| `httping example.com` | HTTP-level ping |
| `telnet google.com 443` | Test TCP port connectivity |
| `nc -zv host port` | TCP port status test |
| `ss -tuln`, `netstat -tuln` | View open/listening ports |

📌 **Use Case**: App can't connect to DB → Check if port is open.

---

## 🧭 2. DNS & Name Resolution (OSI Layer 7)

| Command | Purpose |
|--------|---------|
| `dig domain.com` | Deep DNS record lookup |
| `nslookup domain.com` | Basic name resolution |
| `host domain.com` | Lightweight DNS check |
| `cat /etc/resolv.conf` | DNS server configuration |
| `systemd-resolve --status` | DNS on systemd-based systems |

📌 **Use Case**: Pipeline fails due to DNS error → Misconfigured DNS server.

---

## 🌐 3. IP Address & Routing (Layer 3)

| Command | Purpose |
|--------|---------|
| `ip a` / `ifconfig` | View assigned IP addresses |
| `ip r` / `route -n` | View routing table |
| `ip link` | Interface status (up/down) |
| `nmcli`, `netplan`, `networkctl` | Manage network settings |

📌 **Use Case**: Docker container can't reach Internet → Missing default route.

---

## 🔐 4. Firewall & Security Groups (Layer 4+)

| Tool | Use |
|------|-----|
| `ufw`, `iptables`, `firewalld` | Local firewall configurations |
| AWS Security Groups, Azure NSGs | Cloud network access control |

📌 **Use Case**: Jenkins can't pull repo → Outbound port blocked.

---

## 🌍 5. Proxy, VPN & NAT Issues

| Task | Tools |
|------|-------|
| Check environment proxy | `env | grep -i proxy` |
| Test via proxy | `curl -x proxyhost:port https://example.com` |
| VPN check | `openvpn`, `wg`, `ipsec` logs |
| NAT/Docker routing | `iptables -t nat -L`, `docker network inspect` |

📌 **Use Case**: Proxy blocking external API → Adjust proxy settings or whitelist.

---

## ☁️ 6. Cloud Networking (AWS/GCP/Azure)

| Concept | Description |
|--------|-------------|
| VPC/Subnet | Private IP space management |
| Route Table | Control traffic flow inside cloud |
| Internet/NAT Gateway | Internet access to private subnets |
| Security Groups (SGs) | VM-level firewall |
| Network ACLs | Subnet-level rules |
| Peering/Transit Gateway | Cross-VPC communication |
| PrivateLink | Secure internal service access |

📌 **Use Case**: Lambda fails to call external API → NAT Gateway not linked.

---

## 🐳 7. Docker & Kubernetes Networking

| Tool | Purpose |
|------|---------|
| `docker network ls` | List Docker networks |
| `docker network inspect <name>` | View network config |
| `kubectl exec -it pod -- ping/curl` | Test from inside Pod |
| Network Policies | K8s rules for pod communication |
| CNI Plugins (Flannel, Calico) | Control Pod IP management |

📌 **Use Case**: K8s service unreachable → Misconfigured NetworkPolicy or DNS.

---

## 📊 8. Monitoring & Logging Tools

| Tool | Use |
|------|-----|
| `tcpdump`, `wireshark` | Packet sniffing |
| `iftop`, `nethogs`, `bmon` | Live bandwidth usage |
| CloudWatch, Prometheus, Datadog | Traffic & latency metrics |
| App logs | Track 500 errors, timeouts, etc. |

📌 **Use Case**: High latency → Inspect logs + metrics.

---

## ⚡ 9. Performance & Latency Testing

| Tool | Purpose |
|------|---------|
| `iperf3` | Network throughput testing |
| `mtr` | Combines `ping` + `traceroute` |
| `speedtest-cli` | Quick ISP bandwidth test |

📌 **Use Case**: Slow artifact uploads → Check actual bandwidth.

---

## 🔁 10. Real-World Scenarios for Practice

| Scenario | Tools | OSI Layers |
|----------|-------|------------|
| Website not opening | `ping`, `dig`, `curl` | 3, 7 |
| DB not reachable | `telnet`, `ss`, `netstat` | 4 |
| DNS errors in pipeline | `nslookup`, DNS logs | 7 |
| K8s pod unreachable | `kubectl exec`, NetworkPolicy | 3, 4 |
| VPN blocks repo access | `ping`, `route`, VPN logs | 3 |

---

## 🛠️ Project Idea: `NetDoctor` CLI Tool

A Python-based CLI tool that:

- 📡 Runs all common network diagnostics
- 🧠 Auto-suggests root causes
- 🔧 Provides resolution steps
- 📋 Logs all output with timestamps
- 🌐 Can be expanded to a web dashboard later

---

## 🧠 Summary for Quick Revision

| Area | Must-Know Tools & Concepts |
|------|----------------------------|
| CLI Tools | `ping`, `curl`, `traceroute`, `telnet`, `ss`, `dig`, `ip` |
| DNS | `dig`, `nslookup`, `/etc/resolv.conf` |
| IP & Routing | `ip r`, `ip a`, `nmcli`, `netplan` |
| Firewall | `ufw`, `iptables`, AWS SGs |
| VPN/Proxy | `http_proxy`, `curl -x`, `openvpn`, NAT |
| Cloud | VPC, IGW/NAT, Route Tables, SGs, NACLs |
| Docker/K8s | `docker network`, `kubectl exec`, CNI, Policies |
| Monitoring | `tcpdump`, Prometheus, CloudWatch |
| Testing | `iperf3`, `mtr`, `speedtest-cli` |

---

> 💡 Pro Tip: Practice these tools regularly in a sandbox setup. Try breaking and fixing things intentionally to simulate real-life issues.


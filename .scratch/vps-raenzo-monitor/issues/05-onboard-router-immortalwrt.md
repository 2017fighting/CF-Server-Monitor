# 05: `router`（ImmortalWrt）接入探针

**What to build:** 第二台被监控机器 `router`（ImmortalWrt 25.12.1，x86_64，无 systemd、无 Docker）作为独立服务器出现在面板，指标正常；月流量按实际 WAN 网卡统计，而不是多网卡自动汇总；路由器重启后自动恢复上报。

**Blocked by:** None (can start immediately)

**Status:** ready-for-agent

- [ ] 面板出现 `router` 且在线，CPU、内存、磁盘指标正常
- [ ] 统计网卡明确指向 WAN 口，面板月流量与该网卡自身累计字节数一致
- [ ] 使用适配 OpenWrt（procd）的方式安装并开机自启，不依赖 systemd
- [ ] 重启路由器后两分钟内重新出现在面板并持续上报

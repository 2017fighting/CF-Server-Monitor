# 02: `npm test` 在无 sudo 环境跑绿

**What to build:** 在没有 sudo（包括 CI runner）的机器上执行 `npm test` 全绿。现在 265 条里 1 条失败：前端 WebSocket 生命周期测试启动 Vite 时，mkcert 尝试把根证书写进系统信任库，被 sudo 密码挡住。这条不修，票据 03 的 CI 测试门禁永远红。

**Blocked by:** None (can start immediately)

**Status:** ready-for-agent

- [ ] 无 sudo 的干净环境执行 `npm test`，265/265 通过
- [ ] 原先失败的那条仍覆盖「前端 WebSocket 到达生命周期上限后不重连」，不得删除或弱化测试
- [ ] 证书需求由测试自身解决（自签证书或绕过 https 插件），不要求系统已安装 CA

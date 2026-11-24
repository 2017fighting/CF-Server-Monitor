# 01: Workers 部署 workflow 与线上配置对齐

**What to build:** 给 fork 配好 Cloudflare 凭据后，GitHub Actions 部署出的 Worker 与当前线上实例完全等价：自定义域名、D1 绑定、两条定时任务、Durable Object、`API_USER_NAME` 与 `CORS_ALLOWED_ORIGINS` 全部来自仓库里唯一那份部署配置；`API_SECRET` 仍以 secret 形式存在，不会变成明文变量。任何一次 push 或手动触发，都不该把线上换成一个「没有域名、D1 ID 是占位符」的实例。

**Blocked by:** None (can start immediately)

**Status:** ready-for-agent

- [ ] workflow 不再自己生成部署配置，直接用仓库中已提交的部署配置部署
- [ ] 配齐所需 secret 后手动触发一次，产出的版本与触发前功能等价：首页 200、`/api/servers` 正常、两条定时任务仍在、自定义域名与证书正常
- [ ] 触发后确认 `API_SECRET` 仍是 secret 形式，且没有新增同名明文变量
- [ ] secret 未配置时 workflow 整体跳过，不会误部署
- [ ] 交付说明里写清：fork 需要在 Actions 页面手动启用一次（目前该 fork 上一条 run 记录都没有）

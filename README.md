# Horizon 懒猫微服打包

上游：https://github.com/Thysrael/Horizon （MIT）

AI 驱动的新闻雷达：聚合多源信息，生成中英双语每日简报。

## 打包说明

- 镜像：`ghcr.io/dockers-x/horizon`（由 [dockers-x/horizon](https://github.com/dockers-x/horizon) 自动多架构构建，amd64/arm64）
- 数据持久化：`/lzcapp/var/data` → 容器 `/app/data`
- Horizon 是定时任务型应用（非 Web 服务）：按 `--hours N` 时间窗抓取并生成简报，输出写入数据目录；推送通过 webhook/邮件等渠道
- AI API Key 等配置写入数据目录的 `.env` / `data/config.json`（见上游 README）

## 发布

镜像更新由 dockers-x/horizon 自动跟踪上游 main；本仓库由 [ca-x/lazycat-github-action](https://github.com/ca-x/lazycat-github-action) 镜像模式自动构建 LPK 并发布喵喵商店。

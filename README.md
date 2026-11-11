# scoop-overlay

个人 Scoop 桶（本地桶名 `overlay`）：收录官方桶更新滞后或不收录的软件，由 [Excavator](.github/workflows/excavator.yml) 每 6 小时自动更新 manifest（手动触发：Actions → Excavator → Run workflow）。

```powershell
scoop bucket add overlay https://github.com/sakiko999/scoop-overlay
```

## magpie-ai

[Magpie](https://usemagpie.ai)（[yetone/magpie](https://github.com/yetone/magpie)）的 GitHub rolling 版。官方 `extras` 桶走 stable 通道、更新明显滞后；本桶直接跟随发布仓库 [yetone/magpie-releases](https://github.com/yetone/magpie-releases)。

单包合一：GUI（快捷方式 Magpie AI）+ CLI（`magpie` 命令），共用 Scoop persist 的 `data` 配置目录，预置 `noAutoUpdate`（禁用应用内自更新，统一走 scoop）。

```powershell
scoop install overlay/magpie-ai
```

- **更新前先退出 Magpie**（托盘 → Quit）：运行中 scoop 会静默跳过 install/update/uninstall。
- 日常更新：`scoop update`（刷新桶；`scoop update <app>` 不会拉取 bucket 新提交）→ `scoop update magpie-ai`。
- 从 `extras` 的 magpie-ai 迁移：退出 Magpie → `scoop uninstall magpie-ai` → `scoop install overlay/magpie-ai`（persist 数据自动延续）。
- `extras` 里另有 `magpie`（Blinue/Magpie，窗口放大工具），与本软件无关，勿混淆。
- `scoop uninstall` 不清理应用外部集成（开机自启、`magpie://` 协议、Settings → Command line 写入的用户 PATH）；彻底卸载先在应用内 Settings → Uninstall magpie，或 `magpie uninstall --keep-data` 保留配置。

## steamcommunity-302

[Steamcommunity 302](https://www.dogfight360.com/blog/18682/)（dogfight360）：Steam 社区/商店/下载加速的本地反代工具（hosts / DNS 重定向 / CDN 优选），免费闭源。本桶追踪官方发布页的 Ver 号与直链。

```powershell
scoop install overlay/steamcommunity-302
```

- **更新/卸载前先停止服务并退出**（设置 → 停止服务，托盘退出）：文件被占用时 scoop 会静默跳过。
- Windows Defender 可能因 hosts 修改行为误报 PUA，需手动放行三个文件（notes 里有清单）。
- 302 自带 Windows 全自动更新，与 scoop 管理冲突；建议用 `scoop update` 更新并关闭应用内自动更新（如有选项）。
- 配置/证书/hosts 在应用目录外（`%ProgramData%\Steamcommunity_302`、`%LocalAppData%\S302`），scoop 卸载不会清理，彻底移除按官方页面的完全卸载步骤操作。

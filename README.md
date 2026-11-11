# scoop-magpie-ai

个人 Scoop 桶：追踪 [Magpie](https://usemagpie.ai)（[yetone/magpie](https://github.com/yetone/magpie)）的 GitHub 最新版。

官方 `extras` 桶的 `magpie-ai` 走 stable 通道、更新明显滞后；本桶直接跟随发布仓库 [yetone/magpie-releases](https://github.com/yetone/magpie-releases) 的最新 release，由 [Excavator](.github/workflows/excavator.yml) 每 6 小时自动更新 manifest（手动触发：Actions → Excavator → Run workflow）。

单包合一：GUI（快捷方式 Magpie AI）+ CLI（`magpie` 命令），二者共用 Scoop persist 的 `data` 配置目录，且已预置 `noAutoUpdate`（禁用应用内自更新，统一走 scoop）。

## 使用

```powershell
scoop bucket add magpie-ai-rolling https://github.com/sakiko999/scoop-magpie-ai
scoop install magpie-ai-rolling/magpie-ai
```

若此前安装过 `extras` 的 `magpie-ai`，先完整迁移：

```powershell
# 1. 退出 Magpie（托盘图标 → Quit），并确认无残留进程
Get-Process magpie* -ErrorAction SilentlyContinue
# 2. 卸载 extras 版（persist 数据默认保留，配置自动延续）
scoop uninstall magpie-ai
# 3. 安装本桶版本
scoop install magpie-ai-rolling/magpie-ai
```

注意：**Magpie 在运行时，scoop 的 install/update/uninstall 会被静默跳过**，务必先退出。

## 日常更新

```powershell
scoop update              # 刷新 Scoop 与所有 bucket（scoop update <app> 不会拉取 bucket 新提交）
scoop update magpie-ai
```

## 其他说明

- `extras` 里还有一个 `magpie`（Blinue/Magpie，窗口放大工具），与本软件无关，勿混淆；本桶快捷方式名为 **Magpie AI** 以避免覆盖它的 `Magpie` 快捷方式（如曾被覆盖，`scoop reset magpie` 可恢复）。
- `scoop uninstall` 不会清理应用外部集成（开机自启、`magpie://` 协议、Settings → Command line 写入的用户 PATH）。彻底卸载先在应用内 Settings → Uninstall magpie，只想保留配置可用 `magpie uninstall --keep-data`。

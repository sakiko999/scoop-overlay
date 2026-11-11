# scoop-magpie-ai

个人 Scoop 桶：追踪 [Magpie](https://usemagpie.ai)（[yetone/magpie](https://github.com/yetone/magpie)）的 GitHub 最新版。

官方 `extras` 桶的 `magpie-ai` 走 stable 通道、更新明显滞后；本桶直接跟随发布仓库 [yetone/magpie-releases](https://github.com/yetone/magpie-releases) 的最新 release，由 [Excavator](.github/workflows/excavator.yml) 每 6 小时自动更新 manifest。

单包合一：GUI（快捷方式 Magpie）+ CLI（`magpie` 命令），二者共用 Scoop persist 的 `data` 配置目录，且已预置 `noAutoUpdate`（禁用应用内自更新，统一走 `scoop update`）。

## 使用

```powershell
scoop bucket add magpie-ai-rolling https://github.com/sakiko999/scoop-magpie-ai
scoop install magpie-ai-rolling/magpie-ai
```

若此前安装过 `extras` 的 `magpie-ai`，先 `scoop uninstall magpie-ai` 再安装本桶版本（persist 数据默认保留，配置自动延续）。日常更新：`scoop update magpie-ai`。

注意：`extras` 里还有一个 `magpie`（Blinue/Magpie，窗口放大工具），与本软件无关，勿混淆。

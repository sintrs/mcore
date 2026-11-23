# mcore

上游 [MetaCubeX/mihomo](https://github.com/MetaCubeX/mihomo)（Clash Meta 内核）的**转发仓**。

本仓库**不编译任何东西**，只把上游已经发好的 amd64-v3 包下载下来、改个文件名、重新发布：

| 上游资产 | 本仓库资产 |
|---|---|
| `mihomo-linux-amd64-v3-<tag>.deb` | `mcore-linux-amd64-v3-<tag>.deb` |
| `mihomo-windows-amd64-v3-<tag>.zip` | `mcore-windows-amd64-v3-<tag>.zip` |

二进制与上游逐字节一致，每个 release 正文都附 SHA256，可自行核对。安装后的命令仍是
`mihomo`，包名也是 `mihomo`，配置默认读 `/etc/mihomo`。

## 为什么要这个仓库

只是为了有一个稳定、名字统一的下载入口（`mcore-*`），方便脚本按固定命名规则取包。
上游包名带 `mihomo-` 前缀且同一版本有 `v1 / v2 / v3` 多个变体，脚本里每次拼名字容易出错。

## 自动更新

- `.github/workflows/mirror.yml`：每天 UTC 21:23（北京 05:23）检查上游最新 release，
  本仓库没有该 tag 才转发；已有则跳过。
- 手动触发时可填 `tag`（例如 `v1.19.33`）补发历史版本，或勾 `force` 覆盖已有版本。
- `.github/workflows/keepalive.yml`：每月一次空提交，避免定时任务因 60 天无活动被停用。

## 手动下载

到 [Releases](https://github.com/sintrs/mcore/releases/latest) 页面取当前版本的文件。
文件名形如 `mcore-linux-amd64-v3-v1.19.34.deb`，版本号随上游走：

```bash
TAG=v1.19.34
curl -LO "https://github.com/sintrs/mcore/releases/download/${TAG}/mcore-linux-amd64-v3-${TAG}.deb"
sudo dpkg -i "mcore-linux-amd64-v3-${TAG}.deb"
```

## 与上游的关系

本仓库**不是 fork**，不包含上游源码，也没有对上游代码的任何改动。上游项目版权归
MetaCubeX 及其贡献者，许可证见上游仓库。

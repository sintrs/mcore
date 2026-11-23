# mcore

面向 Linux amd64（v3，即支持 AVX2）与 Windows amd64 的预编译包。

## 文件命名

```
mcore-linux-amd64-v3-<tag>.deb
mcore-windows-amd64-v3-<tag>.zip
```

`<tag>` 是版本号，例如 `v1.19.34`。同一版本只有这两种文件，没有 v1 / v2 等变体，
脚本里按固定规则拼名字即可。

## 安装（Debian / Ubuntu / UOS）

```bash
TAG=v1.19.34
curl -LO "https://github.com/sintrs/mcore/releases/download/${TAG}/mcore-linux-amd64-v3-${TAG}.deb"
sudo dpkg -i "mcore-linux-amd64-v3-${TAG}.deb"
```

## 校验

每个 release 的说明里都附有 SHA256，下载后可对一下：

```bash
sha256sum "mcore-linux-amd64-v3-${TAG}.deb"
```

## 自动更新

- 每天 UTC 21:23（北京 05:23）检查是否有新版本；没有新版本就跳过，不会产生空 release。
- 手动触发时可填 `tag` 补发指定版本，或勾 `force` 覆盖已有版本。
- `keepalive` 每月一次空提交，保证定时任务不因长期无活动被停用。

## 说明

仓库只存放打包好的二进制文件，不含源码。

---
title: podman 安装与卸载
date: 2024-04-09 06:34
---

## 卸载

在 mac 平台完全卸载：

```shell
podman machine stop
podman machine rm
sudo podman-mac-helper uninstall
sudo rm /etc/paths.d/podman-pkg
sudo rm -frv /opt/podman
```

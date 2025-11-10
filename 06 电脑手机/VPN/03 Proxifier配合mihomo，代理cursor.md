---
tags:
  - 软件/VPN
  - Proxifier
  - Cursor
aliases:
  - Proxifier代理Cursor
---
## 问题描述

由于 Cursor 存在区域限制，导致部分地区无法使用 HTTP/2 协议，造成网络连接缓慢。

## 解决方案

通过 **Proxifier** 配合 [[01 Mihomo配置方法|Mihomo]] 代理软件，将 Cursor 相关应用的流量强制通过 SOCKS5 代理协议转发，可以有效解决此问题，恢复正常的访问速度。

![[image 16.png]]
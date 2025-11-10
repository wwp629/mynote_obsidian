---
tags:
  - 问题/软件
  - Windows
  - Microsoft
aliases:
  - Microsoft账户登录报错0x800704cf
  - 解决0x800704cf错误
---

## 问题描述

在 Windows 中登录 Microsoft 账户时，出现错误提示，错误代码为 `0x800704cf`。

## 解决方案

此问题通常与网络代理设置有关，可以通过重置 WinHTTP 代理来解决。

1.  以 **管理员身份** 运行 **PowerShell** 或 **命令提示符 (CMD)**。
2.  输入以下命令并按回车键执行：
<smtcmp_block language="powershell">
netsh winhttp reset proxy
</smtcmp_block>
3.  命令执行完毕后，重启电脑或重新尝试登录 Microsoft 账户。
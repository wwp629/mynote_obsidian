---
tags:
  - 软件/VPN
  - Clash
  - Mihomo
aliases:
  - Mihomo配置
---

## 下载与安装

- **软件名称**：Mihomo
- **官方文档**：[https://clashparty.org/docs/handson](https://clashparty.org/docs/handson)
- **GitHub 地址**：[https://github.com/mihomo-party-org/clash-party](https://github.com/mihomo-party-org/clash-party)

## 首次运行

> [!NOTE] 注意
> 首次运行时需以管理员身份启动，之后即可正常双击打开。

## 详细配置

### 软件设置

无需修改，保持默认设置即可。

### 订阅配置

在 `Sub-Store` 中配置您的订阅地址（请确保使用 Clash 兼容的订阅地址）。

![[image 15.png]]

### 加载订阅

订阅配置完成后，需手动加载相应订阅方可生效。

![[image 1 6.png]]

### 编辑覆写 (Override)

覆写规则用于精细化控制代理行为。

- **覆写规则仓库**：[https://github.com/mihomo-party-org/override-hub](https://github.com/mihomo-party-org/override-hub)

**方法一：通过链接导入**

1.  打开 [ACL4SSR_Online_Full_WithIcon.yaml](https://raw.githubusercontent.com/mihomo-party-org/override-hub/main/yaml/ACL4SSR_Online_Full_WithIcon.yaml) 网址。
2.  在软件的“覆写”设置中，将该网址添加为覆写规则。
![[image 2 6.png]]
3.  根据个人需求修改覆写规则。例如，以下规则用于优化 Cursor 的代理访问，需配合 Proxifier 转换代理协议，详情参考 [[Proxifier配合mihomo，代理cursor]]。
![[image 3 5.png]]
```YAML
+rules:
  - DOMAIN-SUFFIX,api2.cursor.sh,OpenAi
  - DOMAIN-SUFFIX,api3.cursor.sh,OpenAi
  - DOMAIN-SUFFIX,repo42.cursor.sh,OpenAi
  - DOMAIN-SUFFIX,api4.cursor.sh,OpenAi
  - DOMAIN-SUFFIX,marketplace.cursorapi.com,OpenAi
  - DOMAIN-SUFFIX,cursor-cdn.com,OpenAi
  - DOMAIN-SUFFIX,downloads.cursor.com,OpenAi
  - DOMAIN-SUFFIX,anysphere-binaries.s3.us-east-1.amazonaws.com,OpenAi
  - DOMAIN-SUFFIX,release-assets.githubusercontent.com,OpenAi
  - DOMAIN-SUFFIX,github.com,OpenAi
```

**方法二：本地 YAML 文件**

1.  新建一个本地 YAML 规则文件。
2.  将完整的覆写规则代码（例如，从上述链接中获取）复制到文件中。
3.  此方法便于备份和在不同设备间快速迁移配置。

![[image 4 3.png]]

### 代理组设置

代理组的层级配置可以实现智能分流，避免频繁手动切换节点。

- **节点选择**：手动
- **手动切换**：Large 香港01 (选择最常用、最稳定的节点)
- **自动选择**：Large新加坡01 (备用)

![[image 5 3.png]]
![[image 6 3.png]]
![[image 7 3.png]]

例如，下图配置将所有 Cursor 相关流量引导至 `OpenAi` 策略组，该组再指向 `美国节点`，最终由 `Large 美国01` 节点处理。

![[image 8 3.png]]

### 自动更新订阅

设置定时更新，确保节点信息保持最新。

![[image 9 2.png]]
![[image 10 2.png]]

### 自动更新外部资源

设置外部资源（如 GeoIP 数据库）自动更新，以确保分流规则的准确性。

![[image 11 2.png]]

## 日常使用

完成设置后，确保左侧面板的“DNS覆写”和“嗅探覆写”已开启，然后启动“规则”和“系统代理”即可。

通过“连接”面板可以实时查看网络流量走向，便于调试和优化覆写规则。

![[image 12 2.png]]
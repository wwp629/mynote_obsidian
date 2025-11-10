---
tags:
  - 系统/Windows
  - 技巧/系统设置
aliases:
  - Windows11暂停更新
  - Win11暂停更新
---

## 通过注册表暂停 Windows 更新

通过导入一个注册表（`.reg`）文件，可以实现长时间暂停 Windows 更新。

### 操作步骤

1.  创建一个新的文本文档（`.txt`）。
2.  将以下代码完整复制到文档中。
3.  保存文件，并将文件扩展名从 `.txt` 修改为 `.reg`（例如，`PauseUpdates.reg`）。
4.  双击运行该 `.reg` 文件，在弹出的确认窗口中选择“是”，即可将设置导入注册表。

### 注册表代码
<smtcmp_block language="reg">
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsUpdate\UX\Settings]
"FlightSettingsMaxPauseDays"=dword:00001b58
"PauseFeatureUpdatesStartTime"="2023-07-07T10:00:52Z"
"PauseFeatureUpdatesEndTime"="2042-09-05T09:59:52Z"
"PauseQualityUpdatesStartTime"="2023-07-07T10:00:52Z"
"PauseQualityUpdatesEndTime"="2042-09-05T09:59:52Z"
"PauseUpdatesStartTime"="2023-07-07T09:59:52Z"
"PauseUpdatesExpiryTime"="2042-09-05T09:59:52Z"
</smtcmp_block>

### 恢复更新

> [!NOTE] 如何恢复
> 若要恢复自动更新，只需将上述代码中的 `...EndTime` 和 `...ExpiryTime` 的值修改为当前或一个过去的日期，然后重新运行 `.reg` 文件即可。
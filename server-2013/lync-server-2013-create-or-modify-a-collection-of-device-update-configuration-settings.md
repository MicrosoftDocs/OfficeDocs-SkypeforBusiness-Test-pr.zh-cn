---
title: 创建或修改设备更新配置设置集合
TOCTitle: 创建或修改设备更新配置设置集合
ms:assetid: 3e8ce95f-a8c8-417c-b1f7-0f759a567aff
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/JJ994029(v=OCS.15)
ms:contentKeyID: 52061003
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 创建或修改设备更新配置设置集合

 

_**上一次修改主题：** 2016-12-08_

可以使用 Windows PowerShell 和 **New-CsDeviceUpdateConfiguration** cmdlet 创建（仅在站点作用域）设备更新配置设置以及使用 **Set-CsDeviceUpdateConfiguration** cmdlet 对其进行修改。可从 Lync Server 2013 命令行管理程序或从 Windows PowerShell 的远程会话中运行这些 cmdlet。

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>有关使用远程 Windows PowerShell 连接到 Lync Server 的详细信息，请参阅 Lync Server Windows PowerShell 博客文章“快速入门：使用远程 PowerShell 管理 Microsoft Lync Server 2010”，网址为 <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</a>。</td>
</tr>
</tbody>
</table>



## 创建使用默认值的设备更新配置设置

  - 以下命令为 Redmond 站点创建一组新的设备更新配置设置：
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond"
    
    由于上述命令中未指定参数（不包括必需的 Identity 参数），因此新的配置设置集合的所有属性都将使用默认值。

## 在创建设备更新配置设置时更改单个属性值

  - 若要创建使用不同属性值的设置，只需包含相应的参数和参数值。例如，若要创建默认情况下每 21 天删除旧日志文件的设备更新配置设置集合，请使用类似如下的命令：
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupInterval "21.00:00:00"

## 在创建设备更新配置设置时更改多个属性值

  - 通过包括多个参数可修改多个属性值。例如，以下命令可将日志清除间隔设置为 21 天以及将日志刷新间隔设置为 30 分钟：
    
        New-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupInterval "21.00:00:00" -LogFlushInterval "00:30:00"

有关修改现有设备配置设置的详细信息，请参阅 [Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md) cmdlet 的帮助主题。有关创建配置设置集合的详细信息，请参阅 [New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md) cmdlet 的帮助主题。


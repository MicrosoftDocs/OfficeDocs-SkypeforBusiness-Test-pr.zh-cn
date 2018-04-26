---
title: Lync Server 2013：将 Kerberos 身份验证从站点中删除
TOCTitle: 将 Kerberos 身份验证从站点中删除
ms:assetid: 93171b02-bb36-42dc-943d-86d9dde45b59
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg398749(v=OCS.15)
ms:contentKeyID: 49313607
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 在 Lync Server 2013 中将 Kerberos 身份验证从站点中删除

 

_**上一次修改主题：** 2012-01-16_

要成功完成此过程，应以 RTCUniversalServerAdmins 组成员的身份登录。

如果需要从站点删除 Kerberos 身份验证或终止站点，则必须通过使用 **Remove-CsKerberosAccountAssignment** cmdlet 从站点删除 Kerberos 身份验证帐户分配。使用以下过程删除 Kerberos 身份验证帐户分配，此操作会从站点中的所有计算机删除分配。

<table>
<thead>
<tr class="header">
<th><img src="images/JJ656815.warning(OCS.15).gif" title="warning" alt="warning" />警告：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>如果永久终止已启用 Kerberos 的帐户，则删除分配之后，应使用 Active Directory 用户和计算机将其从 Active Directory 域服务 中删除。如果计划将来使用对象，您可能希望保留 Active Directory 对象。</td>
</tr>
</tbody>
</table>


## 从站点删除 Kerberos 身份验证

1.  以 RtcUniversalServerAdmins 组成员的身份，登录到域中运行 Lync Server 2013 的计算机，或登录到安装了管理工具的计算机。

2.  启动 Lync Server 命令行管理程序：依次单击“开始”、“所有程序”和“Microsoft Lync Server 2013”，然后单击“Lync Server 命令行管理程序”。

3.  通过命令行运行以下两个命令：
    
        Remove-CsKerberosAccountAssignment -Identity "site:SiteName"
    
        Enable-CsTopology
    
    例如：
    
        Remove-CsKerberosAccountAssignment -Identity "site:Redmond"
    
        Enable-CsTopology
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>对 Kerberos 身份验证进行更改（例如，添加帐户或删除帐户）之后，必须通过 Lync Server 命令行管理程序命令提示符运行 <strong>Enable-CsTopology</strong>。</td>
    </tr>
    </tbody>
    </table>


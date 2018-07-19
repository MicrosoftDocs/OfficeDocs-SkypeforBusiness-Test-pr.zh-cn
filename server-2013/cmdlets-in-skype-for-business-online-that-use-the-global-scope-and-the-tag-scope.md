---
title: 使用全局作用域和标记作用域的 Cmdlet
TOCTitle: 使用全局作用域和标记作用域的 Cmdlet
ms:assetid: 1e2bc055-8a72-425e-967b-e253add7018c
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Dn362774(v=OCS.15)
ms:contentKeyID: 56271125
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 使用全局作用域和标记作用域的 Cmdlet

 

_**上一次修改主题：** 2015-06-22_

在 Skype for Business Online 中，可以在*全局作用域*或*标记作用域*（或*每用户作用域*）处配置策略。当使用 **Get-Cs** cmdlet 时，您不必指定作用域或标识。如果您不带任何参数调用其中一个 cmdlet，则将返回所有相关项目。例如，此命令可返回有关您的所有外部访问策略的信息：

    Get-CsExternalAccessPolicy

如果您想要限制返回的数据，则需要仅包括 Identity 参数或 Filter 参数。例如，要仅返回全局策略，请使用此命令：

    Get-CsExternalAccessPolicy -Identity "global"

要返回具有标识“RedmondAccessPolicy”的每用户策略，请使用此命令：

    Get-CsExternalAccessPolicy -Identity "RedmondAccessPolicy"

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>当引用每用户策略时，标记 <strong>prefix</strong> 是可选的。此语法（包括 prefix）也有效：<br />
Get-CsExternalAccessPolicy –Identity &quot;tag:RedmondAccessPolicy&quot;</td>
</tr>
</tbody>
</table>


要返回除全局策略之外的所有策略（即，所有每用户策略），请使用此命令：

    Get-CsExternalAccessPolicy -Filter "tag:*"

以下 cmdlet 针对全局作用域和每用户（标记）作用域进行操作：

  - [Get-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClientPolicy)

  - [Get-CsConferencingPolicy](get-csconferencingpolicy.md)

  - [Get-CsDialPlan](get-csdialplan.md)

  - [Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)

  - [Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)

  - [Get-CsPresencePolicy](get-cspresencepolicy.md)

  - [Get-CsVoicePolicy](get-csvoicepolicy.md)

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>不管名称如何，拨号计划从功能来讲都是策略。例如，将使用术语<em>拨号计划</em>，而不使用拨号策略，以便保留以前的 Lync Server 版本使用的术语。</td>
</tr>
</tbody>
</table>


## 另请参阅

#### 概念

[标识、作用域和租户](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)


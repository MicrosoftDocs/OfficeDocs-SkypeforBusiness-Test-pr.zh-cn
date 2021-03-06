﻿---
title: Lync Server 2013 中的电话拨入式会议概述
TOCTitle: Lync Server 2013 中的电话拨入式会议概述
ms:assetid: 6e581cef-960a-4730-8b22-91b2129d34e3
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg398524(v=OCS.15)
ms:contentKeyID: 49313190
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 中的电话拨入式会议概述

 

_**上一次修改主题：** 2012-09-30_

如果组织中的某些用户在其外出或无法访问计算机时需要参加 Lync Server 2013 本地会议，则可部署电话拨入式会议，以使他们可以使用公用电话交换网 (PSTN) 电话来参加会议。

部署 Lync Server 2013 会议时，电话拨入式会议是一个可配置的可选功能。虽然电话拨入式会议使用的某些 Lync Server 2013 组件与企业语音使用的组件相同，但是即使未部署企业语音，也可以部署电话拨入式会议。

> [!NOTE]  
> 如果部署电话拨入式会议，那么必须在每个部署 Lync Server 2013 会议的池中部署电话拨入式会议。无需在每个池中分配访问号码，但必须在每个池中部署拨入功能。当用户呼叫一个池中的访问号码以加入另一个池中的 Lync Server 2013 会议时，此要求支持记录名称功能。



在会议策略中，会议必须支持拨入访问。默认情况下，允许拨入访问的会议会在会议邀请中包括以下信息：

  - 用于标识会议的数字会议 ID。

  - 一个或多个 PSTN 接入号码。

  - 指向电话拨入式会议设置页的链接，其中包含具有其关联语言的接入号码完整列表，创建、重置或解锁个人标识号 (PIN) 的位置，以及其他信息（例如，双音多频 (DTMF) 控制）。

电话拨入式会议支持企业用户和匿名用户。企业用户在其组织内拥有 Active Directory 域服务 凭据和 Lync Server 2013 帐户。匿名用户在组织内不具有企业凭据。在电话拨入式会议环境中，联盟伙伴组织中使用 PSTN 连接至会议的用户被视为匿名用户。对于电话拨入式会议（不同于其他环境），联盟用户都未经过身份验证。

参加允许拨入访问会议的企业用户或会议主持人拨打一个会议访问号码后，系统会提示他们输入会议 ID。如果主持人尚未参加会议，则用户可以输入其统一通信 (UC) 分机号（或完整电话号码）和 PIN，或者等待主持人准许其参加会议。通过只输入其 PIN，会议组织者就可以以主持人身份参加会议。前端服务器使用完整电话号码或分机号与 PIN 的组合唯一地将企业用户映射到其 Active Directory 凭据。因此，在会议中是按名称对企业用户进行身份验证和标识的。企业用户还可以担任由组织者预定义的会议角色。

> [!NOTE]  
> 从办公 IP 电话或从 Lync Server 2013 或 Lync 2010 Attendant 拨入的企业用户不会得到输入其电话号码的提示，这是因为他们已经过身份验证。



要参加电话拨入式会议的匿名用户拨打一个会议接入号码后，系统会提示他们输入会议 ID。还会提示未经身份验证的匿名用户记录其名称。记录的名称用于在会议中标识未经身份验证的用户。除非至少一个主持人或经过身份验证的用户已参加会议，否则不允许匿名用户参加会议，且无法向其分配预定义角色。

> [!NOTE]  
> 选择不输入其电话号码和 PIN 的企业用户未经过身份验证。系统会提示他们记录其名称，并在会议中将他们视为匿名用户。



到预定时间时，会议组织者可选择通过关闭或锁定会议来限制对会议的访问。在这种情况下，系统会请求电话拨入用户进行身份验证。如果电话拨入用户身份验证失败或选择不进行身份验证，他们会被转移到会议厅中等待，直到主持人接受或拒绝他们，或者连接超时并断开连接。他们在会议厅中等待获准加入会议时，电话拨入用户将听到音乐。一旦被允许加入会议，电话拨入用户就可以参与会议的音频部分，并可使用电话键盘执行双音多频 (DTMF) 命令。电话拨入主持人可以使用 DTMF 命令打开或关闭参与者的取消静音功能、锁定或解锁会议、允许会议厅中的人加入会议、打开或关闭进入和退出通知。主持人还可以使用 DTMF 命令允许会议厅中的每个人加入会议，从而更改会议的权限以允许随后的任何人加入会议。所有电话拨入参与者都可以使用 DTMF 命令收听帮助，收听会议名单，以及使自己静音。

电话拨入参与者（即，无论他们是否从 PSTN 拨号）在会议期间收听个人通知，例如，是否已将其静音或取消静音，是否记录会议，或者是否有人在会议厅中等待。

> [!NOTE]  
> 通过单击链接（而不是电话拨入）参加会议的与会者不会听到个人通知。



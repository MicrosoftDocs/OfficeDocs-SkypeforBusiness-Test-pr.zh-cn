﻿---
title: Lync Server 2013：在拓扑中定义可选控制器拓扑
TOCTitle: 在拓扑中定义可选控制器拓扑
ms:assetid: 8e9a659d-23b0-401d-b296-59c7df414d49
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg398717(v=OCS.15)
ms:contentKeyID: 49313557
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 针对 Lync Server 2013 在拓扑中定义可选控制器拓扑

 

_**上一次修改主题：** 2012-09-08_

Lync Server 2013 控制器可以是单实例服务器，也可以安装为多个控制器的负载平衡池，以获得更高的可用性和容量。同时支持硬件负载平衡和域名系统 (DNS) 负载平衡。本主题介绍如何为控制器池配置 DNS 负载平衡。

要在添加或删除服务器角色后成功发布、启用或禁用拓扑，您应该以 **RTCUniversalServerAdmins** 和 **Domain Admins** 组成员的用户身份登录。还可以委派适当的管理员权限，以添加服务器角色。有关详细信息，请参阅 Standard Edition 服务器或 Enterprise Edition 服务器部署文档中的[Lync Server 2013 中的委派安装权限](lync-server-2013-delegate-setup-permissions.md)。对于其他配置更改，只需要“RTCUniversalServerAdmins”组的成员身份。

本主题介绍用于定义和发布两个 控制器拓扑的拓扑的步骤：

  - 定义控制器（单实例）

  - 定义控制器（多控制器池）

## 定义控制器（单实例）

1.  启动拓扑生成器：依次单击“开始”、“所有程序”和“Microsoft Lync Server 2013”，然后单击“Lync Server 拓扑生成器”。

2.  在欢迎页上，单击“从现有部署下载拓扑”。

3.  在“将拓扑另存为”对话框中，键入现有拓扑的本地副本的名称和位置，然后单击“保存”。

4.  展开计划向其中添加控制器的站点，右键单击“控制器池”，然后单击“新建控制器池”。

5.  在“定义控制器池 FQDN”对话框中，执行以下操作：
    
      - 在“池 FQDN”中，键入控制器池的 FQDN。
    
      - 单击“单计算机池”，然后单击“下一步”。

6.  在“定义文件共享”对话框中，执行下列操作之一：
    
    1.  要使用现有的文件共享，请单击“使用先前定义的文件共享”，从列表中选择一个文件共享，然后单击“下一步”。
    
    2.  要创建新的文件共享，请单击“定义新的文件共享”，在“文件服务器 FQDN”中键入文件共享位置的 FQDN，在“文件共享”中键入共享的名称，然后单击“下一步”。
    
    > [!IMPORTANT]  
    > 在发布拓扑前，此步骤中指定或创建的文件共享必须已存在或已创建。<br />
    > 实际上未使用分配给控制器的文件共享，因此可以分配组织中任何池的文件共享。


7.  在“指定 Web 服务 URL”对话框的“外部基 URL”中，指定控制器的 FQDN，然后单击“完成”。
    
    > [!IMPORTANT]
    > 该名称必须可以从 Internet DNS 服务器进行解析并指向反向代理的公用 IP 地址，以侦听对该 URL 的 HTTP/HTTPS 请求，并将其代理到该控制器上的外部 Web 服务虚拟目录中。
    
    > [!WARNING]
    > 如果有多个 前端池或 前端服务器，则外部 Web 服务 FQDN 必须是唯一的。例如，如果将 前端服务器的外部 Web 服务 FQDN 定义为 <strong>pool01.contoso.com</strong>，则不能将 <strong>pool01.contoso.com</strong> 用于另一个 前端池或 前端服务器。如果您还部署 控制器，则为任何 控制器或 控制器池定义的外部 Web 服务 FQDN 必须与任何其他 控制器或 控制器池以及任何 前端池或 前端服务器的不同。如果决定使用自定义的 FQDN 覆盖内部 Web 服务，则每个 FQDN 都必须不同于任何其他 前端池、 控制器或 控制器池。


8.  发布拓扑。

## 定义控制器（多控制器池）

1.  启动拓扑生成器：依次单击“开始”、“所有程序”和“Microsoft Lync Server 2013”，然后单击“Lync Server 拓扑生成器”。

2.  在欢迎页上，单击“从现有部署下载拓扑”。

3.  在“将拓扑另存为”对话框中，键入现有拓扑的本地副本的名称和位置，然后单击“保存”。

4.  展开计划向其中添加控制器的站点，右键单击“控制器池”，然后单击“新建控制器池”。

5.  在“定义控制器池 FQDN”对话框中，执行以下操作：
    
      - 在“池 FQDN”中，键入控制器池的 FQDN。
    
      - 单击“多计算机池”，然后单击“下一步”。

6.  在“定义此池中的计算机”对话框中，执行以下操作：
    
      - 指定第一个池成员的计算机 FQDN，然后单击“添加”。
    
      - 为想要添加的每台计算机重复以上步骤。完成后，单击“下一步”。

7.  在“定义文件共享”对话框中，执行下列操作之一：
    
      - 要使用现有的文件共享，请单击“使用先前定义的文件共享”，从列表中选择一个文件共享，然后单击“下一步”。
    
      - 要创建新的文件共享，请单击“定义新的文件共享”，在“文件服务器 FQDN”中键入文件共享位置的 FQDN，在“文件共享”中键入共享的名称，然后单击“下一步”。
    
    > [!IMPORTANT]  
    > 在发布拓扑前，此步骤中指定或创建的文件共享必须已存在或已创建。<br />
    > 实际上未使用分配给控制器的文件共享，因此可以分配组织中任何池的文件共享。


8.  在“指定 Web 服务 URL”对话框的“外部基 URL”中，指定控制器的 FQDN，然后单击“完成”。
    
    > [!IMPORTANT]
    > 该名称必须可从 Internet DNS 服务器解析，并指向反向代理的公用 IP 地址，该代理侦听发送到该 URL 的 HTTP/HTTPS 请求，并将其代理到该控制器池上的外部 Web 服务虚拟目录。
    
    > [!WARNING]
    > 如果有多个 前端池或 前端服务器，则外部 Web 服务 FQDN 必须是唯一的。例如，如果将 前端服务器的外部 Web 服务 FQDN 定义为 <strong>pool01.contoso.com</strong>，则不能将 <strong>pool01.contoso.com</strong> 用于另一个 前端池或 前端服务器。如果您还部署 控制器，则为任何 控制器或 控制器池定义的外部 Web 服务 FQDN 必须与任何其他 控制器或 控制器池以及任何 前端池或 前端服务器的不同。如果决定使用自定义的 FQDN 覆盖内部 Web 服务，则每个 FQDN 都必须不同于任何其他 前端池、 控制器或 控制器池。


9.  发布拓扑。


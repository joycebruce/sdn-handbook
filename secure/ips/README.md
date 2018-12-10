# IPS (Intrusion Prevention System)

随着攻击手段和工具的不断涌现、攻击技术的日趋成熟，传统的防火墙网络层攻击检测已无法满足安全需要。在此背景下，出现了入侵防御(`IPS`)技术。

## 背景


网络入侵方式越来越多，有的充分利用防火墙放行许可，有的则使杀毒软件失效。比如，在病毒刚进入网络的时候，还没有一个厂家迅速开发出相应的辨认和扑灭程序，于是这种全新的病毒就很快大肆扩散、肆虐于网络、危害单机或网络资源，这就是所谓`Zero Day Attack`。

防火墙可以根据英特网地址（`IP-Addresses`）或服务端口（`Ports`）过滤数据包。但是，它对于利用合法网址和端口而从事的破坏活动则无能为力。因为，防火墙极少深入数据包检查内容。

每种攻击代码都具有只属于它自己的特征（`signature`），病毒之间通过各自不同的特征互相区别，同时也与正常的应用程序代码相区别。杀毒软件就是通过存储所有已知的病毒特征来辨认病毒的。

在`ISO/OSI`网络层次模型（见`OSI`模型）中，防火墙主要在第二到第四层起作用，它的作用在第四到第七层一般很微弱。而杀毒软件主要在第五到第七层起作用。为了弥补防火墙和杀毒软件二者在第四到第五层之间留下的空档，几年前，工业界已经有入侵检测系统投入使用。

入侵侦查系统（`IDS`）在发现异常情况后及时向网络安全管理人员或防火墙系统发出警报。可惜这时灾害往往已经形成。虽然，亡羊补牢，尤未为晚，但是，防卫机制最好应该是在危害形成之前先期起作用。

随后应运而生的入侵反应系统（`IRS: Intrusion Response Systems`）作为对入侵侦查系统的补充能够在发现入侵时，迅速作出反应，并自动采取阻止措施。

而入侵防御系统(`IPS`)则作为二者的进一步发展，汲取了二者的长处。

## 简介

入侵防御的设备通过监控或者分析系统事件检测入侵，并通过一定的响应方式实时地中止入侵行为。

入侵防御系统也像入侵侦查系统一样，专门深入网络数据内部，查找它所认识的攻击代码特征，过滤有害数据流，丢弃有害数据包，并进行记载，以便事后分析。

除此之外，更重要的是，大多数入侵防御系统同时结合考虑应用程序或网络传输层的异常情况，来辅助识别入侵和攻击。

> 比如，用户或用户程序违反安全条例、数据包在不应该出现的时段出现、操作系统或应用程序弱点的空子正在被利用等等现象。

入侵防御系统虽然也考虑已知病毒特征，但是它并不仅仅依赖于已知病毒特征。

应用入侵防御系统的**目的**在于及时识别攻击程序或有害代码及其克隆和变种，采取预防措施，先期阻止入侵，防患于未然。或者至少使其危害性充分降低。

入侵预防系统一般作为防火墙 和防病毒软件的补充来投入使用。在必要时，它还可以为追究攻击者的刑事责任而提供法律上有效的证据（`forensic`）。

### 入侵防御技术介绍

- 异常侦查。正如入侵侦查系统，入侵防御系统知道正常数据以及数据之间关系的通常的样子，可以对照识别异常。
- 在遇到动态代码（`ActiveX`，`JavaApplet`，各种指令语言`script languages`等等）时，先把它们放在沙盘内，观察其行为动向，如果发现有可疑情况，则停止传输，禁止执行。
- 有些入侵预防系统结合协议异常、传输异常和特征侦查，对通过网关或防火墙进入网络内部的有害代码实行有效阻止。
- 内核基础上的防护机制。用户程序通过系统指令享用资源（如存储区、输入输出设备、中央处理器等）。入侵预防系统可以截获有害的系统请求。
- 对`Library`、`Registry`、重要文件和重要的文件夹进行防守和保护。

## 入侵预防系统类型

投入使用的入侵预防系统按其用途进一步可以划分为主机入侵预防系统（`HIPS`: `Hostbased Intrusion Prevension System`）和网络入侵预防系统（`NIPS`: `Network Intrusion Prevension System`）两种类型。

网络入侵预防系统作为网络之间或网络组成部分之间的独立的硬件设备，切断交通，对过往包裹进行深层检查，然后确定是否放行。

网络入侵预防系统借助病毒特征和协议异常，阻止有害代码传播。有一些网络入侵预防系统还能够跟踪和标记对可疑代码的回答，然后，看谁使用这些回答信息而请求连接，这样就能更好地确认发生了入侵事件。

根据有害代码通常潜伏于正常程序代码中间、伺机运行的特点，单机入侵预防系统监视正常程序，比如`Internet Explorer`、`Outlook`，等等，在它们（确切地说，其实是它们所夹带的有害代码）向操作系统发出请求指令，改写系统文件，创建对外连接时，进行有效阻止，从而保护网络中重要的单个机器设备，如服务器、路由器、防火墙等等。这时，它不需要求助于已知病毒特征和事先设定的安全规则。总地来说，单机入侵预防系统能使大部分钻空子行为无法得逞。我们知道，入侵是指有害代码首先到达目的地，然后干坏事。然而，即使它侥幸突破防火墙等各种防线，得以到达目的地，但是由于有了入侵预防系统，有害代码最终还是无法起到它要起的作用，不能达到它要达到的目的。

## 参考

- [IPS简介 - Huawei](http://support.huawei.com/hedex/pages/EDOC10000074993118G29K/06/EDOC10000074993118G29K/06/resources/cfg_utm/sec_vsp_cfg_utm_0026.html)
- [配置入侵防御（IPS）- Huawei](http://support.huawei.com/hedex/pages/EDOC1000054702SZD0528J/13/EDOC1000054702SZD0528J/13/resources/cfg_utm/sec_vsp_cfg_utm_0025.html)
- [入侵防御 - Huawei](http://support.huawei.com/hedex/pages/EDOC1000054702SZD0528J/13/EDOC1000054702SZD0528J/13/resources/online_help_cn/sec_vsp_help_utm_0005.html)

- [IPS 事件过滤器策略 - IBM](https://www.ibm.com/support/knowledgecenter/zh/SSHLHV_5.4.0/com.ibm.alps.doc/concepts/alps_ips_event_filter_policy_container.htm)

- [配置隔离响应对象 - IBM](https://www.ibm.com/support/knowledgecenter/zh/SSHLHV_5.4.0/com.ibm.alps.doc/tasks/alps_configuring_quarantine_response_objects.htm)

- [入侵预防系统 - wikipedia.org](https://zh.wikipedia.org/wiki/%E5%85%A5%E4%BE%B5%E9%A2%84%E9%98%B2%E7%B3%BB%E7%BB%9F)
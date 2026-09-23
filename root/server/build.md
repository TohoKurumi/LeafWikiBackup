---
tags: []
leafwiki_id: Td860fsDg
leafwiki_title: 搭建
leafwiki_created_at: "2026-08-08T22:43:33.839127Z"
leafwiki_updated_at: "2026-09-23T17:48:34.0319529Z"
leafwiki_creator_id: czdX0csDR
leafwiki_last_author_id: czdX0csDR
---
# 搭建
>若你也有意愿开服，本页可作参考

## 硬件
不管是对于阿里云或者是腾讯云的 4H4G3Mbps 轻量应用云，亦或是配置未知的网易租赁服来说，目前的硬件是得到了极大的提升的。基岩版服务端随着更新所要求的硬件配置也是越来越高了，争取早日超过Java版（？ （或许已然超越

- 目前配置（2026/7/14）
  - 金牌电源 650w × 1
  - E5-2673V3 2011针 × 1
  - DDR3 REGECC 1600MHz 4GB × 4
  - SATA 固态 256G × 1
  - GT620 2GB ×
  - 21年装电脑闲置的旧机箱 × 1
  - 一个桥接家里主路由器的边缘路由器 × 1


## 软件
**操作系统：** 
- 当前使用的系统是 Windows Server 2019 Datacenter (1809) x86_64，而且是 Server Core 版本，意味着它砍掉了桌面环境那一大堆组件，仅能使用命令行窗口进行操作，比起之前在轻量应用云上使用的 Windows Server 2019 来说节省了大量的资源以用于运行基岩版服务端。你说为啥不用 Linux ？往下看！

**服务端&加载器：** 
- 自2024年4月转档后我们选用了 [BDS](<https://bluemirror.dmblock.top/#/bedrock>) 服务端，[Levilamina](<https://github.com/LiteLDev/LeviLamina>) 加载器。BDS 是微软官方推出的服务端，是支持原版特性最完整的服务端，最适合生存服务器。其他服务端如 [PocketMine](<https://github.com/pmmp/PocketMine-MP>) 或 [Nukkit](<https://github.com/CloudburstMC/Nukkit>) 都对原版特性支持不足，只适合开小游戏服务器或老版本服务器之类的。目前有两个主流的基于BDS的非官方模组/插件加载器（Levilamina 和 [Endstone](<https://github.com/EndstoneMC/endstone>)）。
- LeviLamina 是一个非官方的模组加载器，旨在为基岩版提供必不可少的 API 支持，是一个轻量级、模块化和多功能的基岩版模组加载器，[LiteLoaderBDS](<https://github.com/LiteLDev/LiteLoaderBDS>) 的后继者。但是此项目核心部分高度依赖Windows！它是在微软移除 pdb 后的唯二幸存者（另一个是 Endstone ，但当时它太冷门没发现它），实在别无选择，虽然还有部署 docker 这个办法，但因为各种考虑放弃了。

  <img src="/assets/Td860fsDg/image.png" width="356" title="Windows Server Core 2019">


## 网络
由于 IPv4 公网地址难以申请，本服只能暂时使用租用云服务器用 FRP 内网穿透对公网开放。

- 云服务器与域名租用
  - 腾讯云轻量应用服务器（2H4G5Mbps Debian 13.2）到期时间：2027-08-25 16:33:54
  - 天霆网络香港特惠云主机Ⅰ型（2H1G10Mbps CentOS 7.6）到期时间：2027-09-07 11:39:22
  - 分别从不同渠道租了两个域名分别解析以上两台云主机，详见[[到期]]

若只是单单映射一个基岩版（BDS）服务到公网并不需要配置这么好和如此多的云服务器，1H1G 就能胜任工作，重点在于带宽，基岩版（BDS）的数据包很小，带宽要求相对友好，但建议最好在 5Mbps 及以上。本服由于需要对外开放的服务多，WebRTC 语音聊天、维基站点以及异地维护远程连接等，有些服务要求低延迟，有些服务在大陆则需要备案，我们还部署了服群互通甚至大群和小群和服务器的互通，一个或多个服务器便可以满足我们相对复杂的需求。
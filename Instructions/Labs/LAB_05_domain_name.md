---
lab:
  title: 练习 05：创建 DNS 区域并配置 DNS 设置
  module: Guided Project - Configure secure access to workloads with Azure virtual networking services
---

# 练习 05：创建 DNS 区域并配置 DNS 设置

## 场景

组织要求工作负荷使用域名而不是 IP 地址进行内部通信。  该组织不想添加自定义 DNS 解决方案。 确定这些要求。
+ contoso.com 需要**专用 DNS 区域**。
+ DNS 将使用到 app-vnet 的**虚拟网络链接**。 
+ 后端子网需要新的 **DNS 记录**。 

## 技能任务

+ 创建和配置专用 DNS 区域。
+ 创建和配置 DNS 记录。
+ 在虚拟网络上配置 DNS 设置。
  
## 体系结构关系图

![Azure DNS 链接到虚拟网络的示意图。](../Media/task-5.png)



## 练习说明

**备注：** 本练习需要安装实验室 01 虚拟网络和子网。 如果需要部署这些资源，则提供[模板](https://github.com/MicrosoftLearning/Configure-secure-access-to-workloads-with-Azure-virtual-networking-services/blob/main/Allfiles/Labs/All-Labs/create-vnet-subnets-template.json)。

### 创建专用 DNS 区域

[Azure 专用 DNS](https://learn.microsoft.com/azure/dns/private-dns-overview) 提供可靠、安全的 DNS 服务来管理和解析虚拟网络中的域名，无需添加自定义 DNS 解决方案。 通过使用专用 DNS 区域，可使用自己的自定义域名，而不使用 Azure 提供的名称。

1. 在 Azure 门户中，搜索并选择 `Private dns zones`。

1. 选择“**+ 创建**”和配置 DNS 区域。 

    | 属性       | 值                        |
    | :------------- | :--------------------------- |
    | 订阅   | 选择订阅 |
    | 资源组 | RG1****                      |
    | 名称           | `private.contoso.com`              |
    | 区域         | **美国东部**                  |

1. 选择“**查看 + 创建**”，然后选择“**创建**”。

1. 等待 DNS 区域部署，然后选择“**转到资源**”。 

### 创建你的专用 DNS 区域的虚拟网络链接

要解析专用 DNS 区域中的 DNS 记录，必须将资源链接到专用区域。 [虚拟网络链接](https://learn.microsoft.com/azure/dns/private-dns-virtual-network-links)将虚拟网络关联到专用区域。

1. 在门户中，继续处理 **private.contoso.com** DNS 区域。 

1. 在“**DNS 管理**”边栏选项卡中，选择“**虚拟网络链接**”。

1. 选择“**+ 添加**”并配置虚拟网络链接。 

    | 属性                 | Value             |
    | :----------------------- | :---------------- |
    | 链接名称                | `app-vnet-link` |
    | 虚拟网络          | app-vnet****      |
    | 启用自动注册 | **已启用**       |

1. 选择“**创建**”并等待部署完成。 如果需要，请**刷新**页面。 

### 创建 DNS 记录集

[DNS 记录](https://learn.microsoft.com/en-us/azure/dns/dns-zones-records#dns-records)提供有关 DNS 区域的信息。 

1. 在门户中，继续处理 **private.contoso.com** DNS 区域。 

1. 在“**DNS 管理**”边栏选项卡中，选择“**+ 记录集**”。

1. 请注意，为每个虚拟机自动创建两条 A 记录。 

1. 选择“**+ 添加**”并配置记录集。 完成后，选择“**添加**”。 
   
    | 属性   | 值        |
    | :--------- | :----------- |
    | 名称       | `backend`    |
    | 类型       | **A**        |
    | TTL        | **1**        |
    | IP 地址 | **10.1.1.5** |

**备注：** 此记录集意味着 app-vnet 中有一个虚拟机，其专用 IP 地址为 10.1.1.5。

### 通过在线培训了解更多信息

+ [Azure DNS 简介](https://learn.microsoft.com/training/modules/intro-to-azure-dns/)。 本模块说明 Azure DNS 的功能、工作原理以及何时应选择使用 Azure DNS 作为解决方案来满足组织的需求。
+ [在 Azure DNS 上托管域](https://learn.microsoft.com/training/modules/host-domain-azure-dns/)。 在本模块中，你将了解如何创建 DNS 区域和 DNS 记录。

### 关键结论

祝贺你完成本练习。 以下是要点：

+ Azure DNS 是一种云服务，可用于承载和管理域名系统 (DNS) 域，也称为 DNS 区域。 
+ Azure DNS 公用区域托管将由 Internet 上的任何主机来解析的记录的域名区域数据。
+ 借助 Azure 专用 DNS 区域，你可以为专用 Azure 资源配置专用 DNS 区域命名空间。
+ DNS 区域是 DNS 记录的集合。 DNS 记录提供关于域的信息。

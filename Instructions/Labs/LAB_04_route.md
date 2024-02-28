---
lab:
  title: 练习：将流量路由到防火墙
  module: Guided Project - Configure secure access to workloads with Azure virtual networking services
---

# 实验室：将流量路由到防火墙


## 方案

现在，防火墙已具备强制实施组织安全要求的策略，因此需要将网络流量路由到防火墙子网，以便筛选和检查流量。 路由表提供对传入和传出 Web 应用程序的网络流量的路由的控制。 将网络流量路由到用作子网默认网关的防火墙时，网络流量受到防火墙规则的控制。 

### 体系结构关系图


![显示包含防火墙和路由表的一个虚拟网络的示意图。](../Media/task-3.png)

### 技能任务

- 创建和配置路由表。
- 将路由表链接到子网。
  

## 练习说明

### 创建路由表

1. 记录 app-vnet-firewall**** 的专用和公共 IP 地址。

    1. 在门户顶部的搜索框中，输入“防火墙”。 在搜索结果中选择“防火墙”。

    1. 选择“app-vnet-firewall”。****

    1. 选择“概述”。

        1. 记录专用 IP 地址****。

    1. 在“概述”窗格中选择“fwpip”。****

    1. 记录公共 IP 地址****。 


1. 在搜索框中输入“路由表”****。 当“路由表”出现在搜索结果中时，请选择它。

1. 在“路由表”页中，选择“+ 创建”****。

1. 在“创建路由表”的“基本信息”**** 选项卡中输入下表中列出的信息：

    | 属性 | 值    |
    |:---------|:---------|
    |订阅|选择订阅|
    |资源组|RG1****|
    |区域|**美国东部**|
    |名称|app-vnet-firewall-rt****|

    

1. 选择“查看 + 创建”，然后选择“创建”。

    [详细了解如何创建防火墙](https://docs.microsoft.com/azure/virtual-network/manage-route-table)和[将路由表关联到子网](https://docs.microsoft.com/azure/virtual-network/tutorial-create-route-table-portal#associate-a-route-table-to-a-subnet)。

### 将路由表关联到子网

1. 在搜索框中输入“路由表”****。 然后在搜索结果中选择“路由表”。

1. 选择“app-vnet-firewall-rt”****。

1. 选择“子网”。

1. 选择“+ 关联”。

1. 在“关联子网****”页中输入下表中列出的信息：

    | 属性 | 值    |
    |:---------|:---------|
    |虚拟网络|app-vnet**** (RG1)|
    |子网|前端|

1. 选择“确定”****。

1. 重复上述步骤，将 app-vnet-firewall-rt**** 路由表关联到 app-vnet 中的**** 后端**** 子网。

### 在路由表中创建路由

1. 在搜索框中输入“路由表”****。 然后在搜索结果中选择“路由表”。

1. 选择“app-vnet-firewall-rt”****。

1. 选择“路由”。

1. 选择 **+ 添加**。

1. 在“添加路由”页中输入下表中列出的信息：****

    | 属性 | Value    |
    |:---------|:---------|
    |路由名称|outbound-firewall****|
    |目标类型|**IP 地址**|
    |目标 IP 地址/CIDR 范围|**0.0.0.0/0**|
    |下一跃点类型|**虚拟设备**|
    |下一跃点地址|前面记录的防火墙的专用 IP 地址****|


1. 选择**添加**。

了解有关创建路由的更多信息[](https://docs.microsoft.com/azure/virtual-network/manage-route-table#add-a-route)。

现在，会将来自前端和后端子网的出站流量路由到防火墙。 



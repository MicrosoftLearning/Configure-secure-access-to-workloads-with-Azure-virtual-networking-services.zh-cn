---
lab:
  title: 练习 02：创建和配置网络安全组
  module: Guided Project - Configure secure access to workloads with Azure virtual networking services
---

# 练习 02：创建和配置网络安全组

## 场景

组织要求严格控制 app-vnet 中的网络流量。 你确定这些要求。
+ 前端子网具有可从 Internet 访问的 Web 服务器。 这些服务器需要**应用程序安全组** (ASG)。 ASG 应与属于组的任何虚拟机接口相关联。 这将使 Web 服务器易于管理。 
+ 后端子网具有前端 Web 服务器使用的数据库服务器。 需要**网络安全组** (NSG) 来控制此流量。 NSG 应与 Web 服务器访问的任何虚拟机接口相关联。 
+ 要进行测试，应在前端子网 (VM1) 和后端子网 (VM2) 中安装虚拟机。  IT 组提供了一个 Azure 资源管理器模板来部署这些 **Ubuntu 服务器**。 

## 技能任务

+ 创建网络安全组。
+ 创建网络安全组规则。
+ 将网络安全组与子网相关联。
+ 在网络安全组规则中创建和使用应用程序安全组。

## 体系结构关系图

![显示关联到虚拟网络的一个 ASG 和 NSG 的示意图。](../Media/task-2.png)




## 练习说明

### 为练习创建网络基础结构

**备注：** 本练习需要安装实验室 01 虚拟网络和子网。 如果需要部署这些资源，则提供[模板](https://github.com/MicrosoftLearning/Configure-secure-access-to-workloads-with-Azure-virtual-networking-services/blob/main/Allfiles/Labs/All-Labs/create-vnet-subnets-template.json)。

1. 使用右上角的图标启动 Cloud Shell 会话****。 或者，直接导航到 `https://shell.azure.com`。

1. 如果系统提示选择 Bash 或 PowerShell，请选择 PowerShell  。

1. 此任务不需要存储，请选择订阅。 **应用**所做的更改。 

1. 使用这些命令部署本练习所需的虚拟机。

>**备注**：如果部署因容量限制失败，请编辑模板并更改“位置”值。 

   ```powershell
   $RGName = "RG1"
   
   New-AzResourceGroupDeployment -ResourceGroupName $RGName -TemplateUri https://raw.githubusercontent.com/MicrosoftLearning/Configure-secure-access-to-workloads-with-Azure-virtual-networking-services/main/Instructions/Labs/azuredeploy.json
   ```
  
1. 在门户中，搜索并选择 `virtual machines`。 验证 vm1 和 vm2 是否**正在运行**。

### 创建应用程序安全组

[应用程序安全组 (ASG)](https://learn.microsoft.com/azure/virtual-network/application-security-groups) 允许将具有类似功能的服务器组合在一起。 例如，托管应用程序的所有 Web 服务器。 

1. 在门户中，搜索并选择 `Application security groups`。
   
1. 选择“**+ 创建**”并配置应用程序安全组。 

    | 属性       | 值                        |
    | :------------- | :--------------------------- |
    | 订阅   | 选择订阅 |
    | 资源组 | RG1****                      |
    | 名称           | `app-frontend-asg`          |
    | 区域         | **美国东部**                  |

1. 选择“**查看 + 创建**”，然后选择“**创建**”。

**备注**：您正在现有虚拟网络所在的同一区域中创建应用程序安全组。

**将应用程序安全组关联到 VM 的网络接口**

1. 在 Azure 门户中，搜索并选择`VM1`。

1. 在“**网络**”边栏选项卡中，选择“**应用程序安全组**”，然后选择“**添加应用程序安全组**”。

1. 选择 **app-frontend-asg**，然后选择“**添加**”。
   
### 创建并关联该网络安全组

[网络安全组 (NSG)](https://learn.microsoft.com/azure/virtual-network/network-security-groups-overview) 保护虚拟网络中的网络流量。 

1. 在门户中，搜索并选择 `Network security group`。

1. 选择“**+ 创建**”并配置网络安全组。 

    | 属性       | 值                        |
    | :------------- | :--------------------------- |
    | 订阅   | 选择订阅 |
    | 资源组 | RG1****                      |
    | 名称           | `app-vnet-nsg`            |
    | 区域         | **美国东部**                  |

1. 选择“**查看 + 创建**”，然后选择“**创建**”。

**将 NSG 与 app-vnet 后端子网相关联。**

NSG 可以与连接到 Azure 虚拟机 (VM) 的子网和/或单个网络接口关联。 

1. 选择“**转到资源**”或导航到 **app-vnet-nsg** 资源。

1. 在“**设置**”边栏选项卡中，选择“**子网**”。

1. 选择“+ 关联”****

1. 选择 **app-vnet (RG1)，** 然后选择“**后端**”子网。 选择“确定”****。

### 创建网络安全组规则

NSG 使用[安全规则](https://learn.microsoft.com/azure/virtual-network/network-security-group-how-it-works)筛选入站和出站网络流量。 

1. 在门户顶部的搜索框中，输入“**网络安全组**”。 在搜索结果中选择网络安全组。

1. 在网络安全组列表中选择“app-vnet-nsg”****。

1. 在“**设置**”边栏选项卡中，选择“**入站安全规则**”。

1. 选择“**+ 添加**”并配置入站安全规则。 

    | 属性                               | 值                          |
    | :------------------------------------- | :----------------------------- |
    | 源                                 | **任意**                        |
    | 源端口范围                     | **\***                         |
    | 目标                            | **应用程序安全组** |
    | 目标应用程序安全组 | **app-frontend-asg**            |
    | 服务                                | **SSH**                        |
    | 操作                                 | **允许**                      |
    | 优先级                               | **100**                        |
    | 名称                                   | **AllowSSH**                   |


### 通过在线培训了解更多信息

+ [使用 Azure 门户通过网络安全组筛选网络流量](https://learn.microsoft.com/training/modules/filter-network-traffic-network-security-group-using-azure-portal/)。 本模块将重点介绍如何在 Azure 门户中使用网络安全组 (NSG) 筛选网络流量。 了解如何创建、配置和应用 NSG 以提高网络安全性。
+ [使用网络安全组和服务终结点来保护和隔离对 Azure 资源的访问](https://learn.microsoft.com/training/modules/secure-and-isolate-with-nsg-and-service-endpoints/)。 在本模块中，你将了解网络安全组以及如何限制网络连接。 

### 关键结论

祝贺你完成本练习。 以下是要点：

+ 应用程序安全组可以根据组织的应用程序来组织虚拟机并定义网络安全策略。
+ 使用 Azure 网络安全组筛选 Azure 虚拟网络中 Azure 资源之间的网络流量。
+ 可将零个或一个网络安全组与虚拟机中的每个虚拟网络子网和网络接口相关联。 
+ 网络安全组包含安全规则，这些规则可允许或拒绝 Azure 资源的入站和出站网络流量。
+ 将虚拟机加入应用程序安全组。 然后，使用应用程序安全组作为网络安全组规则中的源或目标。




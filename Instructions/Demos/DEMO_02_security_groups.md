---
demo:
  title: 演示：创建和配置网络安全组
  module: Guided Project - Configure secure access to workloads with Azure virtual networking services
---
## 演示 - 创建和配置网络安全组


在此演示中，我们将探索安全组。 

**** 备注：**[](https://mslearn.cloudguides.com/en-us/guides/AZ-900%20Exam%20Guide%20-%20Azure%20Fundamentals%20Exercise%2013?azure-portal=true)** 可以使用虚拟网络的交互式实验室模拟，如果无法执行实时演示，则可以单击类似的实验室。 你可能会发现交互式模拟与建议的演示之间存在细微差异，但演示的核心概念和思想相同。 

限制访问 PaaS 资源 - 教程 - Azure 门户[](https://docs.microsoft.com/azure/virtual-network/tutorial-restrict-network-access-to-resources)

### 创建网络安全组

1. 访问 Azure 门户。

1. 搜索并选择“网络安全组” **** 。

1. [支持幻灯片] 创建一个 NSG，在创建过程中解释如何设置。 
 
1. 等待部署新 NSG。

**探索入站和出站规则**

1. 选择新 NSG。

1. [支持幻灯片] 讨论 NSG 如何与子网或网络接口相关联。

1. 讨论目标入站和出站规则。  

1. 查看默认的入站和出站规则。 

1. 创建新规则，说明设置。 专门讨论服务选择（如 HTTPS）和优先级设置。 
 

### 创建 ASG
 
1. [支持幻灯片] 搜索并选择“应用程序安全组”。 ****

1. 创建一个 ASG，并在创建过程中说明如何设置。 
 
1. 等待新 ASG 部署完成。

1. 讨论 ASG 如何与 NSG 规则关联。


### 关联 NSG 
1.  导航到已创建的 NSG
1.  在“设置”部分选择“子网”。
1.  在“子网”页中选择“+ 关联”
1.  在“关联子网”下选择你的“虚拟网络”。


>**** 备注：学生现在应该能够完成 LAB_02


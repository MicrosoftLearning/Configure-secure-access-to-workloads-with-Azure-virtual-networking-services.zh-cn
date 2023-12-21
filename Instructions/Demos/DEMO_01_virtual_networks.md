---
demo:
  title: 演示：创建和配置虚拟网络并对等互连
  module: Guided Project - Configure secure access to workloads with Azure virtual networking services
---
## 演示 - 创建和配置虚拟网络并对等互连


在本演示中，你将创建虚拟网络。

备注：**** 可使用建议设置值，也可根据需要使用自己的自定义值。

备注：**** 为你提供虚拟网络及虚拟网络对等互连****[](https://mslabs.cloudguides.com/guides/AZ-104%20Exam%20Guide%20-%20Microsoft%20Azure%20Administrator%20Exercise%209?azure-portal=true)的[](https://mslearn.cloudguides.com/en-us/guides/AZ-900%20Exam%20Guide%20-%20Azure%20Fundamentals%20Exercise%204?azure-portal=true)**** 交互式实验室模拟，如果无法执行实时演示，则可以单击类似的实验室。 你可能会发现交互式模拟与建议的演示之间存在细微差异，但演示的核心概念和思想相同。 


快速入门：创建虚拟网络 - Azure 门户[](https://docs.microsoft.com/azure/virtual-network/quick-create-portal)

### 在门户中创建虚拟网络


   
1.  [支持幻灯片] 在开始演示前，让我们复习一下什么是虚拟网络以及 Azure 虚拟网络的关键概念。 使用此幻灯片突出显示 Azure 虚拟网络的功能。 以及 Azure 虚拟网络概念和最佳做法。 演示如何创建虚拟网络时，可以解释地址空间、子网、区域和订阅的基本概念。 也可以直接进入演示，最后再讨论这些幻灯片。
   
2.  登录到 Azure 门户并搜索“虚拟网络” **** 。
   
3.  创建虚拟网络，说明基本设置。 确保至少创建了一个子网。 
   
4.  解释 Azure 门户提供了易于使用的界面。 标有红色星号 (*) 的项为必填项。
   
5.  [支持幻灯片] 选择“安全”选项卡。使用此幻灯片简要介绍安全服务，本课程稍后将详细介绍这些主题。 了解更多有关可部署到虚拟网络中服务的信息。 
   
6.  [支持幻灯片] 选择“IP 地址”选项卡。使用此幻灯片查看：规划虚拟网络和子网。 添加或修改子网，为学生演示如何配置子网。 
7.  单击“查看”确保没有验证错误。
8.  单击“创建”并等待部署虚拟网络。 指出通知消息。 
9.  演示如何转到资源。
10. 重复创建另一个虚拟网络的过程，以便演示 VNet 对等互连。

## 配置 VNet 对等互连

注意：在本演示中，你将需要两个虚拟网络。 

使用 VNet 对等互连连接虚拟网络 - 教程[](https://docs.microsoft.com/azure/virtual-network/tutorial-connect-virtual-networks-portal)

**配置第一个虚拟网络的 VNet 对等互连**

1. 在 Azure 门户中，选择第一个虚拟网络 **** 。 查看对等互连的值。 

1. 在“设置”下，选择“对等互连”和“+ 添加新对等互连” ****  **** 。

1. 配置对等互连第二个虚拟网络。 使用信息图标查看不同的设置。 

1. 对等互连完成后，查看对等互连状态。 

**确认第二个虚拟网络的 VNet 对等互连**

1. 在 Azure 门户中，选择第二个虚拟网络 ****

1. 在“设置”下，选择“对等互连” ****  **** 。

1. 可以看到，一个对等互连已自动创建。 请注意，“对等互连状态”为“已连接” ****   **** 。


>**** 备注：学生现在应该能够完成 LAB_01


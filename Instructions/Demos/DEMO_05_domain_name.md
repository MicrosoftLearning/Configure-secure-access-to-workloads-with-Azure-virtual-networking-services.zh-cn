---
demo:
  title: 演示：创建和配置 Azure DNS
  module: Guided Project - Configure secure access to workloads with Azure virtual networking services
---
## 演示 - 创建和配置 Azure DNS

在本演示中，你将探索 Azure DNS。

[教程：托管域和子域 - Azure DNS](https://docs.microsoft.com/azure/dns/dns-delegate-domain-azure-dns)


**创建专用 DNS 区域**

1. 访问 Azure 门户。

1. 搜索 DNS 区域服务 ****  。

1. 创建 DNS 区域并说明该区域的用途。 对于名称，可以使用 contoso.internal.com。

1.  请等待 DNS 区域创建完毕。 可能需要刷新页面。 ****  

**添加 DNS 记录集**


[教程：创建别名记录以引用区域资源记录](https://learn.microsoft.com/azure/dns/tutorial-alias-rr)

1. 创建区域后，选择“+记录集” **** 。

1. 使用“类型”下拉列表查看各种记录类型。 ****   查看如何使用不同的记录类型。 请注意当你选择不同记录类型时记录信息如何变化。

1. 创建 A 记录作为示例。 

**为自动注册链接 Vnet**

1.  部署 DNS 区域后，和学生一起回顾概述页。
1.  创建虚拟网络链接，将专用 DNS 区域链接到虚拟网络。
1.  在左窗格中，选择“虚拟网络链接”。
1.  选择 添加 。
1.  键入 myLink 作为链接名称。
1.  对于“虚拟网络”，请选择“myAzureVNet”。
1.  选中“启用自动注册”复选框。
1.  选择“确定”。

>**备注**：学生现在应该能够完成 LAB_05
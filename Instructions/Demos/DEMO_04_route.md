---
demo:
  title: 演示 - 创建并配置网络路由
  module: Guided Project - Configure secure access to workloads with Azure virtual networking services
---
## 演示 - 创建并配置网络路由

在本演示中，你将学习如何创建路由表、定义自定义路由以及将路由与子网相关联。 


注意：本演示需要一个具有至少一个子网的虚拟网络。 

路由网络流量 - 教程 - Azure 门户[](https://learn.microsoft.com/azure/virtual-network/tutorial-create-route-table-portal#create-a-route-table)


### 创建路由表 

1. 如果有时间，可查看教程图。 说明需要创建用户定义的路由的原因。 

1. 访问 Azure 门户。

1. 搜索并选择“路由表”。**** 讨论何时应使用传播网关路由。 

1. 创建路由表，说明任何不常见的设置。 

1. 等待要部署的新路由表。

**添加路由**

1.  选择新路由表，然后选择“路由” **** 。

1.  创建新的路由。 讨论可用的不同跃点类型。 

1.  创建新路由并等待资源部署完成。
 
### 将路由表与子网关联
一个路由表可与零个或多个子网相关联。 路由表不是与虚拟网络关联， 必须将路由表与每个要关联的子网相关联。


1.  前往希望与路由表相关联的子网。

1.  选择“路由表”，然后选择新的路由表**。 

1.  保存更改 。

 
>**** 备注：只能将路由表与路由表位于同一 Azure 位置和订阅的虚拟网络中的子网关联。

### 测试防火墙
现在，测试防火墙，确认路由和防火墙策略是否如预期工作。 

1.  将远程桌面连接到防火墙公共 IP 地址，并登录到“Srv-Work”虚拟机。
2.  打开 Internet Explorer 并浏览到 https://www.google.com。
3.  在 Internet Explorer 安全警告中选择“确定” > “关闭”。 应会看到 Google 主页。
4.  浏览到 https://www.microsoft.com 。 防火墙应会阻止你访问。

现已验证防火墙规则可正常工作：
- 可以浏览到一个允许的 FQDN，但不能浏览到其他任何 FQDN。
- 可以使用配置的外部 DNS 服务器解析 DNS 名称。
 
>**** 备注：学生现在应该能够完成 LAB_03




>**** 备注：学生现在应能够完成 LAB_04
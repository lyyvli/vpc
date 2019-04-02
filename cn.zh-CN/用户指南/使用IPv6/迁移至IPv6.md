# 迁移至IPv6 {#concept_lfq_n5z_dgb .concept}

您可以为已创建的IPv4协议的VPC开启IPv6通信，IPv4和IPv6通信彼此独立。

## 教程说明 {#section_msx_kvz_dgb .section}

本教程以一个IPv4网段为192.168.0.0/16的VPC为例。该VPC的交换机部署了一个对外提供服务的Web服务器，该ECS实例通过绑定的弹性公网IP对外提供服务。

在完成以下操作后，您部署在ECS实例上的Web应用可以被IPv6客户端通过互联网访问：

-   [步骤一：为已有IPv4 VPC开通IPv6](#section_lyv_gyz_dgb)

    为已有的VPC开通IPv6，分配IPv6地址段。开通后，系统会为您的VPC创建一个IPv6网关。您可以通过IPv6网关管理IPv6访问。更多详细信息，请参考[什么是IPv6网关？](../../../../../cn.zh-CN/产品简介/什么是IPv6网关？.md#)。

-   [步骤二：为ECS实例分配IPv6地址](#section_wwh_nzz_dgb)

    为已有的ECS实例分配IPv6地址。确保您的ECS实例类型支持IPv6，实例规格参见[实例规格族](cn.zh-CN/实例/实例规格族/实例规格族汇总.md#)。

-   [步骤三：配置ECS实例](#section_qqz_4dd_2gb)

    配置ECS实例，将分配的IPv6地址添加到实例网卡上。

-   [步骤四：配置安全组规则](#section_ugx_1jr_dgb)

    为了使ECS实例通过IPv6接收和发送流量，您需要添加针对IPv6地址的安全组规则。

-   [（可选）步骤五：配置IPv6公网带宽](#section_vys_jqd_2gb)

    默认IPv6地址只具备私网通信能力。如果您需要通过该IPv6地址访问互联网或被互联网中的IPv6客户端访问，您需要该IPv6地址购买公网带宽。


## 步骤一：为已有IPv4 VPC开通IPv6 {#section_lyv_gyz_dgb .section}

完成以下操作，为已创建的VPC开通IPv6：

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com)。
2.  在专有网络列表页面，选择目标VPC，然后单击**开通IPv6**。

    **说明：** 目前，仅华北5（呼和浩特地域）支持开通IPv6。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80667/155417381534512_zh-CN.png)

3.  在弹出的对话框，选择**自动开启VPC内所有交换机IPv6功能**，然后单击**确定**。

    开通后，系统会为您的VPC从IPv6地址池中分配一个56位掩码的IPv6网段并创建一个免费版的IPv6网关。


## 步骤二：为ECS实例分配IPv6地址 {#section_wwh_nzz_dgb .section}

在分配IPv6地址前，确保您的ECS实例类型支持IPv6，且ECS实例的状态为运行中或已停止。实例规格请参见[实例规格族](cn.zh-CN/实例/实例规格族/实例规格族汇总.md#)。

完成以下操作，为ECS实例分配IPv6地址：

1.  登录[ECS控制台](https://ecs.console.aliyun.com/#/home)。
2.  在左侧导航栏，单击**实例**。
3.  单击目标ECS实例的ID。
4.  在 配置信息 区域， 单击**更多** \> **管理辅助私网IP** 。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80667/155417381634513_zh-CN.png)

5.  单击 **分配IPv6地址**。
6.  选择IPv6地址分配方式。本操作选择**自动分配**。
7.  单击**修改**。

    刷新实例详情页面，查看分配的IPv6地址。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80667/155417381634514_zh-CN.png)


## 步骤三：配置ECS实例 {#section_qqz_4dd_2gb .section}

分配IPv6地址后，您需要将分配的IPv6地址配置到网络接口上。您可以为实例自动配置IPv6地址和手动配置IPv6地址，推荐您使用更高效的自动配置工具配置IPv6地址。

详细信息，请参考[为Linux实例配置IPv6地址](../../../../../cn.zh-CN/网络/配置IPv6地址/Linux实例配置IPv6地址/步骤4：配置IPv6地址.md#)和[为Windows实例配置IPv6地址](../../../../../cn.zh-CN/网络/配置IPv6地址/Windows实例配置IPv6地址/步骤4：配置IPv6地址.md#)。

本操作以CentOS 7系统为例，为您示范如何自动配置IPv6地址。

1.  远程连接实例。
2.  执行`wget http://ecs-image-utils.oss-cn-hangzhou.aliyuncs.com/ipv6/rhel/ecs-utils-ipv6`下载CentOS 7系统自动配置工具。
3.  执行`chmod +x ./ecs-utils-ipv6`修改执行权限，然后执行`./ecs-utils-ipv6`。
4.  执行`ifconfig`查看IPv6地址信息。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80667/155417381634516_zh-CN.png)


## 步骤四：配置安全组规则 {#section_ugx_1jr_dgb .section}

为了使ECS实例通过IPv6接收和发送流量，您需要添加针对IPv6地址的安全组规则。

本操作中ECS实例部署的服务要通过公网被IPv6客户端访问，所以需要添加一条入方向的安全组规则。操作如下：

1.  在ECS实例列表页面，单击已创建的ECS实例ID。
2.  在ECS实例详情页面，单击**本实例安全组**，然后单击**安全组列表**页签。
3.  单击**配置规则**，然后单击**添加安全组规则**进行配置。

    本操作中的安全组配置如下：

    -   **规则方向**：入
    -   **授权策略**：允许
    -   **协议类型**：全部
    -   **授权类型**：IPv6地址段访问
    -   **授权对象**：::/0

## （可选）步骤五：配置IPv6公网带宽 {#section_vys_jqd_2gb .section}

默认IPv6地址只具备私网通信能力。如果您需要通过该IPv6地址访问互联网或被互联网中的IPv6客户端访问，您需要该IPv6地址购买公网带宽。

完成以下操作，购买公网带宽：

1.  在专有网络控制台的左侧导航栏，单击**IPv6网关**。
2.  找到目标IPv6网关，然后单击**管理**。
3.  在左侧导航栏，单击**IPv6公网带宽**。
4.  找到ECS实例使用的IPv6地址，然后单击**开通公网带宽**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80667/155417381634537_zh-CN.png)

5.  选择一种费方式和公网带宽，然后完成支付。


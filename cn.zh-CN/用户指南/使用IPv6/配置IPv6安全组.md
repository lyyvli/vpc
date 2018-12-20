# 配置IPv6安全组 {#task_wl1_3l2_2gb .task}

IPv4和IPv6通信彼此独立。您需要为ECS实例单独配置IPv6安全组规则。

1.  登录[ECS控制台](https://ecs-cn-huhehaote.console.aliyun.com/#/server/i-hp32kande23gqr6shdlr/group/egress?regionId=cn-huhehaote)。 
2.  在左侧导航栏，单击**网络和安全** \> **安全组**。 
3.  找到目标安全组，然后单击**配置规则**。 
4.  单击**添加安全组规则**。 
5.  配置安全组规则，授权类型选择**IPv6地址段访问**，然后输入授权的IPv6地址段。如果输入::/0则代表所有IPv6地址。 安全组详细的配置说明，请参考[创建安全组](../../../../cn.zh-CN/用户指南/安全组/创建安全组.md#)。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/80686/154531149734557_zh-CN.png)



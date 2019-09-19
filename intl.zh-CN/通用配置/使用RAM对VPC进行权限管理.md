# 使用RAM对VPC进行权限管理 {#task_1925765 .task}

本文介绍了通过RAM的权限管理功能，创建相应的权限策略，从而对专有网络（VPC）进行权限管理，以满足RAM用户操作VPC的多种需求。

请确保您已经注册了阿里云账号。如还未注册，请先完成账号注册。详细信息，请参见[账号注册](https://account.alibabacloud.com/register/intl_register.htm)。

## 基本信息 {#section_5z6_u2v_8kj .section}

使用RAM对VPC进行权限管理前，请先了解几个常用的权限策略。

|权限策略|描述|
|:---|:-|
|AliyunVPCFullAccess|为RAM用户授予VPC的完全管理权限。|
|AliyunVPCReadOnlyAccess|为RAM用户授予VPC的只读访问权限。|

**说明：** VPC的权限定义，请参见[RAM鉴权](../../../../intl.zh-CN/API参考/RAM鉴权.md#)。

## 将自定义权限策略授权给RAM用户 {#section_5on_sav_ceq .section}

1.  创建自定义权限策略。 详细信息，请参见[创建自定义策略](../../../../intl.zh-CN/权限策略管理/自定义策略/创建自定义策略.md#)和[VPC授权样例](#section_vgp_w4w_fwd)。
2.  在权限策略管理页面，找到目标权限策略，单击其权限策略名称。
3.  单击**引用目录**页签，然后单击**新增授权**。
4.  在添加权限页面，**被授权主体**处输入需要授权的用户名称或ID，然后单击**确定**。 

    **说明：** 您也可以直接对用户或用户组授予创建好的权限策略，详情信息，请参见[为RAM用户授权](../../../../intl.zh-CN/用户管理/为RAM用户授权.md#)和[为用户组授权](../../../../intl.zh-CN/用户组管理/为用户组授权.md#)。


## VPC授权样例 {#section_vgp_w4w_fwd .section}

-   示例1：对VPC的管理权限

    假设您的账号为1234567，授权管理该账号下的所有VPC，使某个RAM用户具有操作所有VPC的权限。

    ``` {#codeblock_omm_c2c_dtn}
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*"
                ],
                "Resource": [
                    "acs:vpc:*:1234567:*/*"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "ecs:*Describe*"
                ],
                "Resource": [
                    "*"
                ]
            }
        ]
    }
    ```

-   示例2：对VPC中VSwitch的管理授权

    假设您只想授权青岛Region下的VSwitch的管理权限，使某个RAM用户可以对青岛Region下的VSwitch进行创建/删除/绑定子网路由/解绑子网路由的操作，对于其它地域的VSwitch只有查看权限。

    ``` {#codeblock_y7x_v5z_ujy}
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*Describe*",
                    "vpc:*VSwitch*",
                    "vpc:*RouteTable*"
                ],
                "Resource": [
                    "acs:vpc:cn-qingdao:*:*/*"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "ecs:*Describe*"
                ],
                "Resource": [
                    "*"
                ]
            }
        ]
    }
    ```

-   示例3：只允许操作特定地域下的路由表以及路由表中的路由条目

    假设您的账号为11111111，在多个地域创建了VPC，该权限只授予某个RAM用户对杭州地域VPC的操作权限，且操作权限仅限于：允许新增/删除路由条目，允许创建子网路由并绑定VSwtich，对于其它地域的云产品只有查看权限。

    ``` {#codeblock_sbb_rrt_f9x}
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "ecs:*Describe*"
                ],
                "Resource": [
                    "*"
                ],
                "Condition": {}
            },
            {
                "Effect": "Allow",
                "Action": [
                    "slb:*Describe*"
                ],
                "Resource": [
                    "*"
                ],
                "Condition": {}
            },
            {
                "Effect": "Allow",
                "Action": [
                    "rds:*Describe*"
                ],
                "Resource": [
                    "*"
                ],
                "Condition": {}
            },
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*Describe*",
                    "vpc:*RouteEntry*",
                    "vpc:*RouteTable*"
                ],
                "Resource": [                
    "acs:vpc:cn-hangzhou:11111111:*/*"
                ],
                "Condition": {}
            }
        ]
    }
    ```

-   示例4：只允许修改特定路由表中的路由条目

    假设您只希望RAM用户新增/删除特定路由表中的路由条目。

    ``` {#codeblock_sbi_ni8_tbj}
    {
        "Version": "1",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*RouteEntry*"
                ],
                "Resource": [
                    "acs:vpc:cn-qingdao:*:routetable/vtb-m5e64ujkb7xn5zlq0xxxx"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "vpc:*Describe*"
                ],
                "Resource": [
                    "*"
                ]
            },
            {
                "Effect": "Allow",
                "Action": [
                    "ecs:*Describe*"
                ],
                "Resource": [
                    "*"
                ]
            }
        ]
    }
    ```



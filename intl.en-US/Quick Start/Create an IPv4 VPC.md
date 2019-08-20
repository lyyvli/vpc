# Create an IPv4 VPC {#task_1512598 .task}

This topic describes how to create a VPC network with an IPv4 address block. After you create a VPC, you can create an ECS instance that can be associated with an EIP in the VPC so that the ECS instance can access the Internet.

## Step 1: Create a VPC and a VSwitch {#section_ts2_ab8_rfj .section}

To deploy cloud resources in a VPC, you must complete network planning. For more information, see [Plan a VPC network](../reseller.en-US/Quick Start/Plan a VPC network.md#).

To create a VPC and a VSwitch, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  Select the region in which you want to create a VPC. 

    The VPC must be in the same region as the cloud resources that you want to deploy. In this topic, **China \(Qingdao\)** is selected.

3.  On the VPCs page, click **Create VPC**.
4.  On the Create VPC page, configure the VPC and the VSwitch, and then click **OK**. 

    **Note:** In this topic, select **Default** in the IPv6 CIDR block field.

    |Configuration|Description|
    |:------------|:----------|
    |**VPC**|
    |**Region**|The region in which the VPC is created.|
    |**Name**|Enter a name for the VPC. The name must be 2 to 128 characters in length and can contain letters, numbers, underscores \(\_\), and hyphens \(-\). It must start with a letter.

 |
    |**IPv4 CIDR Block**|Select an IPv4 CIDR block. Options:     -   **Default CIDR Block**: Select 192.168.0.0/16, 172.16.0.0/12, or 10.0.0.0/8.
    -   **Custom CIDR Block**: Select 192.168.0.0/16, 172.16.0.0/12, 10.0.0.0/8, or their subnets. The CIDR block mask must be 8 to 24 bits in length. In this example, select 192.168.0.0/16. If you want to use a public CIDR block as the CIDR block of the VPC, open a ticket.
 **Note:** After the VPC is created, you cannot change its IPv4 CIDR block.

 |
    |**IPv6 CIDR Block**|Select whether to allocate an IPv6 CIDR block to the VPC. By default, no IPv6 CIDR block is allocated. If you select to allocate an IPv6 CIDR block, an IPv6 CIDR block is automatically allocated to your VPC free of charge, for example, 2xx1:db8::/56. By default, IPv6 addresses only support private network communication. If you want to access the Internet through this IPv6 address or be accessed by IPv6 clients on the Internet, you need to activate IPv6 Internet bandwidth.

 **Note:** After the VPC is created, you cannot change its IPv6 CIDR block.

 |
    |**Description**|Enter a description for the VSwitch. The description must be 2 to 256 characters in length and cannot start with `http://` or `https://`.

 |
    |**Resource Group**|Select the resource group to which the VPC belongs.|
    |**VSwitch**|
    |**Name**|Enter a name for the VSwitch. The name must be 2 to 128 characters in length and can contain letters, numbers, underscores \(\_\), and hyphens \(-\). It must start with a letter.

 |
    |**Zone**|Select a zone for the VSwitch. In a VPC, VSwitches in different zones can communicate with each other through the intranet.|
    |**Zone Resource**|The cloud resource instances that can be created in the selected zone. The cloud resources that can be created in different zones vary with time periods. The inventory status of specific instance types can be queried on the purchase page. Only the inventory status of ECS, RDS, and SLB can be queried.

 |
    |**IPv4 CIDR Block**|Enter the IPv4 CIDR block of the VSwitch. When you specify the CIDR block of the VSwitch, note the following limits:     -   The CIDR block of the VSwitch can be the same as that of the VPC to which it belongs, or a subnet of the VPC CIDR block.

For example, if the CIDR block of the VPC is 192.168.0.0/16, the CIDR block of the VSwitch can be 192.168.0.0/16, or any CIDR block between 192.168.0.0/17 and 192.168.0.0/29.

**Note:** If the CIDR block of the VSwitch is the same as that of the VPC to which it belongs, you can only create one VSwitch in the VPC.

    -   The size of the mask for the VSwitch can be /16 to /29, which can provide 8 to 65,536 IP addresses.
    -   The first and last three IP addresses are reserved by the system.

For example, if the CIDR block of the VSwitch is 192.168.1.0/24, the IP addresses 192.168.1.0, 192.168.1.253, 192.168.1.254, and 192.168.1.255 are reserved.

    -   If the VSwitch needs to communicate with VSwitches in other VPCs or with on-premises data centers, make sure that the CIDR blocks involved do not conflict with each other.
 **Note:** After the VSwitch is created, you cannot modify its CIDR block.

 |
    |**Number of Available Private IPs**|The number of available private IP addresses.|
    |**IPv6 CIDR Block**|Enter the IPv6 CIDR block of the VSwitch. The mask for the IPv6 CIDR block of the VSwitch is /64. You can enter a value from 0 to 255 to define the last eight bits of the IPv6 CIDR block.

 For example, if the IPv6 CIDR block of the selected VPC is 2xx8:4004:c0:b900::/56 and you enter 255 \(ff in hexadecimal notation\), the IPv6 CIDR block of the VSwitch is 2xx8:4004:c0:b9ff::/64.

 |
    |**Description**|Enter a description for the VSwitch. The description must be 2 to 256 characters in length and cannot start with `http://` or `https://`.

 |


## Step 2: Create an ECS instance {#section_o0d_7va_dk9 .section}

To create an ECS instance in the VPC, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **VSwitches**.
3.  Select the region to which the target VSwitch belongs. In this topic, select **China \(Qingdao\)**.
4.  On the VSwitches page, find the target VSwitch, and then choose **Purchase** \> **ECS Instance** in the **Actions** column.
5.  On the Custom Launch page, configure the ECS instance, and then click **confirm to pay**. 

    The networking parameters are set as follows:

    -   **Network Type**: Select the created VPC and VSwitch.
    -   **Assign Public IP Address**: Do not select this checkbox.
    -   **Security Group**: Use the default security group.
6.  Go back to the ECS console to view the created ECS instance. 

    ![View the created ECS instance](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2434/156629703854444_en-US.png)


## Step 3: Create an EIP and associate it with the ECS instance {#section_avr_zkv_582 .section}

An EIP is a public IP address that you can purchase individually. You can associate an EIP with an ECS instance in a VPC to enable the ECS instance to access the Internet.

To create an EIP and associate it with the ECS instance, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.console.aliyun.com/#/vpc).
2.  In the left-side navigation pane, click **Elastic IP Addresses**.
3.  On the Elastic IP Addresses page, click **Create EIP**.
4.  On the Elastic IP page, configure the EIP, and then click **Buy Now** and complete the payment. For information about EIP billing, see [Pay-As-You-Go](../../../../../reseller.en-US/Pricing/Pay-As-You-Go.md#).
5.  On the Elastic IP Addresses page, find the target EIP, and then click **Bind** in the **Actions** column.
6.  On the Bind Elastic IP Address page, complete the following configurations, and then click **OK**. 
    -   **Instance Type**: Select ECS Instance.
    -   **ECS Instance**: Select the ECS instance to be associated with the EIP.

## Step 4: Test access to the Internet {#section_qlb_0xv_o70 .section}

After the EIP is associated with the ECS instance, the ECS instance can communicate with the Internet. You can use the associated EIP address to access the ECS instance.

**Note:** Remote access must be allowed by the security group rules of the ECS instance. For more information, see [Typical applications of commonly used ports](../../../../../reseller.en-US/Security/Security groups/Typical applications of commonly used ports.md#).


# Cases for configuring ECS security groups {#concept_z13_qvd_sdb .concept}

When creating an ECS instance of the VPC network, you can either use the default security group or use other existing security groups in the VPC. A security group is a virtual firewall used to control the inbound and outbound traffic of an ECS instance.

This topic lists some common security group configurations for ECS instances of the VPC network.

## Case 1: Intranet communication {#section_qnk_5vd_sdb .section}

The following are two types of communication methods between ECS instances of the VPC network:

-   By default, ECS instances in the same security group of the same VPC can communicate with each other.
-   ECS instances in different VPCs cannot communicate with each other. To achieve communication between two ECS instances in different VPCs, use Express Connect, VPN Gateway, or CEN to connect them. When doing so, make sure the security group rules allow access between the target ECS instances, as shown in the following table.

    |Security group rules|Rule direction|Authorization policy|Protocol type and port range|Authorization type|Authorization object|
    |:-------------------|:-------------|:-------------------|:---------------------------|:-----------------|--------------------|
    |Security group configurations for the ECS instance in VPC 1|Inbound|Allow| Windows: RDP

 3389/3389

 |Address field access| Enter the private IP address to access the ECS instance.

 To allow the access of any ECS instance, enter 0.0.0.0/0.

 |
    |Inbound|Allow| Linux: SSH

 22/22

 |Address field access|
    |Inbound|Allow| Custom TCP

 Custom

 |Address field access|
    |Security group configurations for the ECS instance in VPC 2|Inbound|Allow| Windows: RDP

 3389/3389

 |Address field access| Enter the private IP address to access the ECS instance.

 To allow the access of any ECS instance, enter 0.0.0.0/0.

 |
    |Inbound|Allow| Linux: SSH

 22/22

 |Address field access|
    |Inbound|Allow| Custom TCP

 Custom

 |Address field access|


## Case 2: Deny the access of specific IP addresses or ports {#section_hwk_fyd_sdb .section}

You can configure security groups to deny the access of specific IP addresses or ports to an ECS instance.

|Security group rules|Rule direction|Authorization policy|Protocol type and port range|Authorization type|Authorization object|
|:-------------------|:-------------|:-------------------|:---------------------------|:-----------------|--------------------|
|Deny the access of a specific IP address range to all ports of the ECS instance|Inbound|Drop| All

 -1

 |Address field access| Enter the IP address range to block, in the form of CIDR block, such as 10.0.0.1/32.

 |
|Deny the access of a specific IP address range to port 22 of the ECS instance|Inbound|Drop| SSH \(22\)

 22/22

 |Address field access| Enter the IP address range to block, in the form of CIDR block, such as 10.0.0.1/32.

 |

## Case 3: Allow the remote access of a specific IP address {#section_yyf_qyd_sdb .section}

If you have configured a NAT Gateway or EIP for an ECS instance in a VPC, you can add the following security group rules to allow Windows remote logon or Linux SSH logon.

|Security group rules|Rule direction|Authorization policy|Protocol type and port range|Authorization type|Authorization object|
|:-------------------|:-------------|:-------------------|:---------------------------|:-----------------|--------------------|
|Allow Windows remote logon|Inbound|Allow| RDP

 3389/3389

 |Address field access| To allow the logon of any public IP address, enter 0.0.0.0/0.

 To allow only the remote logon of a specific IP address, enter the IP address.

 |
|Allow Linux SSH logon| Inbound|Allow| SSH

 22/22

 |Address field access| To allow the logon of any public IP address, enter 0.0.0.0/0.

 To allow only the remote logon of a specific IP address, enter the IP address.

 |

## Case 4: Allow access from the Internet to the HTTP/HTTPS service deployed on the ECS instance {#section_mgp_gzd_sdb .section}

If you have deployed a website on an ECS instance in a VPC and configured an EIP or NAT Gateway to provide services, configure the following security group rules to allow access from the Internet.

|Security group rules|Rule direction|Authorization policy|Protocol type and port range|Authorization type|Authorization object|
|:-------------------|:-------------|:-------------------|:---------------------------|:-----------------|--------------------|
|Allow access to port 80| Inbound|Allow| HTTP

 80/80

 |Address field access|0.0.0.0/0|
|Allow access to port 443| Inbound|Allow| HTTPS

 443/443

 |Address field access|0.0.0.0/0|
|Allow access to port 80|Inbound|Allow| TCP

 80/80

 |Address field access|0.0.0.0|


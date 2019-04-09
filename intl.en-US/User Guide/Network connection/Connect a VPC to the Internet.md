# Connect a VPC to the Internet {#concept_zr3_rr4_4gb .concept}

You can use Elastic IP Address \(EIP\) or NAT Gateway to allow cloud resources in a VPC to access the Internet.

## Overview {#section_yjs_ts4_4gb .section}

By default, cloud resources in a VPC cannot access the Internet or be accessed from the Internet. You can configure a public IP address or a NAT Gateway so that the VPC can communicate with the Internet.

In addition, VPC provides Internet Shared Bandwidth and Data Transfer Plan to help you save Internet cost. For more information, see [How to save the Internet cost?](../../../../../reseller.en-US/Best practices/How to save the Internet cost?.md#)

## EIP {#section_uxs_ct4_4gb .section}

An Elastic IP Address \(EIP\) is a public IP address resource that you can purchase and possess independently. An EIP is a type of NAT IP address. It is located on the Internet gateway of Alibaba Cloud, and is mapped to the attached resource, then the resource can communicate with the Internet through the EIP.

Currently, you can attach an EIP to an ECS instance of the VPC network, an ENI, an intranet SLB instance of the VPC network, or a NAT Gateway. For more information, see [EIP user guide](../../../../../reseller.en-US/User Guide/Create an EIP.md#).

The benefits of EIP are as follows:

-   Independently purchased and possessed

    You can purchase an EIP as an independent resource instead of purchasing it together with other computing or storage resources.

-   Flexible attaching

    You can attach an EIP to a resource that needs to access the Internet and detach and release the EIP when it is unneccessary to avoid additional cost.

-   Configurable network capability

    You can adjust the bandwidth of an EIP as needed. The bandwidth change takes effect immediately.


## NAT Gateway {#section_hpy_d54_4gb .section}

NAT Gateway is an enterprise-class VPC Internet gateway that provides NAT proxy services \(SNAT and DNAT\), the forwarding capacity of up to 10 Gbps, and cross-zone disaster recovery.

With NAT Gateway, multiple ECS instances of the VPC network can access the Internet through one public IP address. For more information, see [NAT Gateway user guide](../../../../../reseller.en-US/Quick Start/Create a NAT gateway.md#).

The benefits of NAT Gateway are as follows:

-   Flexible and easy-to-use

    As an enterprise-class Internet gateway for VPC, NAT Gateway provides SNAT and DNAT functions, which means you can directly configure SNAT and DNAT rules without setting up a NAT Gateway by yourself.

-   High availability

    The NAT gateway is a virtual network hardware which is based on the self-developed distributed gateway of Alibaba Cloud and virtualized by SDN technology. With the forwarding capacity of up to 10 Gbps, NAT Gateway supports large-scale Internet applications.

-   Pay-AS-You-Go billing

    You can change the gateway specification as well as the specifications and number of EIPs at any time to meet changing service requirements.



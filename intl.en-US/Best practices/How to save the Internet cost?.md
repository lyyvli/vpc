# How to save the Internet cost? {#concept_aqz_v45_sdb .concept}

You can use Internet Shared Bandwidth and Data Transfer Plan to save the Internet cost.

## Data Transfer Plan {#section_ugb_hr5_sdb .section}

After you purchase a Data Transfer Plan, traffic fee is automatically deducted from the plan and no additional operation is required. You can view the usage of Data Transfer Plan of different products in [Billing Management - Resource Packages](https://expense.console.aliyun.com/?spm=5176.doc55774.2.5.zPwbsg#/flow/list/).

This section analyzes Data Transfer Plan from the following aspects:

-   How much can Data Transfer Plan save?

    Data Traffic Package supports Idle-time Data Transfer Plan with lower price. Take Hong Kong, China as an example. The prices of Pay-As-You-Go traffic, Full-time Data Transfer Plan and Idle-time Data Transfer Plan are as follows:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2450/1565791396830_en-US.jpg)

    Take the 5-TB Data Transfer Plan in Hong Kong, China region as an example. The cost comparison is as follows. You can find that Data Transfer Plan saves a lot of traffic costs.

    |Hong Kong, China 5-TB traffic|Unit price \(Yuan/GB\)|Total price \(Yuan\)|Cost saved \(Yuan\)|Proportion of cost saved|
    |:----------------------------|:---------------------|:-------------------|:------------------|:-----------------------|
    |Pay-As-You-Go traffic|1|5120|0|0|
    |Full-time Data Transfer Plan|0.75|3727|1393|27.2%|
    |Idle-time Data Transfer Plan|0.51|2609|2511|49%|

-   What are the usage scenarios of Data Transfer Plan?

-   Data Transfer Plan instructions

    -   Data Transfer Plan has a validity period. After a plan expires, the remaining traffic in the plan cannot be used. We recommend that you choose the specification of Data Transfer Plan according to the history usage of the service system. You can purchase a small-specification plan first and buy more in the future to avoid wasting.

    -   After a Data Transfer Plan is used up, traffic further used by the service is billed as Pay-As-You-Go traffic and the service is not interrupted.

    -   If you have purchased multiple Data Transfer Plans, traffic in the Data Transfer Plan to expire first is deducted first.


## Internet Shared Bandwidth {#section_isl_5r5_sdb .section}

Internet Shared Bandwidth is an independent bandwidth product that provides high-quality multi-line BGP bandwidth and various billing methods. You can add EIPs to Internet Shared Bandwidth so that the EIPs can share the bandwidth. You can bind EIPs to ECS instances of the VPC network, NAT Gateways, and SLB instances of the VPC network, so that these products can use Internet Shared Bandwidth.

Besides, Internet Shared Bandwidth provides rich billing methods, including 95 billing, billing by fixed bandwidth, and more. Using Internet Shared Bandwidth and the rich billing methods can effectively save bandwidth cost and provide strong elastic service capability. See [Understand Internet Shared Bandwidth through one figure](https://yq.aliyun.com/articles/185545?spm=a2c4g.11186623.2.6.bTGD2h) to quickly know about Internet Shared Bandwidth.

**Note:** Internet Shared Bandwidth is an independent bandwidth product that does not contain any public IP by default. You can add EIPs to Internet Shared Bandwidth.

The bandwidth sharing function of Internet Shared Bandwidth helps you reduce Internet bandwidth cost, especially in the case of great bandwidth fluctuation. Suppose you have 10 ECS instances in Hong Kong, China and all the instances are bound to EIPs. If billing by bandwidth is adopted, the peak bandwidth is 100 Mbps. You must pay 3253 Yuan/day, which is the cost of 10 EIPs with the peak bandwidth of 100 Mbps, as shown in the following figure.

Traffic analysis of the 10 public IPs shows that the services differ in bandwidth fluctuation. The peak outbound bandwidth of the 10 servers is about 500 Mbps, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2450/1565791396832_en-US.png)

Therefore, if you use Internet Shared Bandwidth, you only need to buy a 500-Mbps Internet Shared Bandwidth and the 10 ECS instances can use it. In this way, each ECS instance can use peak bandwidth five times that of the original one, and you only need to pay 1680 Yuan per day, the cost of the 500-Mbps bandwidth. Thus 1573 Yuan, that is, 50% bandwidth cost, is saved.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/2450/1565791397833_en-US.png)

Internet Shared Bandwidth also provides 95 billing and "unlimited" peak bandwidth. The billing is based on the actual bandwidth usage minus the abrupt peak bandwidth. In this way, the bandwidth cost is saved and the impact of limited bandwidth on service is avoided. It is especially difficult for users with great bandwidth fluctuation to estimate a reasonable peak bandwidth. A high peak bandwidth will cause wasting; and a low peak bandwidth will cause packet loss and further affect service development and user experience. In this case, you can choose 95 billing.

Therefore, if you have multiple EIPs and experience obvious bandwidth fluctuation, using Internet Shared Bandwidth can greatly save the cost. You can choose 95 billing for services frequently experiencing abrupt bandwidth peak, thus the impact of limited peak bandwidth on the service and the cost wasting caused by high peak bandwidth are avoided.

**Note:** You must analyze the traffic model of the system to select an appropriate billing mode:

-   For systems with stable traffic, you can choose the Subscription billing mode by bandwidth, which can save 20%-30% cost compared with Pay-As-You-Go billing by bandwidth.

-   You can choose 95 billing for services frequently experiencing abrupt bandwidth peak.



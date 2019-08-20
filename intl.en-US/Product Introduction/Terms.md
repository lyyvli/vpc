# Terms {#concept_o1y_bmz_ndb .concept}

This topic describes the terms about VPCs.

|Term| Description|
|:---|:-----------|
|Virtual Private Cloud \(VPC\)|A VPC is a private network established in Alibaba Cloud. VPCs are logically isolated from each other. You can create and manage cloud resources in your VPC, such as ECS, SLB, and RDS.|
|VSwitch|A VSwitch is a basic network device that connect different cloud resources in a VPC. When you create a cloud resource in a VPC, you must specify the VSwitch to which the cloud resource is connected.|
|VRouter|A VRouter is a hub that connects all VSwitches in a VPC and serves as a gateway that connects the VPC to other networks. A VRouter also forwards network traffic according to the route entries in its route table.|
|Route Table|A route table is a list of route entries in a VRouter.|
|Route Entry|Each item in a route table is a route entry. A route entry specifies the next hop address for the network traffic directed to a destination CIDR block. Route entries are divided into system route entries and custom route entries.|


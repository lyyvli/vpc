# Limits {#concept_dyx_jkx_5db .concept}

The following table describes the limits that apply to VPCs.

|Resource|Limit|Quota increase supported?|
|:-------|:----|:------------------------|
|Maximum number of VPCs per region|10|Yes. Open a ticket.|
|Available CIDR blocks|192.168.0.0/16, 172.16.0.0/12, 10.0.0.0/8, and their subnets|Yes. Open a ticket.|
|Maximum number of VRouters per VPC|1|No.|
|Maximum number of VSwitches per VPC|24|Yes. Open a ticket.|
|Maximum number of route tables per VPC|10|Yes. Open a ticket.|
|Maximum number of custom route entries per route table|48|Yes. Open a ticket.|
|Maximum number of network addresses used by a single VPC to support cloud products For example, if an ECS instance has only one private IP address, the ECS instance uses one network address. If an ECS instance is associated with multiple NICs or an NIC is configured with multiple IP addresses, the number of network addresses used by the ECS instance is the sum of the VPC addresses assigned to these NICs.

 |15,000|No.|


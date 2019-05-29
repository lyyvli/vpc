# AssociateEipAddress {#doc_api_Vpc_AssociateEipAddress .reference}

Associates an EIP with a cloud product instance in the same region.

Note the following when you call this action:

-   You can associate an EIP with a VPC ECS instance, a VPC SLB instance, or a NAT Gateway in the same region.
-   To associate an EIP with a NAT Gateway, make sure that there was no NAT bandwidth package under your account before January 26, 2018. Otherwise open a ticket to associate the EIP with the NAT Gateway.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=AssociateEipAddress), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AssociateEipAddress|The name of this action. Value: **AssociateEipAddress**.

 |
|AllocationId|String|Yes|eip-2zeerraiwb7ujxxxxxxxx|The ID of the EIP.

 |
|InstanceId|String|Yes|i-2zebb08phyczxxxxxxxx|The ID of the instance to associate.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the EIP belongs.

 |
|InstanceRegionId|String|No|cn-hangzhou|The ID of the region to which the associated instance belongs.

 |
|InstanceType|String|No|EcsInstance|The type of the cloud product instance to associate. Valid values: **Nat|SlbInstance|EcsInstance|NetworkInterface**.

 |
|Mode|String|No|NAT|The mode of associating. Valid values: **NAT | MULTI\_BINDED**.

 |
|PrivateIpAddress|String|No|192.xx.xx.4|An IP address in the CIDR block of the VSwitch.

 If you leave the option empty, the system allocates a private IP address according to the VPC ID and VSwitch ID.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|C0FD0EED-F90D-4479-803D-DD62335357E5|The ID of the request. 

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://vpc.aliyuncs.com/? Action=AssociateEipAddress
&AllocationId=eip-2zeerraiwb7ujxxxxxxxx
&InstanceId=i-2zebb08phyczxxxxxxxx
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<AssociateEipAddressResponse>
  <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
</AssociateEipAddressResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message |Description|
|----------------|----------|--------------|-----------|
|400 |InvalidAssociation.Duplicated|Specified instance already is associated.|This instance is already associated with an EIP or a Global Acceleration instance. You must delete this instance before you can associate it with a different EIP or Global Acceleration instance.|
|400|OperationDenied|Specified instance is not in VPC.|The specified instance does not exist in the VPC.|
|400|InvalidParameter.Mismatch|Specified elastic IP address and ECS instance are not in the same region.|The specified EIP and ECS instance are not in the same region.|
|400|IncorrectEipStatus|Current elastic IP status does not support this operation|The current status of the specified EIP address does not support this operation.|
|404|InvalidInstanId.NotFound|Specified instance does not exist.|The specified instance does not exist.|
|400|IncorrectInstanceStatus|Current instance status does not support this operation.|The current instance status does not support this operation.|
|400|InvalidInstanceType.ValueNotSupported|The specified value of InstanceType is not supported.|The value of the InstanceType parameter is invalid.|
|400|IncorrectHaVipStatus|HaVip can be operated by this action only when it's status is Available or InUse.|You can perform this operation only if the HAVIP is the Available or InUse state.|
|400|InvalidParameter|The specified parameter is not valid.|The specified parameter value is invalid.|
|400|OperationDenied|Eip of default vpc not allow this operation|The EIP of the default VPC does not support this operation.|
|400|Forbbiden|The eip instance owener error|You need to be authorized to call the EIP. Please check that you have the appropriate permissions and try again.|
|400|InvalidBindingStatus|The eip binding status invalid.|The associating status of the EIP is invalid.|
|400|BIND\_INSTANCE\_HAVE\_PORTMAP\_OR\_BIND\_EIP|The instance may have portMap or already bind eip.|You must delete the existing port forwarding rule associated with the ECS instance first.|
|400|BIND\_INSTANCE\_OWENER\_ERROR|Cannot operate the eip.|You cannot operate this EIP.|
|404|InvalidAllocationId.NotFound|Specified allocation ID is not found|The specified public IP address does not exist.|
|400|InvalidParams.NotFound|instance not found|The specified instance does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)


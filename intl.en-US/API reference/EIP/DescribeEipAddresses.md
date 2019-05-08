# DescribeEipAddresses {#reference_i4w_xmt_ndb .reference}

Queries EIPs in a region.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeEipAddresses| The name of this action. Value:

 DescribeEipAddresses

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the EIP belongs.

 To query the region ID, call DescribeRegions.

 |
|AllocationId|String|No|eip-2zeerraiwb7ujxxxxxxxx| The ID of the EIP.

 |
|AssociatedInstanceId|String|No|i-2zebb08phycxxxxxxxx| The ID of the cloud resource to which the EIP is attached.

 |
|AssociatedInstanceType|String|No|EcsInstance| The cloud resource to which the EIP is bound. Valid values:

 -   EcsInstance \(default\): an ECS instance of the VPC network

-   SlbInstance: an SLB instance of the VPC network

-   Nat: NAT Gateway

-   HaVip: HAVIP instance


 Each ECS and SLB instance can be attached to only one EIP. However, a NAT Gateway can be attached to multiple EIPs.

 |
|ChargeType|String|No|PostPaid| The billing method of the EIP.

 -   **PostPaid**: Pay-As-You-Go.
-   **PrePaid**: Subscription.

 |
|EipAddress|String|No|116.xx.xx.28| The IP address of the EIP. After it is specified, you can view the information related to the EIP.

 |
|Filter.1.Key|String|No|Filter.1.Name| The filter condition to use.

 |
|Filter.1.Value|String|No|value1| The value of the corresponding filter condition.

 |
|Filter.2.Key|String|No|Filter.2.Description| The filter condition to use.

 |
|Filter.2.Value|String|No|value2| The value of the corresponding filter condition.

 |
|ISP|String|No|BGP| The service provider. In most cases, BGP data centers are used.

 |
|IncludeReservationData|Boolean|No|true| Indicates whether order data that has not taken effect is included. Default value: false.

 |
|LockReason|String|No|financial| The locking type.

 -   Financial: locked because the bill is overdue.
-   Security: locked for security protection.

 |
|PageNumber|Integer|No|10| The number of pages to return. Default value: 1.

 |
|PageSize|Integer|No|10| The number of rows per page. Maximum value: 50. Default value: 10.

 |
|ResourceGroupId|String|No|rg-acfmxazb4pxxxxxxxx| The ID of the resource group.

 |
|Status|String|No|Available| The status of the EIP. Valid values:

-   Associating: being attached

-   Unassociating: being detached

-   InUse: attached

-   Available: available


 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|EipAddresses|N/A|N/A| A list of EIPs.

 |
|└AllocationId|String|eip-2zeerraiwb7ujxxxxxxxx| The ID of the EIP.

 |
|└AllocationTime|String|2019-04-23T01:37:38Z| The time at which the EIP was created.

 |
|└AvailableRegions|N/A|cn-hangzhou| The ID of the region.

 |
|└Bandwidth|String|5| The peak bandwidth in Mbps of the EIP.

 |
|└BandwidthPackageId|String|cbwp-bp1ego3i4j07cxxxxxxxx| The ID of the Internet Shared Bandwidth to which the EIP is added.

 |
|└BandwidthPackageType|String|CommonBandwidthPackage| The type of the Internet Shared Bandwidth.

 |
|└ChargeType|String|PayByTraffic| The billing method of the EIP.

 |
|└Descritpion|String|Description| The description of the EIP.

 |
|└EipBandwidth|String|101| The bandwidth of the EIP before it is added to or removed from Internet Shared Bandwidth

 |
|└ExpiredTime|String|2019-04-29T02:37:38Z| The expiration time according to ISO8601 standard. UTC time must be used. Format: YYYY-MM-DDThh:mmZ.

 |
|└HDMonitorStatus|String|false| Indicates whether the EIP has enabled second-level monitoring.

 |
|└HasReservationData|String|wweayhddrhht|The value is **true** only if the **IncludeReservationData** parameter is **true** and there is order data that has not taken effect.|
|└ISP|String|BGP| The service provider. Usually, BGP data centers are used.

 |
|└InstanceId|String|vpc-bp15zckdt37xxxxxxxx| The ID of the instance to which the EIP is attached.

 |
|└InstanceRegionId|String|cn-hangzhou| The ID of the region to which the attached resource belongs.

 |
|└InstanceType|String|EcsInstance| The type of the attached instance.

 |
|└InternetChargeType|String|PayByBandwidth| The billing method of the EIP.

 |
|└IpAddress|String|101.xx.xx.36| The IP address of the EIP.

 |
|└Name|String|EIP| The name of the EIP.

 |
|└OperationLocks|N/A|financial| The reason that the EIP is locked. Valid values:

 -   financial: locked because the bill is overdue
-   security: locked for security protection

 |
|└LockReason|String|financial| The reason that the EIP is locked. Valid values:

 financial: locked because the bill is overdue

 security: locked for security protection

 |
|└RegionId|String|cn-hangzhou| The ID of the region to which the EIP belongs.

 |
|└ReservationActiveTime|String|2019-03-11T16:00:00Z| The time at which the renewal takes effect.

 |
|└ReservationBandwidth|String|12| The renewal bandwidth.

 |
|└ReservationInternetChargeType|String|PayByBandwidth| The payment type of renewal.

 |
|└ReservationOrderType|String|RENEWCHANGE| The type of the renewal order.

 -   RENEWCHANGE: renewal change
-   TEMP\_UPGRADE: temporary upgrade
-   UPGRADE: upgrade

 |
|└ResourceGroupId|String|rg-acfmxazxxxxxxxx| The ID of the resource group.

 |
|└Status|String|Associating| The status of the EIP.

 -   Associating: attaching
-   Unassociating: detaching
-   InUse: attached
-   Available: available

 |
|TotalCount|Integer|10| The number of queried entries.

 |
|PageNumber|Integer|10| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF| The ID of the request.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#codeblock_1sf_8xg_3yd}

https://vpc.aliyuncs.com/?Action=DescribeEipAddresses
&RegionId=cn-hangzhou
&CommonParameters

```

 **Response example** 

-   XML format

    ``` {#codeblock_c56_51s_nr7}
    <DescribeEipAddressesResponse>
      <RequestId>7EEF2D6B-D207-4197-AE37-01279C888757</RequestId>
      <PageNumber>1</PageNumber>
      <EipAddresses>
        <EipAddress>
          <ChargeType>PostPaid</ChargeType>
          <AllocationTime>2018-01-15T11:17:30Z</AllocationTime>
          <ResourceGroupId>rg-acfmxazxxxxxxxxx</ResourceGroupId>
          <InstanceId/>
          <Description/>
          <IpAddress>59.110.xx.xx</IpAddress>
          <AllocationId>eip-2ze88m67qx5zxxxxx</AllocationId>
          <InternetChargeType>PayByTraffic</InternetChargeType>
          <InstanceType/>
          <Name/>
          <Status>Available</Status>
          <BandwidthPackageId/>
          <InstanceRegionId/>
          <BandwidthPackageType/>
          <RegionId>cn-beijing</RegionId>
          <OperationLocks/>
          <ExpiredTime/>
          <AvailableRegions>
            <AvailableRegion>cn-beijing</AvailableRegion>
          </AvailableRegions>
          <Bandwidth>1</Bandwidth>
        </EipAddress>
      </EipAddresses>
      <TotalCount>1</TotalCount>
      <PageSize>10</PageSize>
    </DescribeEipAddressesResponse>
    
    ```

    `JSON` format

    ``` {#codeblock_g39_45l_4un}
    {
    	"DescribeEipAddressesResponse":{
    		"PageNumber":"1",
    		"EipAddresses":{
    			"EipAddress":{
    				"ChargeType":"PostPaid",
    				"Status":"Available",
    				"RegionId":"cn-beijing",
    				"ResourceGroupId":"rg-acfmxazxxxxxxxx",
    				"AllocationTime":"2018-01-15T11:17:30Z",
    				"IpAddress":"59.110.xx.xx",
    				"AllocationId":"eip-2ze88m67qx5zxxxxx",
    				"AvailableRegions":{
    					"AvailableRegion":"cn-beijing"
    				},
    				"InternetChargeType":"PayByTraffic",
    				"Bandwidth":"1"
    			}
    		},
    		"TotalCount":"1",
    		"PageSize":"10",
    		"RequestId":"7EEF2D6B-D207-4197-AE37-01279C888757"
    	}
    }
    ```


## Error codes {#section_fzy_lrr_5gb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|Forbidden.RegionNotFound|Specified region is not found during access authentication.|The specified region does not exist.|
|404|InvalidFilterKey.NotFound| |The specified key in the key/value pair of the filter is invalid.|
|404|InvalidFilterValue| |The specified value in the key/value pair of the filter is invalid.|
|404|InvalidLockReason.NotFound|The specified LockReason is not found|The reason that the EIP is locked was not found.|
|400|InvalidIAssociatedInstanceType.ValueNotSupported|The specified value of AssociatedInstanceType is not supported.|The specified AssociatedInstanceType value is invalid.|
|400|InvalidChargeType.ValueNotSupported|The specified ChargeType is not supported.|This billing method is not supported.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)


# DescribeRouterInterfaces {#reference_i4w_x11mt_ndb .reference}

Queries one or more router interfaces in a region.

You can filter the results using the following filters. The relationship between the values of a filter is “or”.  A router interface is returned so long as one filter is met. The relationship between filters is “and”. A router interface is returned only all the filters are met.

-   **RouterInterfaceId**: The ID of the router interface.
-   **RouterId**: The ID of the router.
-   **RouterType**: The type of the router. Valid values: **VRouter| VBR**.
-   **RouterInterfaceOwnerId**: The ID of the account to which the router interface belongs.
-   **OppositeInterfaceId**: The ID of the peer router interface.
-   **OppositeRouterType**: The type of the peer router interface. Valid values:**VRouter | VBR**.
-   **OppositeRouterId**: The ID of the peer router interface.
-   **OppositeInterfaceOwnerId**: The ID of the account to which the peer router interface belongs.
-   **Status**: The status of the router interface.
-   **Name** : The name of the router interface.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|DescribeRouterInterfaces| The value of this action. Value: 

 DescribeRouterInterfaces

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which one or more router interfaces belongs.

 To query the region ID, call DescribeRegions.

 |
|Filter.n.Key|String|No|Filter.1.status| Filter keys. Up to five filters are supported. Value range of n: 1 to 5.

 |
|Filter.n.Value.m|String|No|Filter.1.Active| The corresponding value of the specified filter key. Value range of m: 1 to 5.

 |
|IncludeReservationData|Boolean|No|false| Indicates whether renewal data is included.

 |
|PageNumber|Integer|No|0|  The number of pages to return. Default value: 1.

 |
|PageSize|Integer|No|10| The number of entries per page. Maximum value: 50. Default value: 10.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|TotalCount|Integer|10| The number of queried entries.

 |
|PageNumber|Integer|10| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RequestId|String|C7F6FCBD-F9CC-4501-8EF3-CDC9577CAE45| The ID of the request.

 |
|RouterInterfaceSet|N/A|N/A| A list of router interfaces.

 |
|└AccessPointId|String|ap-cn-shanghaiSZ-pd-A| The ID of the access point.

 |
|└Bandwidth|Integer|10| The bandwidth of the router interface.

 |
|└BusinessStatus|String|Normal| The business status of the router interface.

 -   **Normal**: normal
-   **FinancialLocked**: locked because the router interface is overdue
-   **SecurityLocked**: locked for security protection

 |
|└ChargeType|String|PayByTraffic| The payment method.

 |
|└ConnectedTime|String|2017-06-08T12:20:55| The time at which the connection was established.

 |
|└CreationTime|String|2017-06-08T12:20:55| The time at which the route table was created.

 |
|└CrossBorder|Boolean|false| Indicates whether the connection is a cross-border connection.

 |
|└Description|String|This is my router interface.| The description of the router interface.

 |
|└EndTime|String|2017-06-08T12:20:55| The end time of data obtaining.

 |
|└HasReservationData|String|false| Whether renewal data is obtained.

 |
|└HealthCheckSourceIp|String|116.62.222.28| The source IP of health check.

 |
|└HealthCheckTargetIp|String|116.62.222.28| The target IP of health check.

 |
|└Name|String|test| The name of the router interface.

 |
|└OppositeAccessPointId|String|ap-cn-shanghaiSZ-pd-A| The ID of the peer access point.

 |
|└OppositeBandwidth|Integer|12| The bandwidth of the peer router interface.

 |
|└OppositeInterfaceBusinessStatus|String|Normal| The business status of the peer router interface.

 |
|└OppositeInterfaceId|String|ri-bp1itx13bwe6f2wfh3qpj| The ID of the peer router interface.

 |
|└OppositeInterfaceOwnerId|String|1231579085529123| The ID of account to which the peer router interface belongs.

 |
|└OppositeInterfaceSpec|String|Large| The specification of the peer router interface.

 |
|└OppositeInterfaceStatus|String|Normal| The status of the peer router interface.

 |
|└OppositeRegionId|String|cn-shanghai| The region where the peer router interface is located.

 |
|└OppositeRouterId|String|vrt-bp1d3bxtdv68tfd7gfjkd| The ID of the router to which the peer router interface belongs.

 |
|└OppositeRouterType|String|VRouter| The type of the router to which the peer router interface belongs.

 |
|└OppositeVpcInstanceId|String|vpc-bp1qpo0kug3a20qqe9h7v| The ID of the VPC to which the peer router interface belongs.

 |
|└ReservationActiveTime|String|2019-03-11T16:00:00Z| The time at which the renewal takes effect.

 |
|└ReservationBandwidth|String|10| The bandwidth for the renewal.

 |
|└ReservationInternetChargeType|String|PayByBandwidth| The payment type for the renewal.

 |
|└ReservationOrderType|String|RENEWCHANGE| The order type for the renewal.

 |
|└Role|String|InitiatingSide| The role in a peering connection.

 |
|└RouterId|String|vrt-bp1d3bxtdv68tfd7gfjkd| The ID of the router to which the route entry belongs.

 |
|└RouterInterfaceId|String|ri-2zenfgfpyu3v93koa4sfo| The ID of the router interface.

 |
|└RouterType|String|VRouter| The type of the router to which the route table belongs. Valid values:

 -   VRouter: VRouter
-   VBR: VBR

 |
|└Spec|String|Large| The specification of the router interface.

 |
|└Status|String|active| The status of the router interface.

 |
|└VpcInstanceId|String|vpc-2ze3tq4uxhysg717x7o4d| The ID of the local VPC in the peering connection.

 |

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=DescribeRouterInterfaces
&RegionId= cn-hangzhou
&<CommonParameters>

```

**Response example**

-   XML format

    ``` {#xml_return_success_demo}
    <?xml version="1.0" encoding="UTF-8" ?>
    <DescribeRouterInterfacesResponse>
    	<PageNumber>1</PageNumber>
    	<TotalCount>2</TotalCount>
    	<PageSize>10</PageSize>
    	<RequestId>01818199-04F6-47F4-9ADF-7CC824CF57A4</RequestId>
    	<RouterInterfaceSet>
    		<RouterInterfaceType>
    			<ChargeType>Prepaid</ChargeType>
    			<HasReservationData>false</HasReservationData>
    			<OppositeInterfaceBusinessStatus>Normal</OppositeInterfaceBusinessStatus>
    			<RouterInterfaceId>ri-2zenfgfpyu3v93koa4sfo</RouterInterfaceId>
    			<OppositeInterfaceStatus>Deleted</OppositeInterfaceStatus>
    			<Spec>Small.5</Spec>
    			<OppositeInterfaceOwnerId>1231579085529123</OppositeInterfaceOwnerId>
    			<CrossBorder>false</CrossBorder>
    			<OppositeInterfaceSpec>Negative</OppositeInterfaceSpec>
    			<CreationTime>2017-12-27T06:34:30Z</CreationTime>
    			<RouterType>VRouter</RouterType>
    			<Status>Inactive</Status>
    			<OppositeRouterType>VRouter</OppositeRouterType>
    			<OppositeRouterId>vrt-bp1el837xkkakub7ci0tj</OppositeRouterId>
    			<OppositeInterfaceId>ri-bp1itx13bwe6f2wfh3qpj</OppositeInterfaceId>
    			<VpcInstanceId>vpc-2ze3tq4uxhysg717x7o4d</VpcInstanceId>
    			<RouterId>vrt-2zeazning6tbzkm5c0jj2</RouterId>
    			<ConnectedTime>2017-12-27T06:34:37Z</ConnectedTime>
    			<OppositeRegionId>cn-hangzhou</OppositeRegionId>
    			<BusinessStatus>Normal</BusinessStatus>
    			<Role>InitiatingSide</Role>
    			<OppositeVpcInstanceId>vpc-bp1iq3579f26c3gpkj92e</OppositeVpcInstanceId>
    			<EndTime>2018-01-27T16:00:00Z</EndTime>
    		</RouterInterfaceType>
    		<RouterInterfaceType>
    			<ChargeType>Prepaid</ChargeType>
    			<HasReservationData>false</HasReservationData>
    			<OppositeInterfaceBusinessStatus>Normal</OppositeInterfaceBusinessStatus>
    			<RouterInterfaceId>ri-2zegbp7nhj0mnwm6irnuo</RouterInterfaceId>
    			<OppositeInterfaceStatus>Deleted</OppositeInterfaceStatus>
    			<Spec>Small.1</Spec>
    			<OppositeInterfaceOwnerId>1231579085529123</OppositeInterfaceOwnerId>
    			<CrossBorder>false</CrossBorder>
    			<OppositeInterfaceSpec>Negative</OppositeInterfaceSpec>
    			<CreationTime>2017-12-27T06:31:30Z</CreationTime>
    			<RouterType>VRouter</RouterType>
    			<Status>Inactive</Status>
    			<OppositeRouterType>VRouter</OppositeRouterType>
    			<OppositeRouterId>vrt-bp1d3bxtdv68tfd7gfjkd</OppositeRouterId>
    			<OppositeInterfaceId>ri-bp12dxgw8gmoma1h506qf</OppositeInterfaceId>
    			<VpcInstanceId>vpc-2ze3tq4uxhysg717x7o4d</VpcInstanceId>
    			<RouterId>vrt-2zeazning6tbzkm5c0jj2</RouterId>
    			<ConnectedTime>2017-12-27T06:31:36Z</ConnectedTime>
    			<OppositeRegionId>cn-hangzhou</OppositeRegionId>
    			<BusinessStatus>Normal</BusinessStatus>
    			<Role>InitiatingSide</Role>
    			<OppositeVpcInstanceId>vpc-bp15k6sx6fhdz2jw4daz0</OppositeVpcInstanceId>
    			<EndTime>2018-10-27T16:00:00Z</EndTime>
    		</RouterInterfaceType>
    	</RouterInterfaceSet>
    <DescribeRouterInterfacesResponse>
    ```

-   JSON format

    ``` {#json_return_success_demo}
    {
    	"PageNumber":1,
    	"TotalCount":2,
    	"PageSize":10,
    	"RequestId":"01818199-04F6-47F4-9ADF-7CC824CF57A4",
    	"RouterInterfaceSet":{
    		"RouterInterfaceType":[
    			{
    				"ChargeType":"Prepaid",
    				"HasReservationData":false,
    				"OppositeInterfaceBusinessStatus":"Normal",
    				"RouterInterfaceId":"ri-2zenfgfpyu3v93koa4sfo",
    				"OppositeInterfaceStatus":"Deleted",
    				"Spec":"Small.5",
    				"OppositeInterfaceOwnerId":"1231579085529123",
    				"CrossBorder":false,
    				"OppositeInterfaceSpec":"Negative",
    				"CreationTime":"2017-12-27T06:34:30Z",
    				"RouterType":"VRouter",
    				"Status":"Inactive",
    				"OppositeRouterId":"vrt-bp1el837xkkakub7ci0tj",
    				"OppositeRouterType":"VRouter",
    				"OppositeInterfaceId":"ri-bp1itx13bwe6f2wfh3qpj",
    				"ConnectedTime":"2017-12-27T06:34:37Z",
    				"RouterId":"vrt-2zeazning6tbzkm5c0jj2",
    				"VpcInstanceId":"vpc-2ze3tq4uxhysg717x7o4d",
    				"BusinessStatus":"Normal",
    				"OppositeRegionId":"cn-hangzhou",
    				"Role":"InitiatingSide",
    				"EndTime":"2018-01-27T16:00:00Z",
    				"OppositeVpcInstanceId":"vpc-bp1iq3579f26c3gpkj92e"
    			},
    			{
    				"ChargeType":"Prepaid",
    				"HasReservationData":false,
    				"OppositeInterfaceBusinessStatus":"Normal",
    				"RouterInterfaceId":"ri-2zegbp7nhj0mnwm6irnuo",
    				"OppositeInterfaceStatus":"Deleted",
    				"Spec":"Small.1",
    				"OppositeInterfaceOwnerId":"1231579085529123",
    				"CrossBorder":false,
    				"OppositeInterfaceSpec":"Negative",
    				"CreationTime":"2017-12-27T06:31:30Z",
    				"RouterType":"VRouter",
    				"Status":"Inactive",
    				"OppositeRouterId":"vrt-bp1d3bxtdv68tfd7gfjkd",
    				"OppositeRouterType":"VRouter",
    				"OppositeInterfaceId":"ri-bp12dxgw8gmoma1h506qf",
    				"ConnectedTime":"2017-12-27T06:31:36Z",
    				"RouterId":"vrt-2zeazning6tbzkm5c0jj2",
    				"VpcInstanceId":"vpc-2ze3tq4uxhysg717x7o4d",
    				"BusinessStatus":"Normal",
    				"OppositeRegionId":"cn-hangzhou",
    				"Role":"InitiatingSide",
    				"EndTime":"2018-10-27T16:00:00Z",
    				"OppositeVpcInstanceId":"vpc-bp15k6sx6fhdz2jw4daz0"
    			}
    		]
    	}
    }
    ```


## Error codes {#section_m1p_srg_qgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidFilterKey.ValueNotSupported|Specified filter key is not supported: Filter.X.key|The specified filter key is not supported.|
|400|InvalidParam.NotNull|The parameter must not be null.|The parameter cannot be null.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)


# DescribeRouteTableList {#reference_o4n_ymk_qdb .reference}

Queries a route table.

## Debug {#section_ayr_qdk_pgb .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_p4n_ymk_qdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String |Yes |DescribeRouteTableList| The name of this action.  Value: 

 DescribeRouteTableList

 |
|RegionId|String|Yes|cn-hangzhou| The region ID of the VPC to which the route table belongs.

 To query the region ID, call [DescribeRegions](~~36063~~).

 |
|PageNumber|Integer|No |1| The number of pages to return. Default value: 1.

 |
|PageSize |Integer|No |12| The number of rows per page. Maximum value: 50. Default value: 10.

 |
|ResourceGroupId|String|No|rg-acfmxazb4ph6aiy| The ID of the resource group.

 |
|RouteTableId|String| No|vtb-bp145q7glnuzdvzu21pom| The ID of the route table.

 |
|RouteTableName|String|No|doctest| The name of the route table.

 |
|RouterId|String|No|vrt-bp1lhl0taikrteen80oxx| The ID of the router to which the route table belongs.

 |
|RouterType|String| No|VBR| The type of the router to which the route table belongs. Valid values:

 -   VRouter \(default\): VRouter

-   VBR: VBR


 |
|VpcId|String| No|vpc-bp15zckdt37pq72zvw3| The ID of the VRouter to which the route table belongs. The value of the RouterType parameter is set to VRouter automatically when this parameter is specified.

 |

## Response parameters {#section_fpn_ymk_qdb .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|PageNumber|Integer|12| The current page number.

 |
|PageSize|Integer|1| The number of rows per page.

 |
|RequestId|String|DC668356-BCB4-42FD-9BC3-FA2B2E04B634| The ID of the request.

 |
|RouterTableList|N/A|N/A| A list of route tables.

 |
|└CreationTime|String|2017-08-22T10:40:25Z| The time at which the route table was created. The format is **YYYY-MM-DDThh:mmZ**.

 |
|└Description|String|This is Route Table.| The description of the route table.

 |
|└ResourceGroupId|String|rg-acfmxazb4ph6aiy| The ID of the resource group.

 |
|└RouteTableId|String|vtb-bp145q7glnuzdvzu21pom| The ID of route table.

 |
|└RouteTableName|String|doctest| The name of the route table.

 |
|└RouteTableType|String|System|  

 The type of route table. Valid values:

 -   Custom: a custom route table
-   System: a system route table

 |
|└RouterId|String|vrt-bp1lhl0taikrteen80oxx| The ID of the router to which the route table belongs.

 |
|└RouterType|String|VBR|  

 The type of the router to which the route table belongs. Valid values:

 -   VRouter: VRouter
-   VBR: VBR

 |
|└Tags| | | A list of route table tags.

 |
|└VSwitchIds| |vsw-bp12mw1f8k3jgygk9bmlj| A list of VSwitches under the VPC.

 |
|└VpcId|String|vpc-bp15zckdt37pq72zvw3| The ID of the VRouter to which the route table belongs.

 The value of the **RouterType** parameter is set to **VRouter** automatically when this parameter is specified.

 |
|TotalCount|Integer|12| The number of rows per page.

 |

## Examples {#section_fqn_ymk_qdb .section}

**Request example**

```
https://vpc.aliyuncs.com/?Action=DescribeRouteTableList
&RegionId=cn-qingdao
&RouteTableName=myRouteTable
&VpcId=vpc-m5epxxxxxxxxxxxxx
&CommonParameters
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8" ? >
    <
    DescribeRouteTableListsResponse>
    	<Code>200</Code>
    	<Message>successful</Message>
    	<PageNumber>1</PageNumber>
    	<PageSize>10</PageSize>
    	<RequestId>87261511-FEB9-4BEC-85BF-70XXXXXXXXX</RequestId>
    	<RouterTableList>
    		<RouterTableListType>
    			<CreationTime>2018-08-03T08:14:54Z</CreationTime>
    			<Description>ddd</Description>
    			<RouteTableId>vtb-m5evbtbptnx2bXXXXXXXXX</RouteTableId>
    			<RouteTableName>aaa1111</RouteTableName>
    			<RouteTableType>Custom</RouteTableType>
    			<RouterId>vrt-m5egeuhgj52xgXXXXXXXXX</RouterId>
    			<RouterType>VRouter</RouterType>
    			<VSwitchIds>
    				<VSwitchId>vsw-m5e3r57pxkgijXXXXXXXXX</VSwitchId>
    			</VSwitchIds>
    			<VpcId>vpc-m5epe3ag3qXXXXXXXXX</VpcId>
    		</RouterTableListType>
    	</RouterTableList>
    	<Success>true</Success>
    	<TotalCount>1</TotalCount> 
    </DescribeRouteTableList>
    ```

-   JSON format

    ```
    {
      "code": "200",
      "message": "successful",
      "Pagenumber": 1,
      "Pagesize": 10,
      "RequestId": "87261511-FEB9-4BEC-85BF-70XXXXXXXXX",
      "RouterTableList": {
        "RouterTableListType": [
          {
            "CreationTime": "2018-08-03T08:14:54Z",
            "Description": "ddd",
            "RouteTableId": "vtb-m5evbtbptnx2bXXXXXXXXX",
            "RouteTableName": "aaa1111",
            "RouteTableType": "Custom",
            "RouterId": "vrt-m5egeuhgj52xgXXXXXXXXX",
            "routerType":"VRouter"
            "Vswitchids ":{
              "VSwitchId": [
                "vsw-m5e3r57pxkgijXXXXXXXXX"
              ]
            },
            "VpcId": "vpc-m5epe3ag3qXXXXXXXXX"
          }
        ]
      },
      "Success": true,
      "TotalCount": 1
    }
    ```


## Error codes {#section_t5d_ysb_fhb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|Forbbiden|User not authorized to operate on the specified resource.|You are not authorized to operate on this resource. Please apply for the permission and try again later.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)


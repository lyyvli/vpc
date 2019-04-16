# ModifyRouteTableAttributes {#reference_i4w_xmt_ndb .reference}

Modifies the name and description of a route table.

## Debug {#section_ayr_qdk_pgb .section}

By using [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancer), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String |Yes |ModifyRouteTableAttributes| The name of this action.  Value:

 ModifyRouteTableAttributes

 |
|RegionId|String |Yes |cn-hangzhou| The region ID of the VPC to which the route table belongs.

 To query the region ID, call DescribeRegions.

 |
|RouteTableId|String |Yes |vtb-bp145q7glnuzdvzu21pom|The ID of the route table.|
|Description|String| No|This is my route table.| The description of the route table.

 The description must be 2 to 256 characters in length. It must start with a letter, but cannot start with `http://` or `https://`.

 |
|RouteTableName|String| No|doctest| The name of the route table.

 The name must be 2 to 128 characters in length. It can contain letters, numbers, periods \(.\), underlines \(\_\), and hyphens \(-\). It must start with an English letter. The name cannot start with `http://` or `https://`.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|62172DD5-6BAC-45DF-8D44-xxxxxxxx|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

http(s)://vpc.aliyuncs.com/?Action=ModifyRouteTableAttributes
&RegionId=cn-hangzhou
&RouteTableId=vtb-bp145q7glnuzdvzu21pom
&<CommonParameters>

```

**Response example**

-   XML format

    ``` {#xml_return_success_demo}
    <ModifyRouteTableAttributesResponse>
      <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxx</RequestId>
    </ModifyRouteTableAttributesResponse>
    
    ```

-   JSON format

    ``` {#json_return_success_demo}
    {
    	"RequestId":"62172DD5-6BAC-45DF-8D44-xxxxxxxx"
    }
    ```


## Error codes {#section_p4t_jmy_pgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|Forbbiden|User not authorized to operate on the specified resource.|You are not authorized to operate this resource.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)


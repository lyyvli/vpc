# ModifyNatGatewayAttribute {#reference_i4w_xm3t_ndb .reference}

Modifies the name and description of a NAT Gateway.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ModifyNatGatewayAttribute| The name of this action. Value:

 ModifyNatGatewayAttribute

 |
|NatGatewayId|String|Yes|ngw-xxoo123| The ID of the NAT Gateway.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|Description|String|No|fortest| The description of the NAT Gateway.

 The description must be 2 to 256 characters in length. It must start with a letter. It cannot start with `http://` or `https://`.

 |
|Name|String|No|nat123| The name of the NAT Gateway.

 The name must be 2 to 128 characters in length and can contain letters, numbers, periods \(.\), underscores \(\_\), or hyphens \(-\). The name must start with a letter. It cannot start with `http://` or `https://`.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|AB5F62CF-2B60-4458-A756-42C9DFE108D1|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=ModifyNatGatewayAttribute
&NatGatewayId=ngw-xxoo123
&RegionId=cn-hangzhou
&<CommonParameters>
			
```

 **Response example** 

-   XML format

    ```
    <ModifyNatGatewayAttributeResponse>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
    </ModifyNatGatewayAttributeResponse>
    					
    ```

-   JSON format

    ```
    {
    	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3"
    }
    ```


## Error codes {#section_kqy_2qv_vgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidNatGatewayId.NotFound|The specified NatGatewayId does not exist in our records.|The specified NatGatewayId does not exist.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The name is invalid.|
|400|InvalidParameter.Description.Malformed|The specified Description is not valid.|The description is invalid.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)


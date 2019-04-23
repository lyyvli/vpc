# ModifyEipAddressAttribute {#reference_i4w_xmt_ndb .reference}

Modifies the name, description, and peak bandwidth of an EIP.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifyEipAddressAttribute), you can easily debug APIs, automatically generate SDK example codes, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ModifyEipAddressAttribute| The value of this action. Value:

 ModifyEipAddressAttribute

 |
|AllocationId|String|Yes|eip-2zeerraiwb7uj6i0d0fo3| The ID of the EIP.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region where the VPC that the route table belongs to is located.

 |
|Bandwidth|String|No|100| The peak bandwidth of the EIP. Unit: Mbps.

 |
|Description|String|No|Description| The description of the EIP.

 The description must be 2 to 256 characters in length. It must start with a letter but cannot start with `http://` or `https://`.

 |
|Name|String|No|Test123| The name of the EIP.

 The name must be 2 to 128 characters in length and can contain letters, numbers, periods \(.\), underscores \(\_\), or hyphens \(-\). The name must start with a letter. It cannot start with `http://` or `https://`.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|4EC47282-1B74-4534-BD0E-403F3EE64CAF|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

    https://vpc.aliyuncs.com/?Action=ModifyEipAddressAttribute
    &AllocationId=eip-25877c70xxxxxxxx
    &Name=eip1
    &<CommonParameters>
   
```

 **Response example** 

-   XML format

    ```
    <ModifyEipAddressAttributeResponse>
          <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
          </ModifyEipAddressAttributeResponse>
         
    ```

-   JSON format

    ```
    {
          "RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
          }
    ```


## Error codes {#section_k5n_hqk_5gb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InsufficientBalance.Eip|Your account does not have enough balance.|Your account does not have a sufficient balance. Recharge your account first.|
|404|InvalidAllocationId.NotFound|Specified allocation ID is not found|The specified public IP address does not exist.|
|400|InvalidParameter|Specified value of "Bandwidth" is not supported.|The specified bandwidth value is invalid.|
|500|InternalError|The request processing has failed due to some unknown error.|An error occurred while the request was being processed.|
|400|IncorrectEipStatus|Current elastic IP status does not support this operation.|The current status of the specified EIP address does not support this operation.|
|404|InvalidAllocationId.NotFound|Specified allocation ID is not found..|The specified public IP address does not exist.|
|400|InvalidParameter|The parameter is invalid.|The specified parameter value is invalid.|
|404|Forbidden.RegionNotFound|Specified region is not found during access authentication.|The specified region does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)


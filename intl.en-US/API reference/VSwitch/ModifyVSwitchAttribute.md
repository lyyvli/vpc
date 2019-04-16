# ModifyVSwitchAttribute {#reference_i4w_xmt_ndb .reference}

Modifies the name and description of a VSwitch.

## Debug {#section_ayr_qdk_pgb .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|ModifyVSwitchAttribute| The name of this action. Value:

 ModifyVSwitchAttribute

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the VSwitch belongs.

 |
|VSwitchId|String|Yes|vsw-25naue4gz| The ID of the VSwitch.

 |
|Description|String|No|This is my vswitch.| The description of the VSwitch.

 The description must be 2 to 256 characters in length. It must start with a letter and cannot start with `http://` or `https://`.

 |
|Ipv6CidrBlock|Integer|No|0| The IPv6 CIDR block of the VSwitch. You can customize the last eight bits of an IPv6 CIDR block. Value range: 0 to 255

 By default, the mask of an IPv6 CIDK block is 64-bit long.

 |
|VSwitchName|String|No|VSwitch-1| The name of the VSwitch.

 The name must be 2 to 128 characters in length. It can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). The name must start with a letter and cannot start with `http://` or `https://`.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|RequestId|String|C0FD0EED-F90D-4479-803D-DD623XXXXXX|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

http(s)://[Endpoint]/?VSwitchId=vsw-25naue4gz
&<CommonParameters>

```

**Response example**

-   XML format

    ``` {#xml_return_success_demo}
    <ModifyVSwitchAttributeResponse>
      <RequestId>0ED8D006-F706-4D23-88ED-E11ED28DCAC0</RequestId>
    </ModifyVSwitchAttributeResponse>
    
    ```

-   JSON format

    ``` {#json_return_success_demo}
    {
    	"RequestId":"0ED8D006-F706-4D23-88ED-E11ED28DCAC0"
    }
    ```


## Error codes {#section_kmt_qsr_pgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|The specified VSwitch does not exist.|
|400|InvalidVSwitchName.Malformed|Specified virtual switch name is not valid.|The format of the name of the specified VSwitch is invalid.|
|400|InvalidVSwitchDiscription.Malformed|Specified virtual switch description is not valid.|The description of the VSwitch is invalid.|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|The specified VSwitch does not exist.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc)


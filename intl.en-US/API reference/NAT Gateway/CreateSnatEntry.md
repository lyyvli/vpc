# CreateSnatEntry {#reference_i34w_xmt_ndb .reference}

Adds an SNAT entry to an SNAT table.

Each SNAT entry consists of a SourceVSwitchId and a SnatIp. After an SNAT entry is added, ECS instances under the specified VSwitch can access the Internet using the public IP \(SnatIp\).

Before you call this action, note the following:

-   The VSwitch specified in the SNAT entry must belong to the same VPC as the NAT Gateway.

-   Each VSwitch can only be added with one SNAT entry.

-   An SNAT entry cannot be added if there is a HaVip instance under the specified VSwitch.

-   The public IP \(SnatIp\) address in the SNAT entry must meet the following requirements:
    -   If your account has a NAT bandwidth package before January 26, 2018, the SnatIp must be a public IP address in the NAT bandwidth package of the NAT Gateway.
    -   If your account does not have a NAT bandwidth package before January 26, 2018, the SnatIp must be an EIP attached to the NAT Gateway.
    -   A public IP address cannot be used by a DNAT entry and an SNAT entry at the same time.

## Debug {#apiExplorer .section}

By using [API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpcAttribute), you can easily debug APIs, automatically generate SDK code examples, and quickly search for APIs.

## Request parameters {#section_cch_pjg_mdb .section}

|Parameter|Type|Required?|Example value|Description|
|:--------|:---|:--------|-------------|:----------|
|Action|String|Yes|CreateSnatEntry| The name of this action. Value:

 CreateSnatEntry

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the NAT Gateway belongs.

 To query the region ID, call DescribeRegions.

 |
|SnatIp|String|Yes|47.XXX.XXX.98|The public IP address. Separate multiple EIPs with commas.|
|SnatTableId|String|Yes|stb-bp190wu8io1vgevxxxxxx| The ID of the SNAT table.

 |
|SnatEntryName|String|No|SnatEntry-1| The name of the SNAT entry to be created. The name must be 2 to 128 characters in length and start with a letter or a Chinese character. The name cannot start with`http://` or `https://`.

 |
|SourceCIDR|String|No|10.1.1.0/24| The CIDR block of the VSwitch. Example value: 10.0.0.1/24.

 **Note:** This parameter and the **SourceVSwtichId** parameter cannot be used at the same time. If you have specified the **SourceVSwitchId** parameter, you cannot specify the **SourceCIDR** parameter. If you have specified the **SourceCIDR** parameter, you cannot specify the **SourceVSwitchId** parameter.

 |
|SourceVSwitchId|String|No|vsw-bp1nhx2s9ui5oxxxxxxxx| The ID of the VSwitch to access the Internet.

 |

## Response parameters {#section_ugs_f1g_cz .section}

|Parameter|Type|Example value|Description|
|:--------|:---|-------------|:----------|
|SnatEntryId|String|snat-kmd6nv8fyxxxxxxxx|The ID of the SNAT entry.|
|RequestId|String|2315DEB7-5E92-423A-91F7-4C1EC9AD97C3|The ID of the request.|

## Examples {#section_ix5_h1g_cz .section}

**Request example**

``` {#createVPCpub}

https://vpc.aliyuncs.com/?Action=CreateSnatEntry
&RegionId=cn-hangzhou
&SnatIp=47.XXX.XXX.98
&SnatTableId=stb-bp190wu8io1vgevxxxxxx
&<CommonParameters>

```

 **Response example** 

-   XML format

    ``` {#codeblock_uh3_fk7_msn}
    <CreateSnatEntryResponse>
      <RequestId>2315DEB7-5E92-423A-91F7-4C1EC9AD97C3</RequestId>
      <SnatEntryId>snat-119smw5tkxxxxxxxx</SnatEntryId>
    </CreateSnatEntryResponse>
    
    ```

-   JSON format

    ``` {#codeblock_40i_wj5_xjk}
    {
    	"RequestId":"2315DEB7-5E92-423A-91F7-4C1EC9AD97C3",
    	"SnatEntryId":"snat-kmd6nv8fyxxxxxxxx"
    }
    ```


## Error codes {#section_afy_vjc_wgb .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidRegionId.NotFound|The specified RegionId does not exist in our records.|The specified region ID does not exist.|
|404|InvalidSnatTableId.NotFound|Specified SNAT table does not exist.|The specified SNAT table does not exist.|
|400|Forbidden.SourceVSwitchId.IncludeHaVip|There is some HaVips under specified VSwitch|One or more HAVIPs are already under the specified VSwitch.|
|400|InvalidSnatIp.Malformed|The specified SnatIp is not a valid IP address.|The specified SNAT IP address is invalid.|
|400|SNAT\_IP\_POOL\_COUNT\_TOO\_MANY|The Snat pool ip too many.|The quota for IP addresses in the SNAT IP address pool has been reached.|
|400|Forbidden.SnatEntryCountLimited|SNAT entry in the specified SNAT table reach it?s limit.|The quota for SNAT entries has been reached.|
|400|NOT\_ALLOW\_USE\_SOURCECIDR|The User not in nat\_scope\_unlimited white list. Cannot use SourceCidr param.|The specified intranet IP address does not belong to the CIDR block of the VPC.|
|404|InvalidVSwitchId.NotFound|The specified virtual switch does not exists.|The specified VSwitch does not exist.|
|400|INVALID\_PARAMETER|The parameter invalid.|The parameter is invalid.|
|400|Forbidden.SourceVSwitchId.Duplicated|The specified SourceCIDRis duplicated.|An SNAT rule has already been configured for this VSwitch.|
|404|InvalidSnatIp.NotFound|Specified SnatIp does not found on the NAT Gateway|The specified public IP address cannot be found in the NAT Gateway.|
|400|Forbidden.IpUsedInForwardTable|The specified SnatIp already used in forward table|This public IP address is being used by a DNAT rule. Select a different IP address or delete the DNAT rule that uses this IP address.|
|400|Forbindden|The specified Instance already bind eip|An EIP is already associated with this ECS instance. Disassociate the EIP from the ECS instance first and then add the forwarding rule.|
|400|InvalidParameter.Name.Malformed|The specified Name is not valid.|The specified name is invalid. Enter a valid name and try again.|

[See common error codes](https://error-center.aliyun.com/status/product/Vpc).


# UnassociateRouteTable {#reference_i4w_xmt_ndb .reference}

将路由表和交换机解绑。

## 请求参数 {#section_cch_pjg_mdb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 UnassociateRouteTable

 |
|RegionId|String|是| 路由表所属的VPC的地域ID。

 您可以通过调用 DescribeRegions接口获取地域ID。

 |
|RouteTableId|String|是|路由表ID。|
|VSwitchId|String|否|要解绑的交换机ID。|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#createVPCpub}
https://vpc.aliyuncs.com/?Action=UnassociateRouteTable
&RegionId=cn-qingdao
&RouteTableId=vtb-m5evbtbptnxxxxxxx
&VSwitchId=vsw-m5e3r57pxxxxxxxxxxxxxx
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <UnassociateRouteTableResponse>
        <RequestId>62172DD5-6BAC-45DF-8D44-xxxxxxx</RequestId>
    </UnassociateRouteTableResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": "62172DD5-6BAC-45DF-8D44-xxxxxxxx"
    }
    ```



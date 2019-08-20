# ModifyRouteEntry {#doc_api_Vpc_ModifyRouteEntry .reference}

Modifies the name of a custom route entry.

## Debug {#api_explorer .section}

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Vpc&api=ModifyRouteEntry&type=RPC&version=2016-04-28)

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ModifyRouteEntry|The name of this action. Value: **ModifyRouteEntry**.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the route entry belongs.

 |
|RouteEntryId|String|Yes|rte-1234567890|The ID of the custom route entry.

 |
|RouteEntryName|String|No|EntryName|The name of the route entry.

 The name must be 2 to 128 characters in length and start with a letter or a Chinese character. The name cannot start with `http://`or `https://`.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|861E6630-AEC0-4B2D-B214-6CB5E44B7F04|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=ModifyRouteEntry
&RegionId=cn-hangzhou
&RouteEntryId=rte-1234567890
&<CommonParameters>

```

Response example

`XML` format

``` {#xml_return_success_demo}
<ModifyRouteEntryResponse>
    <RequestId>861E6630-AEC0-4B2D-B214-6CB5E44B7F04</RequestId>
</ModifyRouteEntryResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"861E6630-AEC0-4B2D-B214-6CB5E44B7F04"
}
```

## Errors { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|403|Forbidden|User not authorized to operate on the specified resource.|You are not authorized to use this resource.|


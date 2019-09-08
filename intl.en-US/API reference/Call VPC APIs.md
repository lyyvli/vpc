# Call VPC APIs {#concept_jyw_13k_qdb .concept}

When you call a VPC API, an HTTP GET request is sent to the API service address of VPC, and the system responds according to the parameters set in the request. Both the request and the response are UTF-8-encoded.

## Request syntax {#section_mqj_q3f_mdb .section}

VPC APIs use RPC style. You can call VPC APIs by sending HTTP GET requests.

The request syntax is as follows:

``` {#codeblock_zf2_xac_wgv}
http://Endpoint/?Action=xx&Parameters
```

where,

-   Endpoint: The endpoint of VPC APIs is `vpc.aliyuncs.com`.
-   Action: the name of the action. For example, if you need to query one or more VPCs, the action is DescribeVpcs.
-   Version: the version of the API. The version of VPC APIs is 2016-04-28.
-   Parameters: the request parameters. Separate multiple parameters by using ampersands \(&\).

    Request parameters include common parameters and API-specific parameters. Common parameters include API version and identity authentication information among other parameters. For more information, see [Common parameters](reseller.en-US/API reference/Common parameters.md#).


The following is an example of calling DescribeVpcs to query one or more VPCs.

**Note:** The following code has been edited to ease readability.

``` {#codeblock_4gl_88h_ahb}
https://vpc.aliyuncs.com/?Action=DescribeVpcs
&Format=xml
&Version=2014-05-15
&Signature=xxxx%xxxx%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&Timestamp=2012-06-01T12:00:00Z
…
```

## API authorization {#section_mlp_qmf_mdb .section}

To maintain account security, we recommend that you use the Access Keys \(AKs\) of RAM users to call APIs. Before you use the AKs of RAM users to call APIs, you must grant permissions to the RAM users by attaching corresponding policies to them.

For a list of VPC resources and interfaces that can be authorized, see [RAM authentication](reseller.en-US/API reference/RAM authentication.md#).

## API signature {#section_jtc_ymf_mdb .section}

Authentication is required by the VPC service for each API call, which is provided by the inclusion of signature information in the request.

VPC uses an AccessKeyID and AccessKeySecret pair \(that is, an AK\) and symmetric encryption to authenticate the identity of the request sender. AKs are certificates that Alibaba Cloud issues to Alibaba Cloud accounts and RAM users for authentication. It is similar to a logon password. The AccessKeyID is used to identify the visitor's identity. The AccessKeySecret is the key used to encrypt the signature string. The server uses the AccessKeySecret to decrypt the signature string. The AccessKeySecret must be kept confidential.

For an RPC API, you must add the signature to the API request in the following format:

`https://endpoint/?SignatureVersion=*1.0*&SignatureMethod=*HMAC-SHA1*&Signature=*xxxx%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf*`

Take the API call of DescribeVpcs as an example. If your AccessKeyID is `testid`, and your AccessKeySecret is `testsecret`, then, the URL in the signature is as follows:

``` {#codeblock_0v6_230_tp7}
http://vpc.aliyuncs.com/?Action=DescribeVpcs
&Timestamp=2016-02-23T12:46:24Z
&Format=XML
&AccessKeyId=testid
&SignatureMethod=HMAC-SHA1
&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
&Version=2014-05-26
&SignatureVersion=1.0
```

To generate the signature, follow these steps:

1.  Create the string to be signed by using the request parameter.

    ``` {#codeblock_uzw_r0c_jwi}
    GET&%2F&AccessKeyId%3Dtestid&Action%3DDescribeVpcs&Format%3DXML&SignatureMethod%3DHMAC-SHA1&SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf&SignatureVersion%3D1.0&TimeStamp%3D2016-02-23T12%253A46%253A24Z&Version%3D2014-05-15
    ```

    .

2.  Calculate the HMAC value of the string.

    Add an ampersand \(&\) after the AccessKeySecret to add the key of the HMAC value. In this example, the key is `testsecret&`.

    ``` {#codeblock_36o_lt1_t7s}
    CT9X0VtwR86fNWS********juE=
    ```

3.  Add the signature to the request parameter.

    ``` {#codeblock_lbu_wt0_o8t}
    http://vpc.aliyuncs.com/?Action=DescribeVpcs
    &Timestamp=2016-02-23T12:46:24Z
    &Format=XML
    &AccessKeyId=testid
    &SignatureMethod=HMAC-SHA1
    &SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
    &Version=2014-05-26
    &SignatureVersion=1.0
    &Signature=xxxx%3D
    ```



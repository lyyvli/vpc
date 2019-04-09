# Call VPC APIs {#concept_jyw_13k_qdb .concept}

When a VPC API is called, an HTTP GET request is sent to the endpoint of VPC APIs. You must add corresponding request parameters in the request according to the API description. After the calling, the system returns the handling result. The request and response results are encoded using the UTF-8 character set.

## Request structure {#section_mqj_q3f_mdb .section}

VPC APIs belong to the RPC type. You can call VPC APIs by sending HTTP GET requests.

The request structure is as follows:

```
http://Endpoint/?Action=xx&Parameters
```

Where:

-   Endpoint: The endpoint of VPC APIs is `vpc.aliyuncs.com`.
-   Action: The action to perform. For example, call DescribeVpcs to query all the created VPCs.
-   Version: The version of the API to use. The current VPC API version is 2016-04-28.
-   Parameters: Request parameters. Use “&” to separate multiple parameters.

    Request parameters consist of common parameters and API specific parameters. Common parameters include VPI version, credentials, and so on.


The following is an example using the DescribeVpcs API to query the created VPCs:

**Note:** To make it easy to read, the API request is displayed in the following format:

```
https://vpc.aliyuncs.com/?Action=DescribeVpcs
&Format=xml
&Version=2014-05-15
&Signature=xxxx%xxxx%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&Timestamp=2012-06-01T12:00:00Z
...
```

## API authorization {#section_mlp_qmf_mdb .section}

For the security of your account, we recommend that you use a RAM user to call APIs. Before using a RAM user to call an API, you must grant the RAM user the corresponding permission to call the API by creating an authorization policy and attaching the policy to the RAM user.

For more information, see [RAM authentication](reseller.en-US/API reference/RAM authentication.md#).

## API signature {#section_jtc_ymf_mdb .section}

To ensure the security of your API, you must sign the API request. Alibaba Cloud uses the signature in the request to verify the identity of the person who calls the API.

VPC uses AccessKey ID and AccessKey Secret for symmetrical encryption to verify the identity of the requester. AccessKey is an identity credential issued to Alibaba Cloud accounts and the RAM users \(similar to the login password\). The AccessKey ID is used to verify the identity of the user, and the AccessKey Secret is used to encrypt the signature string and is also the key used by the server to verify the signature string. The AccessKey Secret must be kept strictly confidential.

For an RPC API, you must add the signature to the API request in the following format:

`https://endpoint/?SignatureVersion=*1.0*&SignatureMethod=*HMAC-SHA1*&Signature=*CT9X0VtwR86fNWSnsc6v8YGOjuE%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf*`

Take the DescribeVpcs API as an example. If the AccessKey ID is `testid`, and the AccessKey Secret is `testsecret`, the original request URL is as follows:

```
http://vpc.aliyuncs.com/?Action=DescribeVpcs
&Timestamp=2016-02-23T12:46:24Z
&Format=XML
&AccessKeyId=testid
&SignatureMethod=HMAC-SHA1
&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
&Version=2014-05-26
&SignatureVersion=1.0
```

Follow these steps to calculate the signature:

1.  Use the request parameters to create a canonicalized query string to sign.

    ```
    GET&%2F&AccessKeyId%3Dtestid&Action%3DDescribeVpcs&Format%3DXML&SignatureMethod%3DHMAC-SHA1&SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf&SignatureVersion%3D1.0&TimeStamp%3D2016-02-23T12%253A46%253A24Z&Version%3D2014-05-15
    ```

    .

2.  Calculate the HMAC value of the string to sign.

    Append an ampersand \(&\) to the AccessKey Secret to use the new string as the key to compute the HMAC. In this example, the key is `testsecret&amp;`.

    ```
    CT9X0VtwR86fNWSnsc6v8YGOjuE=
    ```

3.  Add the signature to the request parameters:

    ```
    http://vpc.aliyuncs.com/?Action=DescribeVpcs
    &Timestamp=2016-02-23T12:46:24Z
    &Format=XML
    &AccessKeyId=testid
    &SignatureMethod=HMAC-SHA1
    &SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
    &Version=2014-05-26
    &SignatureVersion=1.0
    &Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D
    ```



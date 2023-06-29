---
title: "cloudPC: validateBulkResize"
description: "Validate that a set of Cloud PC devices meet the requirements to be bulk resized."
author: "SleepIsImportant"
ms.localizationpriority: medium
ms.prod: "cloud-pc"
doc_type: apiPageType
---

# cloudPC: validateBulkResize

Namespace: microsoft.graph

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Validate that a set of [cloudPC](../resources/cloudpc.md) devices meet the requirements to be bulk resized.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type|Permissions (from least to most privileged)|
|:---|:---|
|Delegated (work or school account)|CloudPC.ReadWrite.All|
|Delegated (personal Microsoft account)|Not supported.|
|Application|CloudPC.ReadWrite.All|

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->

``` http
POST /deviceManagement/virtualEndpoint/cloudPCs/validateBulkResize
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|
|Content-Type|application/json. Required.|

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

|Property|Type|Description|
|:---|:---|:---|
|cloudPcIds|String collection|The selected Cloud PC id list to be validated. The max count is 2000.|
|targetServicePlanId|String|The target service plan id of the resize configuration with the new vCPU and storage size.|

## Response

If successful, this method returns a `200 OK` response code and the requested [cloudPcResizeValidateResult](../resources/cloudpcresizevalidationresult.md) object collection in the response body.

## Examples

### Request

The following is an example of a request.

<!-- {
  "blockType": "request",
  "name": "cloudpc.validatebulkresize"
}
-->

``` http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPCs/validateBulkResize
Content-Type: application/json

{
  "cloudPcIds": [
    "30d0e128-de93-41dc-89ec-33d84bb662a0", 
    "7c82a3e3-9459-44e4-94d9-b92f93bf78dd"
  ],
  "targetServicePlanId": "662009bc-7732-4f6f-8726-25883518b33e"
}
```

### Response

The following is an example of the response.

<!-- {
  "blockType": "response",
  "@odata.type": "Collection(microsoft.graph.cloudPcResizeValidationResult)",
  "truncated": true
}
-->

``` http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "value": [
        {
            "@odata.type": "#microsoft.graph.cloudPcResizeValidationResult",
            "cloudPcId": "30d0e128-de93-41dc-89ec-33d84bb662a0",
            "validationResult": "success"
        },
        {
            "@odata.type": "#microsoft.graph.cloudPcResizeValidationResult",
            "cloudPcId": "7c82a3e3-9459-44e4-94d9-b92f93bf78dd",
            "validationResult": "operationNotSupported"
        }
    ]
}
```

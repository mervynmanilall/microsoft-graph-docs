---
title: "List cookies"
description: "Get a list of hostCookie resources."
author: "joerattazzi-microsoft"
ms.localizationpriority: medium
ms.prod: "security"
doc_type: apiPageType
---

# List cookies

Namespace: microsoft.graph.security

[!INCLUDE [threatintelligence-api-disclaimer](../../includes/threatintelligence-api-disclaimer.md)]

Get a list of [hostCookie](../resources/security-hostcookie.md) resources.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

| Permission type                        | Permissions (from least to most privileged) |
| :------------------------------------- | :------------------------------------------ |
| Delegated (work or school account)     | ThreatIntelligence.Read.All                 |
| Delegated (personal Microsoft account) | Not supported.                              |
| Application                            | ThreatIntelligence.Read.All                 |

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->

```http
GET /security/threatIntelligence/hosts/{hostId}/cookies
```

## Optional query parameters

This method supports the `$count`, `$select`, `$top`, and `$skip` OData query parameters to help customize the response. For general information, see [OData query parameters](/graph/query-parameters).

## Request headers

| Name          | Description               |
| :------------ | :------------------------ |
| Authorization | Bearer {token}. Required. |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.security.hostCookie](../resources/security-hostcookie.md) objects in the response body.

## Examples

### Request

The following is an example of a request.

<!-- {
  "blockType": "request",
  "name": "list_hostcookie",
  "sampleKeys": ["contoso.com"]
}
-->

```http
GET https://graph.microsoft.com/v1.0/security/threatIntelligence/hosts/contoso.com/cookies
```

### Response

The following is an example of the response.

> **Note:** The response object shown here might be shortened for readability.

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "Collection(microsoft.graph.security.hostCookie)"
}
-->

```json
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.security.hostCookie",
      "id": "c2VjdXJlbWFpbC5jb250b3NvLmNvbSQkT0lEQyQkc2VjdXJlbWFpbC5jb250b3NvLmNvbQ==",
      "firstSeenDateTime": "2022-02-26T07:23:34.558Z",
      "lastSeenDateTime": "2023-02-28T04:57:15.288Z",
      "domain": "securemail.contoso.com",
      "name": "OIDC",
      "host": {
          "id": "securemail.contoso.com"
      }
    }
  ]
}
```

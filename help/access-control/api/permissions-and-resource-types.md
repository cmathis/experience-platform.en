---
keywords: Experience Platform;home;popular topics
solution: Experience Platform
title: List names of permissions and resource types
topic: developer guide
---

# List names of permissions and resource types

You can list the names of all permissions and resource types by making a GET request to the `/acl/reference` endpoint. These names can then be used in API calls to [view effective policies](./effective-policies.md) for the current user.

A **permission** is a policy that is managed through the Adobe Admin Console, and maps to zero or more resource-type policies. A **resource type** is a policy that enables read, write, and/or delete capabilities for a specific type of Platform resource (such as datasets or schemas).

**API format**

```http
GET /acl/reference
```

**Request**

```shell
curl -X GET \
  https://platform.adobe.io/data/foundation/access-control/acl/reference \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}'
```

**Response**

A successful response returns a `permissions` object and a `resource-types` object, each containing a full list of names for access permissions or resource types, respectively.

```json
{
  "permissions": {
    "export-audience-for-segment": {
      "segments": [
        "read"
      ]
    },
    "manage-datasets": {
      "connection": [
        "read",
        "write",
        "delete"
      ],
      "datasets": [
        "read",
        "write",
        "delete"
      ]
    }
    {"..."}
  },
  "resource-types": {
    "classes": [
      "read",
      "write",
      "delete"
    ],
    "connection": [
      "read",
      "write",
      "delete"
    ],
    "data-types": [
      "read",
      "write",
      "delete"
    ],
    "...": [
      "..."
    ]
  }
}
```

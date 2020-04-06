---
keywords: Experience Platform;home;popular topics
solution: Experience Platform
title: Delete an object
topic: developer guide
---

# Delete an object

You can delete a Catalog object by providing its ID in the path of a DELETE request. 

>[!WARNING] Take extra care when deleting objects, as this cannot be undone and may produce breaking changes elsewhere in Experience Platform.

**API format**

```http
DELETE /{OBJECT_TYPE}/{OBJECT_ID}
```

| Parameter | Description |
| --- | --- |
| `{OBJECT_TYPE}` | The type of Catalog object to be deleted. Valid objects are: <ul><li>`accounts`</li><li>`batches`</li><li>`connections`</li><li>`dataSets`</li><li>`dataSetFiles`</li><li>`dataSetViews`</li></ul> |
| `{OBJECT_ID}` | The identifier of the specific object you want to update. |

**Request**

The following request deletes a dataset whose ID is specified in the request path.

```shell
curl -X DELETE \
  'https://platform.adobe.io/data/foundation/catalog/dataSets/5ba9452f7de80400007fc52a' \
  -H 'Authorization: Bearer {ACCESS_TOKEN}' \
  -H 'x-api-key: {API_KEY}' \
  -H 'x-gw-ims-org-id: {IMS_ORG}' \
  -H 'x-sandbox-name: {SANDBOX_NAME}'
```

**Response**

A successful response returns HTTP status 200 (OK) and an array containing the ID of the deleted dataset. This ID should match the one sent in the DELETE request. Performing a GET request on the deleted object returns HTTP status 404 (Not Found), confirming that the dataset has been deleted successfully.

```json
[
    "@/dataSets/5ba9452f7de80400007fc52a"
]
```

>[!NOTE] If no Catalog objects match the ID provided in your request, you may still receive an HTTP Status Code 200, but the response array will be empty.
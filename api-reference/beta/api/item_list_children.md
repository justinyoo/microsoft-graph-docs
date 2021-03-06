# List children

Items with the folder resource may contain one or more child items. This API
lists the contents of a drive or item's `children` collection using either the root folder, item ID or path.

### Prerequisites
One of the following **scopes** is required to execute this API: 

  * Files.Read

### HTTP request
```http
GET /drive/root/children
GET /drive/items/{item-id}/children
GET /drive/root:/{item-path}:/children
```

### Optional query parameters
This method supports the [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.

### Request headers

| Name     | Type | Description        |
|:----------------|:------|:--------------------------------------------|
| if-none-match | String  | If this request header is included and the eTag (or cTag) provided matches the current tag on the file, an `HTTP 304 Not Modified` response is returned. |
| Authorization  | string  | Bearer <token>. Required. |


### Request body
Do not supply a request body for this method.

### Example
Here is an example of how to call this API.
##### Request
Here is an example of the request.

<!-- {
  "blockType": "request",
  "name": "get_children"
}-->
```http
GET /drive/root/children
```

### Response

Here is an example of the response.
<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.item",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {"name": "myfile.jpg", "size": 2048, "file": {} },
    {"name": "Documents", "folder": { "childCount": 4} },
    {"name": "Photos", "folder": { "childCount": 203} },
    {"name": "my sheet(1).xlsx", "size": 197 }
  ],
  "@odata.nextLink": "https://..."
}
```

**Note:** If a collection exceeds the default page size (200 items), the **@odata.nextLink** property is returned in the response to indicate more items are available and provide the request URL for the next page of items. You can control the page size through
[optional query string parameters](https://dev.onedrive.com/odata/optional-query-parameters.htm).
For more info, see [List children for a OneDrive item](https://dev.onedrive.com/items/list.htm).

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "List the children of an item.",
  "keywords": "list,children,collection",
  "section": "documentation",
  "tocPath": "Items/List Children"
} -->

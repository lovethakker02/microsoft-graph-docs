# Create TableRow

Adds rows to the end of the table. Note that the API can accept multiple rows data using this API. Adding one row at a time could lead to performance degradation. The recommended approach would be to batch the rows together in a single call rather than doing single row insertion. For best results, collect the rows to be inserted on the application side and perform single rows add operation. Experiment with the number of rows to determine the ideal number of rows to use in single API call. 

## Error Handling

This request might occasionally receive a 504 HTTP error. The appropriate response to this error is to repeat the request.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](../../../concepts/permissions_reference.md).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Files.ReadWrite    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Not supported. |

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/tables/{id|name}/rows/add
POST /workbook/worksheets/{id|name}/tables/{id|name}/rows/add

```
## Request headers
| Name       | Description|
|:---------------|:----------|
| Authorization  | Bearer {token}. Required. |
| Workbook-Session-Id  | Workbook session Id that determines if changes are persisted or not. Optional.|

## Request body
In the request body, provide a JSON object with the following parameters.

| Parameter	   | Type	|Description|
|:---------------|:--------|:----------|
|index|number|Optional. Specifies the relative position of the new row. If null, the addition happens at the end. Any rows below the inserted row are shifted downwards. Zero-indexed.|
|values|Json|A 2-dimensional array of unformatted values of the table rows (boolean or string or number).|

## Response

If successful, this method returns `200 OK` response code and [TableRow](../resources/tablerow.md) object in the response body.

## Example
In this example two rows of data are inserted at the end of the table. 

##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "tablerowcollection_add"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/tables/{id|name}/rows/add
Content-type: application/json
Content-length: 51

{
  "values": [
    [1, 2, 3],
    [4, 5, 6]
  ]
}
```
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.workbookTableRow"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 45

{
  "index": 99,
  "values": "values-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "TableRowCollection: add",
  "keywords": "",
  "section": "documentation",
  "suppressions": [
    "Error: /api-reference/v1.0/api/table_post_rows.md/tablerowcollection_add/values:
      Type mismatch between example and table. Parameter name: values; example type (Collection(Collection)) is a collection, while the table description type (microsoft.graph.Json) is not.",
    "Warning: /api-reference/v1.0/api/table_post_rows.md/tablerowcollection_add/values:
      Inconsistent types between parameter (Collection) and table (None)"
  ],
  "tocPath": ""
}-->
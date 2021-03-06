# Create subscription

Subscribes a listener application to receive notifications when mail, calendar events, or contacts change.
### Prerequisites
One of the following **scopes**, depending on the target resource, are required to execute this API: *Mail.Read*, *Calendars.Read*, or *Contacts.Read* 
### HTTP request
<!-- { "blockType": "ignored" } -->

```http
POST /subscriptions

```
### Optional query parameters
This method supports the [OData Query Parameters](http://graph.microsoft.io/docs/overview/query_parameters) to help customize the response.

### Request headers
| Name       | Type | Description|
|:-----------|:------|:----------|
| Authorization  | string  | Bearer <token>. Required. |


### Response
If successful, this method returns `201, Created` response code and [subscription](../resources/subscription.md) object in the response body.

### Example
##### Request
Here is an example of the request.
<!-- {
  "blockType": "request",
  "name": "create_subscription_from_subscriptions"
}-->
```http
POST https://graph.microsoft.com/beta/subscriptions
Content-type: application/json
Content-length: 208

{
   "changeType": "Created",
   "notificationUrl": "https://webhook.azurewebsites.net/api/send/myNotifyClient",
   "clientState": "subscription-identifier",  
   "resource": "me/messages"
}
```
In the request body, supply a JSON representation of [subscription](../resources/subscription.md) object.
##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.subscription"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 252

{
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#subscriptions/$entity",
  "subscriptionId":"7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource":"me/messages",
  "changeType":"Created",
  "clientState":"subscription-identifier",
  "notificationUrl":"https://webhook.azurewebsites.net/api/send/myNotifyClient",
  "subscriptionExpirationDateTime":"2015-11-20T18:23:45.9356913Z"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create subscription",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
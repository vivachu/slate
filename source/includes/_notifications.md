# Notifications

## Set Firebase token

```shell
curl "http://api.parade.pet/user/setFirebaseToken/<token>"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns “OK” or an error message

```
  "OK"
```

This endpoint is used to set the authenticated user's Firebase token.

### HTTP Request

`POST http://api.parade.pet/user/setFirebaseToken/<token>`
  
### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
token | true |  Firebase token string, included as part of url


<aside class="success">
Sets the authenticated user's firebaseToken field to the POSTed Firebase token.  Returns "OK" if successful.
</aside>
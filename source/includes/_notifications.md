# Notifications

## Set Firebase token

```shell
curl "http://api.parade.pet/user/setFirebaseToken"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'token=jkh3kjh32kj32kj3'
```

> The above command returns “OK” or an error message

```
  "OK"
```

This endpoint is used to set the authenticated user's Firebase token.

### HTTP Request

`POST http://api.parade.pet/user/setFirebaseToken`
  
### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
token | true |  Firebase token string


<aside class="success">
Sets the authenticated user's firebaseToken field to the POSTed Firebase token.  Returns "OK" if successful.
</aside>
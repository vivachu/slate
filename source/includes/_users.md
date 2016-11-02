# Users

## Sign up With Email

```shell
curl "http://localhost:1337/user/create"
  -d 'email=janice@parade.pet'
  -d 'password=p3tp@rad3!'
  -d 'confirmPassword=p3tp@rad3!'
  -d 'firstName=Janice'
  -d 'lastName=Lu'
```

> The above command returns JSON structured like this:

```json
{
  "user": {
    "location": 6,
    "firstName": "Janice",
    "lastName": "Lu",
    "email": "janice@parade.pet",
    "silverCoins": 0,
    "goldCoins": 0,
    "id": 1,
    "fullName": "Janice Lu",
    "profileImage": 1232
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzaWQiOjE1MDI3LCJpYXQiOjE0Njk4MTIzMTh9.vul5bXtU69sKPUQG4-taH5YGeHbRQ4BPBYQpq-QA5ZU"
}
```

This endpoint creates the new user, logs the user in, and returns an authorization token.  If this email already exists in the database, or the password does not match the confirmPassword, an error message is returned.   

### HTTP Request

`POST http://api.parade.pet/user/create`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | The user's email address.  This is the user's unique username.
password | true | The unencrypted password.
confirmPassword | true | The unencrypted password
firstName | true | The user's first name
lastName | true | The user's last name

<aside class="success">
The user object and the user's authentication token is returned.
</aside>

## Set Firebase Token

```shell
curl "http://api.parade.pet/user/setFirebaseToken/<token>"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns “OK” or an error message

```
  "OK"
```

This endpoint is used to set the authenticated user's Firebase Token.

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

## Block User

```shell
curl "http://api.parade.pet/user/block"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'userToBlock=8372'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint reports an entry that the user finds questionable.

### HTTP Request

`POST http://api.parade.pet/user/block`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userToBlock | true | The ID of the user to block   

<aside class="success">
Returns OK
</aside>

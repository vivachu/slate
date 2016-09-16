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
    "email": "janice@parade.pet",
    "firstName": "Janice",
    "lastName": "Lu",
    "silverCoins": 0,
    "goldCoins": 0,
    "registerStep": 1,
    "faceOffType": 1,
    "createdAt": "2016-07-29T17:11:58.788Z",
    "updatedAt": "2016-07-29T17:11:58.788Z",
    "id": 1,
    "fullName": "Janice Lu",
    "profileThumb": "https://assets.parade.pet/images/default-user-thumb.png",
    "profileMedium": "https://assets.parade.pet/images/default-user-med.png",
    "profileLarge": "https://assets.parade.pet/images/default-user-large.png"
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

## Validate Social Tokens

```shell
curl "http://api.parade.pet/user/validateSocialTokens"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this: 

```
{
    "facebook": true,
    "twitter": false,
    "google": true,
    "instagram": false
}
```

This endpoint validates the user's saved authentication tokens with each respective social network and returns true or false to indicate whether the server has a valid auth token saved for each respective social network.  

### HTTP Request

`GET http://api.parade.pet/user/validateSocialTokens
  
### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns true or false for each social network. Note that false will be returned if a social network's token has expired or does not possess access rights to post on the user's behalf.  
</aside>

## Set Social Tokens

```shell
curl "http://api.parade.pet/user/setSocialTokens"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns “OK” or an error message

```
  "OK"
```

This endpoint is used to save the authenticated user's Facebook, Twitter, Google and Instagram Tokens and user id's.

### HTTP Request

`POST http://api.parade.pet/user/setSocialTokens/`
  
### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
facebookToken | false |  Facebook token string
twitterToken | false |  Twitter token string
googleToken | false |  Google token string
instagramToken | false |  Instagram token string

<aside class="success">
Sets the authenticated user's social token fields to the POSTed tokens.  Returns "OK" if successful.  Note this call does NOT validate the tokens; see validateSocialTokens.
</aside>
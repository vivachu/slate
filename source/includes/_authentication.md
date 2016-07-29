# Authentication

> To authorize, use this code:

```shell
# With shell, pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization:  Bearer meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your user's API token.

The Pet Parade API contains both public and private API endpoints.  Private API endpoints require an authorization token to be passed to the server in a header string that looks like the following:

`Authorization: Bearer meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your user's API token.  
</aside>
API tokens are specific to each Pet Parade user account.  To get a new token, you must first call the <code>/auth/login</code> or <code>/auth/loginWithFacebook</code> or endpoint.  

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

## Login With Email

```shell
curl "http://localhost:1337/auth/login"
  -d 'email=janice@parade.pet'
  -d 'password=p3tp@rad3!'
```

> The above command returns JSON structured like this:

```json
{
  "user": {
    "location": 6,
    "firstName": "Janice",
    "lastName": "Lu",
    "email": "janice@parade.pet",
    "facebookId": null,
    "facebookToken": null,
    "silverCoins": 0,
    "goldCoins": 0,
    "id": 1,
    "createdAt": "2016-06-15T18:36:43.000Z",
    "updatedAt": "2016-06-15T18:36:43.000Z",
    "fullName": "Janice Lu",
    "profileThumb": "https://d1rm8ch162y542.cloudfront.net/images/default-user-thumb.png",
    "profileMedium": "https://d1rm8ch162y542.cloudfront.net/images/default-user-med.png",
    "profileLarge": "https://d1rm8ch162y542.cloudfront.net/images/default-user-large.png"
  },
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzaWQiOjEsImlhdCI6MTQ2NjAxNjcyM30.ASL8gaX3Ulfs7I_lcLfa-1RVJX83qfsQP4rVbIH9AkI"
}
```

If the user exists in the Pet Parade database, this endpoint logs the user in and returns an authorization token.  If the email does not exist or the password is incorrect, an error message is returned.   

### HTTP Request

`GET http://api.parade.pet/auth/login`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | The user's email address.  This is the user's unique username.
password | true | The unencrypted password.

<aside class="success">
The user object and the user's authentication token is returned.
</aside>

## Login With Facebook

```shell
curl "http://localhost:1337/auth/loginWithFacebook"
  -d 'fbUserId=853018704828094'
  -d 'fbToken=woofwoofwoof'
```

> The above command returns JSON structured like this:

```json
{
  "user": {
    "location": 6,
    "firstName": "Janice",
    "lastName": "Lu",
    "email": "janice@parade.pet",
    "facebookId": null,
    "facebookToken": null,
    "silverCoins": 0,
    "goldCoins": 0,
    "id": 1,
    "createdAt": "2016-06-15T18:36:43.000Z",
    "updatedAt": "2016-06-15T18:36:43.000Z",
    "fullName": "Janice Lu",
    "profileThumb": "https://d1rm8ch162y542.cloudfront.net/images/default-user-thumb.png",
    "profileMedium": "https://d1rm8ch162y542.cloudfront.net/images/default-user-med.png",
    "profileLarge": "https://d1rm8ch162y542.cloudfront.net/images/default-user-large.png"
  },
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzaWQiOjEsImlhdCI6MTQ2NjAxNjcyM30.ASL8gaX3Ulfs7I_lcLfa-1RVJX83qfsQP4rVbIH9AkI"
}
```

If the user exists in the Pet Parade database, this endpoint logs the user in and returns an authorization token.  If the user does not exist in the db, the user is automatically verified with Facebook and created in the Pet Parade database if the FB token is valid.  

### HTTP Request

`GET http://api.parade.pet/auth/loginWithFacebook`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
fbUserId | true | The user's Facebook user ID as returned by the Facebook API.
fbToken | true | A valid Facebook auth token.

<aside class="success">
The user object and the user's authentication token is returned.
</aside>


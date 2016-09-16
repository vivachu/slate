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

`POST http://api.parade.pet/auth/login`

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

## Login With Twitter

```shell
curl "http://localhost:1337/auth/loginWithTwitter"
  -d 'twitterToken=woofwoofwoof'
```

> The above command returns JSON structured like this:

```json
{
  "user": {
    "location": 6,
    "firstName": "Janice",
    "lastName": "Lu",
    "email": "janice@parade.pet",
    "silverCoins": 2920,
    "goldCoins": 5,
    "id": 1,
    "fullName": "Janice Lu",
    "profileImage": 12282
  },
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzaWQiOjEsImlhdCI6MTQ2NjAxNjcyM30.ASL8gaX3Ulfs7I_lcLfa-1RVJX83qfsQP4rVbIH9AkI"
}
```

If the user exists in the Pet Parade database, this endpoint logs the user in and returns an authorization token.  If the user does not exist in the db, the user is automatically verified with Twitter and created in the Pet Parade database if the Twitter token is valid.  

### HTTP Request

`GET http://api.parade.pet/auth/loginWithTwitter`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
twitterToken | true | A valid Twitter auth token.

<aside class="success">
The user object and the user's authentication token is returned.
</aside>

## Login With Google

```shell
curl "http://localhost:1337/auth/loginWithGoogle"
  -d 'googleToken=woofwoofwoof'
```

> The above command returns JSON structured like this:

```json
{
  "user": {
    "location": 6,
    "firstName": "Janice",
    "lastName": "Lu",
    "email": "janice@parade.pet",
    "silverCoins": 2920,
    "goldCoins": 5,
    "id": 1,
    "fullName": "Janice Lu",
    "profileImage": 12282
  },
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzaWQiOjEsImlhdCI6MTQ2NjAxNjcyM30.ASL8gaX3Ulfs7I_lcLfa-1RVJX83qfsQP4rVbIH9AkI"
}
```

If the user exists in the Pet Parade database, this endpoint logs the user in and returns an authorization token.  If the user does not exist in the db, the user is automatically verified with Google and created in the Pet Parade database if the Google token is valid.  

### HTTP Request

`GET http://api.parade.pet/auth/loginWithGoogle`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
googleToken | true | A valid Google auth token.

<aside class="success">
The user object and the user's authentication token is returned.
</aside>


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
    "silverCoins": 0,
    "goldCoins": 0,
    "id": 1,
    "fullName": "Janice Lu",
    "profileImage": 1232
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
  -d 'utm_campaign=contest-adwords'
  -d 'utm_medium=display'
  -d 'utm_source=google'
  -d 'device={"model":"SM-G930P","vendor":"Samsung","type":"mobile"}'
  -d 'os={"name":"Android","version":"6.0.1"}'  
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
			"profileImage": null,
			"socialImageUrl": "https://graph.facebook.com/v2.7/10205685653854321/picture?height=100&width=100"
		  },
		  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzaWQiOjEsImlhdCI6MTQ2NjAxNjcyM30.ASL8gaX3Ulfs7I_lcLfa-1RVJX83qfsQP4rVbIH9AkI"
		}
```

If the user exists in the Pet Parade database, this endpoint logs the user in and returns an authorization token.  If the user does not exist in the db, the user is automatically verified with Facebook and created in the Pet Parade database if the FB token is valid.  

### HTTP Request

`POST http://api.parade.pet/auth/loginWithFacebook`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
fbUserId | true | The user's Facebook user ID as returned by the Facebook API.
fbToken | true | A valid Facebook auth token.
utm_campaign | false | Marketing campaign pass through
utm_medium | false | Marketing pass through
utm_source | false | Marketing pass through
device | false | The device model, vendor and type passed through as a JSON string 
os | false | The iOS name and version passed through as a JSON string

<aside class="success">
The user object and the user's authentication token is returned.
</aside>

## Login With Twitter

```shell
curl "http://localhost:1337/auth/loginWithTwitter"
  -d 'twitterToken=woofwoofwoof'
  -d 'twitterSecret=woofwoofwoofSecret'
  -d 'utm_campaign=contest-adwords'
  -d 'utm_medium=display'
  -d 'utm_source=google'
  -d 'device={"model":"SM-G930P","vendor":"Samsung","type":"mobile"}'
  -d 'os={"name":"Android","version":"6.0.1"}'  
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
    "profileImage": null,
	"socialImageUrl": "https://pbs.twimg.com/profile_images/378800000753932431/676c96084573bd3f0cf8cdda9bf9b81c_bigger.jpeg"
  },
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzaWQiOjEsImlhdCI6MTQ2NjAxNjcyM30.ASL8gaX3Ulfs7I_lcLfa-1RVJX83qfsQP4rVbIH9AkI"
}
```

If the user exists in the Pet Parade database, this endpoint logs the user in and returns an authorization token.  If the user does not exist in the db, the user is automatically verified with Twitter and created in the Pet Parade database if the Twitter token is valid.  

### HTTP Request

`POST http://api.parade.pet/auth/loginWithTwitter`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
twitterToken | true | A valid Twitter auth token.
twitterSecret | true | A valid Twitter secret that pais with the auth token.
utm_campaign | false | Marketing campaign pass through
utm_medium | false | Marketing pass through
utm_source | false | Marketing pass through
device | false | The device model, vendor and type passed through as a JSON string 
os | false | The iOS name and version passed through as a JSON string

<aside class="success">
The user object and the user's authentication token is returned.
</aside>

## Login With Google

```shell
curl "http://localhost:1337/auth/loginWithGoogle"
  -d 'googleToken=woofwoofwoof'
  -d 'utm_campaign=contest-adwords'
  -d 'utm_medium=display'
  -d 'utm_source=google'
  -d 'device={"model":"SM-G930P","vendor":"Samsung","type":"mobile"}'
  -d 'os={"name":"Android","version":"6.0.1"}'  
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
    "profileImage": null,
	"socialImageUrl": "https://lh5.googleusercontent.com/-qwH0vbfyHXo/AAAAAAAAAAI/AAAAAAAAAA0/r7qnmlhNFV4/s96-c/photo.jpg"    
  },
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzaWQiOjEsImlhdCI6MTQ2NjAxNjcyM30.ASL8gaX3Ulfs7I_lcLfa-1RVJX83qfsQP4rVbIH9AkI"
}
```

If the user exists in the Pet Parade database, this endpoint logs the user in and returns an authorization token.  If the user does not exist in the db, the user is automatically verified with Google and created in the Pet Parade database if the Google token is valid.  

### HTTP Request

`POST http://api.parade.pet/auth/loginWithGoogle`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
googleToken  | true | Pet Parade server will validate the googleToken with Google
utm_campaign | false | Marketing campaign pass through
utm_medium | false | Marketing pass through
utm_source | false | Marketing pass through
device | false | The device model, vendor and type passed through as a JSON string 
os | false | The iOS name and version passed through as a JSON string

<aside class="success">
The user object and the user's Pet Parade authentication token is returned.
</aside>

## Validate Social Tokens

```shell
curl "http://api.parade.pet/auth/validateSocialTokens"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this: 

```
{
    "facebook": true,
    "twitter": false
}
```

This endpoint validates the user's saved auth tokens for Facebook and Twitter and confirms whether the token is valid to share content on the user's behalf.  

### HTTP Request

`GET http://api.parade.pet/auth/validateSocialTokens`
  
### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns true or false for each social network. Note that false will be returned if a social network's token has expired or does not possess access rights to post on the user's behalf.  
</aside>

## Set Social Token

```shell
curl "http://api.parade.pet/auth/setSocialToken"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'fbUserId=218127272'
  -d 'fbToken=28SAKJDNBHDHAKAJJEJE28XJHSU'  
```

> The above command returns JSON structured like this: 

```
    "OK"
```

This endpoint saves either the user's facebook and/or twitter social tokens.  If you are passing in the fbToken, then the user's fbUserId is also required.  If you are passing in the user's twitterToken, then the user's twitterSecret is also required.  

### HTTP Request

`POST http://api.parade.pet/auth/setSocialToken`
  
### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
fbToken | false | Either the facebook token or the twitter token is required.
fbUserId | false | The facebookId of the user.
twitterToken | false | Either the facebook token or the twitter token is required.
twitterSecret | false | The user's twitter secret.

<aside class="success">
Returns OK if the logged in user's social tokens was updated successfully.
</aside>

## Forgot Password

```shell
curl "http://localhost:1337/auth/forgotPassword"
  -d 'email=janice@parade.pet'
```

> The above command returns JSON structured like this:

```json
  "OK"
```

If the user exists in the Pet Parade database, this endpoint sends an email to the user with a randomly generated password reset code that expires after 24 hours.  

### HTTP Request

`POST http://api.parade.pet/auth/forgotPassword`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | The username of the user.

<aside class="success">
Returns OK if user was found and email sent successfully.
</aside>

## Verify Forgot Password Code

```shell
curl "http://localhost:1337/auth/verifyForgotPasswordCode"
  -d 'email=janice@parade.pet'
  -d 'code=2828XJHSU'
```

> The above command returns JSON structured like this:

```json
{
  "forgotToken": "DJANNkkdnadsnadsfkhheaed.asdfajskewen"
}
```

If the user exists in the Pet Parade database and the code is correct, then a temporary authorization token is passed back to the user which must be passed as the Authorization header to the changePassword endpoint.  

### HTTP Request

`POST http://api.parade.pet/auth/verifyForgotPasswordCode`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | The username of the user.
code | true | The code sent to the user.

<aside class="success">
Returns the authorization token to use for the changePassword endpoint.
</aside>

## Change Password

```shell
curl "http://localhost:1337/auth/changePassword"
  -d 'email=janice@parade.pet'
  -d 'newPassword=myNewPassword'
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

The user's password is changed and the user object and permanent authentication token is returned.   

### HTTP Request

`POST http://api.parade.pet/auth/changePassword`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization: Forgot meowmeowmeow | true | Replace "meowmeowmeow" with the temporary ForgotPassword token of the user. 


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | The username of the user.
newPassword | true | The new password.

<aside class="success">
Sets the user's password to the new value and returns the user object and the authorization token for subsequent requests.  
</aside>



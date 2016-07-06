---
title: Pet Parade API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>Pet Parade</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Pets Parade API! You can use our API to access Pet Parade API endpoints.

You can view examples on how to call each endpoint from the Shell using curl or via your web browser using the Postman extension in the dark area to the right.

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

`GET http://api.parade.pet/auth/login`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | The user's email address.  This is the user's unique username.
password | true | The unencrypted password.

<aside class="success">
The user object and the user's authentication token is returned.
</aside>


# Game Play

## Get Active FaceOffSet

```shell
curl "http://localhost:1337/faceoffset/active"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
  // TODO: REPLACE WITH REAL EXAMPLE
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
]
```

This endpoint retrieves the authorized user's active FaceOffSet.  If no FaceOffSet is currently active or all the FaceOffs in the set have been completed then a new FaceOffSet is created and returned..

### HTTP Request

`GET http://localhost:1337/faceoffset/active`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns the active FaceOffSet for the user to begin the game play session.
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve


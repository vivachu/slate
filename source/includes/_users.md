# Users

## Sign up With Email

```shell
curl "http://localhost:1337/user/create"
  -d 'email=janice@parade.pet'
  -d 'password=p3tp@rad3!'
  -d 'firstName=Janice'
  -d 'lastName=Lu'
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
confirmPassword | false | The unencrypted password
firstName | true | The user's first name
lastName | true | The user's last name
utm_campaign | false | Marketing campaign pass through
utm_medium | false | Marketing pass through
utm_source | false | Marketing pass through
device | false | The device model, vendor and type passed through as a JSON string 
os | false | The iOS name and version passed through as a JSON string

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

## Send Feedback

```shell
curl "http://api.parade.pet/user/sendFeedback"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'subject=Feature Suggestion'
  -d 'message=I would love to be able to delete a photo.'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint reports an entry that the user finds questionable.

### HTTP Request

`POST http://api.parade.pet/user/sendFeedback`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
subject | true | The subject of your message  
message | true | The message

<aside class="success">
Returns OK
</aside>

## Get User Profile

```shell
curl "http://api.parade.pet/user/profile"
  -d 'id=1523'
```

> The above command returns JSON structured like this:

```json 
{
  "name": "Kaylyn may",
  "profileImage": 5927,
  "socialImageUrl": null,
  "location": "Knoxville, Tn",
  "pets": [
    {
      "id": 1408,
      "name": "Moose"
    },
    {
      "id": 1409,
      "name": "Hank"
    }
  ],
  "entries": [
    {
      "id": 3253,
      "image": 5926
    },
    {
      "id": 3252,
      "image": 5925
    },
    {
      "id": 3251,
      "image": 5924
    },
    {
      "id": 3250,
      "image": 5923
    },
    {
      "id": 3246,
      "image": 5919
    },
    {
      "id": 3245,
      "image": 5918
    }
  ]
}
```

This endpoint returns the user profile for the specific userId passed as a parameter.

### HTTP Request

`GET http://api.parade.pet/user/profile/<id>`

### Header Parameters

None


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | userId value, passed in the url path

<aside class="success">
Returns the user profile for the specific userId.
</aside>

## Edit User Profile

```shell
curl "http://api.parade.pet/user/update"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json 
"OK"
```

This endpoint update the user profile for the signed in user.

### HTTP Request

`POST http://api.parade.pet/user/update`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
firstName | false | The user's first name
lastName | false | The user's last name
location | false | The user's location
profileImage | false | The id of the user's profile image


<aside class="success">
Returns OK if success or an error message.
</aside>

## Create Address

```shell
curl "http://localhost:1337/user/address/create"
  -d 'email=janice@parade.pet'
  -d 'contactName=Janice Lu'
  -d 'street1=123 Any Ln'
  -d 'street2=Apt 1'
  -d 'city=San Francisco'
  -d 'state=California'
  -d 'postalCode=94546'
```

> The above command returns JSON structured like this:

```json
{
  "address": 4
}
```

Create a new address for the user.  Returns the ID of the address object.
### HTTP Request

`POST http://api.parade.pet/user/address/create`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
email | true | The user's email address to send the shipping confirmation
contactName | true | The contact name of the user to ship to.
street1 | tree | The street address
street2 | false | Second line of address
city | true | City
state | true | State
postalCode | true | Zip Code
placeId | false | Google Place ID

<aside class="success">
The newly created address ID is returned.
</aside>

## Update Address

```shell
curl "http://localhost:1337/user/address/update"
  -d 'id=4'
  -d 'email=janice@parade.pet'
  -d 'contactName=Janice Lu'
  -d 'street1=123 Any Ln'
  -d 'street2=Apt 1'
  -d 'city=San Francisco'
  -d 'state=California'
  -d 'postalCode=94546'
```

> The above command returns JSON structured like this:

```json
{
  "address": 4
}
```

Update the address for the user.  Returns the ID of the address object.
### HTTP Request

`POST http://api.parade.pet/user/address/update`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | The ID of the address object to update
email | true | The user's email address to send the shipping confirmation
contactName | true | The contact name of the user to ship to.
street1 | tree | The street address
street2 | false | Second line of address
city | true | City
state | true | State
postalCode | true | Zip Code
placeId | false | Google Place ID

<aside class="success">
The updated address ID is returned.
</aside>

## Get Shipping Address

```shell
curl "http://api.parade.pet/user/address"
  -d 'id=1523'
```

> The above command returns JSON structured like this:

```json 
{
  "user": 104,
  "contactName": "Paula Pickles",
  "email": "paulapickles@gmail.com",
  "street1": "67 Baldwin",
  "street2": null,
  "city": "San Francisco",
  "state": "California",
  "postalCode": "012922",
  "placeId": null,
  "id": 1
}
```

This endpoint returns the user profile for the specific userId passed as a parameter.

### HTTP Request

`GET http://api.parade.pet/user/address`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------

<aside class="success">
Returns the user's shipping address.
</aside>

## Set User Location

```shell
curl "http://api.parade.pet/user/setLocation"
  -d 'name=New York, NY, United States'
  -d 'placeId=ChIJOwg_06VPwokRYv534QaPC8g'
  -d 'city=New York'
  -d 'state=NY'
  -d 'country=United States'
  -d 'postalCode=10014'
```

> The above command returns JSON structured like this:

```json
"OK"
```

This endpoint updates the user's location, creating a new Location object if necessary.

### HTTP Request

`POST http://api.parade.pet/user/setLocation`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
name | true | New York, NY, United States
placeId | true | placeId returned by Google Places API
city | true | full city name returned by Google Places API
state | true | 2-letter abbreviation for state
country | true | country name returned by Google Places API
postalCode | true | postal code

<aside class="success">
Returns "OK"
</aside>

## Set Marketing Info

```shell
curl "http://api.parade.pet/user/setMarketingInfo"
  -d 'shopType=1'
  -d 'petStoreName="Petco"
  -d 'petStoreplaceId=ChIJOwg_06VPwokRYv534QaPC8g'
  -d 'petStoreAddress="157 Chambers Street, New York"
  -d 'petSite="PetCo"
```

> The above command returns JSON structured like this:

```json
"OK"
```

This endpoint updates the user's marketing info, creating a new PetSite object or pet store Location object if necessary.  Either (shopType, petStore, petStorePlaceId, petStoreAddress, petStoreCity, petStoreState) OR (shopType, petSite) parameters are required.

### HTTP Request

`POST http://api.parade.pet/user/setMarketingInfo`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
shopType | true | 0=phone, 1=computer, 2=local store
petStoreName | false | PetCo
petStorePlaceId | false | ChIJOwg_06VPwokRYv534QaPC8g
petStoreAddress | false | 157 Chambers Street
petStoreCity | false | New York
petStoreState | false | NY
petSite | false | PetCo

<aside class="success">
Returns "OK"
</aside>

## Get Marketing Info

```shell
curl "http://api.parade.pet/user/setMarketingInfo"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
    "shopType": 1,
    "petsite": {
        "name": "PetEdge",
        "url": "https://www.petedge.com"
    }
}
```
> OR

```json
{
    "shopType": 1,
    "petstore": {
        "name": "PetCo",
        "address": "157 Chambers Street, New York",
        "city": "New York",
        "state": "NY",
        "country": "United States"
    }
}

```

This endpoint returns the user's marketing info, including either the petsite or petstore.

### HTTP Request

`GET http://api.parade.pet/user/setMarketingInfo`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

None

<aside class="success">
Returns user marketing info.  If no marketing info, returns {}.
</aside>


## Archive User

```shell
curl "http://api.parade.pet/user/archive"
  -d 'userid=1523'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint archives the user and all associated data and unsubscribes from Mailchimp when passed userid as a parameter. You must be logged in as an admin user.

### HTTP Request

`POST http://api.parade.pet/user/archive`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user (must be an admin user)


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userid | true | The userId of the user to archive

<aside class="success">
Returns "OK"
</aside>


## Unarchive User

```shell
curl "http://api.parade.pet/user/unarchive"
  -d 'userid=1523'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint unarchives the user and all associated data and resubscribes to Mailchimp when passed userid as a parameter. You must be logged in as an admin user.

### HTTP Request

`POST http://api.parade.pet/user/unarchive`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user (must be an admin user)


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
userid | true | The userId of the user to unarchive

<aside class="success">
Returns "OK"
</aside>



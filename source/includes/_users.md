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
timeZoneOffset | false |  the local timezone offset as a signed floating point number.  For example -4.5 is four hours and 30 minutes from GMT. 


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
email | false | The replyTo address

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
  ],
  "awards": [
    {
      "pet": {
        "id": 1039,
        "name": "Coder",
        "profileImage": 5981
      },
      "name": "33rd Place Dog",
      "period": "Month of Mar 2017",
      "ribbon": "33rd"
    },
    {
      "pet": null,
      "name": "The Generous Pet Parent Award",
      "period": "Week of Feb 26, 2017",
      "ribbon": "G"
    },
    {
      "pet": {
        "id": 1040,
        "name": "Joey",
        "profileImage": 5981
      },
      "name": "24th Place Cat",
      "period": "Week of Feb 26, 2017",
      "ribbon": "24th"
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
  -d 'street=158 Berkeley Place'
  -d 'placeId=ChIJOwg_06VPwokRYv534QaPC8g'
  -d 'city=New York'
  -d 'state=NY'
  -d 'country=United States'
  -d 'postalCode=11215'
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
street | false | street address 
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
curl "http://api.parade.pet/user/marketingInfo"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
    "shopType": 1,
    "petSite": {
        "name": "BarkBox",
        "url": "https://barkbox.com"
    },
    "petStore": {
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

`GET http://api.parade.pet/user/marketingInfo`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

None

<aside class="success">
Returns user marketing info.  If no marketing info, returns {}.
</aside>




## Get Friend Code

```shell
curl "http://api.parade.pet/user/friendCode"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
    "friendCode": "123abc", 
    "referralBonus": { 
      "amount": 25, 
      "type": "goldTickets"
    }
}
```

This endpoint returns the user's friend code.

### HTTP Request

`GET http://api.parade.pet/user/friendCode`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

None

<aside class="success">
Returns user friend code.
</aside>


## Get Friends

```shell
curl "http://api.parade.pet/user/friends"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
    "referers": [
        {
            "userid": 25,
	    "profileImage": 954,
            "socialImageUrl": null,
            "initials": "MW",
            "fullname": "Mike W",
            "pets": [
                {
                    "pet": 32,
                    "name": "Fido",
                    "image": 3227,
                    "type": "dog",
                    "place": 68148,
                    "placeByType": 39140,
                    "placeByLocation": 2761,
                    "placeByBreed": 44,
                    "points": 0,
                    "birthYear": 2016,
                    "birthMonth": null,
                    "birthDay": null
                }
            ]
        }
    ],
    "referred": [
        {
            "referralBonus": null,
            "referralBonusType": null,
            "referralBonusAwardedDate": null,
            "userid": 7220,
            "pets": [
                {
                    "pet": 6406,
                    "name": "Ava",
                    "image": 31823,
                    "type": "dog",
                    "place": 40183,
                    "placeByLocation": 10000,
                    "placeByBreed": 360,
                    "placeByType": 23122,
                    "points": 0,
                    "birthYear": 2014,
                    "birthMonth": null,
                    "birthDay": null
                }
            ]
        },
        {
            "referralBonus": 25,
            "referralBonusType": 1,
            "referralBonusAwardedDate": "2017-08-30T23:27:24.000Z",
            "userid": 30,
            "pets": [
                {
                    "pet": 52,
                    "name": "blue",
                    "image": 186,
                    "type": "dog",
                    "placeByLocation": 10000,
                    "placeByBreed": 40,
                    "points": 0,
                    "place": 50765,
                    "placeByType": 29299,
                    "birthYear": 2014,
                    "birthMonth": null,
                    "birthDay": null
                }
            ]
        }
    ]
}
```

This endpoint returns the user's friends, separated into referred and referers.  For referred friends, the fields "referralBonus", "referralBonusType", and "referralBonusAwardedDate" will show from which referred friend the current user received a referral bonus.  For referer friends, these fields will be fields will show which referer friend received the referral bonus from referring the current user.

### HTTP Request

`GET http://api.parade.pet/user/friends`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

None

<aside class="success">
Returns user's friends.
</aside>

## Add Friend

```shell
curl "http://api.parade.pet/user/addFriend"
  -H "Authorization:  Bearer meowmeowmeow"
  -d "friendCode=abc123"
```

> The above command returns JSON structured like this:

```json
    "OK"
```

This endpoint adds a friend if the POSTed friendCode matches existing user's code.

### HTTP Request

`POST http://api.parade.pet/user/addFriend`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
friendCode | true | The friendCode of the friend to add

<aside class="success">
Returns OK
</aside>

## Friend Ladder

```shell
curl "http://api.parade.pet/user/friends"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'start=2017-09-01'
  -d 'end=2017-09-30'
  -d 'placeId=ChIJ7cv00DwsDogRAMDACa2m4K8'
  -d 'type=dog'
```

> The above command returns JSON structured like this:

```json
{
    "referralBonus": {
        "amount": 25,
        "type": "goldTickets"
    },
    "friendLadder":
    [
        {
            "id": 25,
            "firstName": "Mike",
            "lastName": "W",
            "profileImage": 954,
            "socialImageUrl": null,
            "highestRank": 0,
            "pets": [
                {
                    "pet": 3151,
                    "name": "Birdie",
                    "image": 14858,
                    "type": "other",
                    "place": 2096,
                    "placeByBreed": 19,
                    "placeByType": 241,
                    "placeByLocation": 115,
                    "placeId": "ChIJOwg_06VPwokRYv534QaPC8g",
                    "points": 3450,
                    "birthYear": 2015,
                    "birthMonth": null,
                    "birthDay": null
                },
                {
                    "pet": 32,
                    "name": "Fido",
                    "image": 3227,
                    "type": "dog",
                    "place": 5798,
                    "placeByLocation": 303,
                    "placeId": "ChIJOwg_06VPwokRYv534QaPC8g",
                    "placeByBreed": 10000,
                    "placeByType": 2849,
                    "points": 1570,
                    "birthYear": 2016,
                    "birthMonth": null,
                    "birthDay": null
                }
            ]
        },
        {
            "id": 26,
            "firstName": "Kristi",
            "lastName": " Clark",
            "profileImage": null,
            "socialImageUrl": null,
            "highestRank": 26384,
            "pets": [
                {
                    "pet": 1474,
                    "name": "Chirp",
                    "image": 6234,
                    "type": "other",
                    "place": 26384,
                    "placeByType": 1413,
                    "placeByLocation": 771,
                    "placeId": "ChIJ7cv00DwsDogRAMDACa2m4K8",
                    "placeByBreed": 139,
                    "points": 490,
                    "birthYear": 2016,
                    "birthMonth": 5,
                    "birthDay": 31
                },
                {
                    "pet": 49951,
                    "name": "Callie",
                    "image": 200918,
                    "type": "cat",
                    "place": 42314,
                    "placeByBreed": 547,
                    "points": 100,
                    "placeByType": 15674,
                    "placeByLocation": 1279,
                    "placeId": "ChIJ7cv00DwsDogRAMDACa2m4K8",
                    "birthYear": 2016,
                    "birthMonth": 3,
                    "birthDay": 2
                }
            ]
        }
    ]
}
```

This endpoint returns the user's friend ladder for the specific leaderboard chosen.

### HTTP Request

`GET http://api.parade.pet/user/friendLadder`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
start | true | start date for the leaderboard
end | true | end date for the leaderboard
placeId | false | placeId for the location leaderboard
type | true | leaderboard type (dog, cat, other, all, location)

<aside class="success">
Returns user's friend ladder as an array of friends, where each friend has an array of pets, for the chosen leaderboard.
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



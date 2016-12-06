# Pets

## Leaderboard

```shell
curl "http://api.parade.pet/pet/leaderboard"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'start=2016-06-01'
  -d 'end=2016-06-30'
  -d 'place=200'
  -d 'size=3'  
  -d 'type=dog'
  -d 'contest=1'
```

> The above command returns JSON structured like this:

```json 
{
	"leaderboard": [
	{ 
	  "id": 129,
	  "image": 234,
	  "name": "Fluffy",
	  "place": 200,
	  "points": 10900,
	  "numFaceOffs": 900,
	  "numTreats": 212
	},
	{ 
	  "id": 1928,
	  "image": 2328,
	  "name": "Spanky",
	  "place": 201,
	  "points": 10800,
	  "numFaceOffs": 1029,
	  "numTreats": 29
	},
	{ 
	  "id": 876,
	  "image": 202,
	  "name": "Donald",
	  "place": 202,
	  "points": 10500,
	  "numFaceOffs": 872,
	  "numTreats": 450
	}
	]
}
```

Pets accumulate points for FaceOff wins and Treats received.  The leaderboard endpoint returns an ordered list of pets using the sum total of points across all entries for a specified contest over a set time period.  If no contest is specified, then the leaderboard sums points across all contests (default).

### HTTP Request

`GET http://api.parade.pet/pet/leaderboard`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
start | false | Start date in yyyy-mm-dd format to limit results. If no start date is defined, the first day of the current month is assumed as the time period.  
end | false | End date in yyyy-mm-dd format to limit results.  The end date is inclusive, meaning if 2016-06-30 is specified then points scored any time on 6/30 are included. If no end date is defined, the last day of the start month is assumed as the time period. 
place | false | The placement position to start the return results.
type | false | The type of pet to filter against: dog, cat, other.  No value indicates all pets.
contest | false | id value of the Contest to filter the results against.  If no contest is specified, then the points are summed across all contests.  

<aside class="success">
This endpoint returns the leaderboard for the specified time period, contest, and pet type.  By default if no parameters are passed, then the top 100 pets for the current month across all contests are returned. 
</aside>


## Get My Pets

```shell
curl "http://api.parade.pet/pets"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'start=2016-06-01'
  -d 'end=2016-06-30'
  -d 'contest=1'
```

> The above command returns JSON structured like this:

```json 
{
	"pets": [
	{ 
	  "id": 129,
	  "image": 234,
	  "name": "Mr Big",
	  "place": 1292,
	  "points": 900,
	  "numFaceOffs": 98,
	  "numTreats": 9	  
	},
	{ 
	  "id": 1928,
	  "image": 2328,
	  "name": "Sparks",
	  "place": 989,
	  "points": 1010,
	  "numFaceOffs": 289,
	  "numTreats": 21
	}
	]
}
```

This endpoint returns the authorized user's pets and their points total and placement over the specified time period and contest.  By default if no parameters are passed, then the pet's points balance and placement are calculated for the current month across all contests. 

### HTTP Request

`GET http://api.parade.pet/pets`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
start | false | Start date in yyyy-mm-dd format over which to calculate points and placement. If no start date is defined, the first day of the current month is assumed as the time period.  
end | false | End date in yyyy-mm-dd format over which to calculate points and placement. If no end date is defined, the last day of the start month is assumed as the time period. 
contest | false | id value of the Contest to filter the results against.  If no contest is specified, then the points are summed across all contests.  

<aside class="success">
Returns the authorized user's pets and their points total and placement over the specified time period and contest.  By default if no parameters are passed, then the pet's points balance and placement are calculated for the current month across all contests. 
</aside>

## Get Pet Profile

```shell
curl "http://api.parade.pet/pet/profile"
  -d 'id=1003'
```

> The above command returns JSON structured like this:

```json 
{
  "name": "Bella",
  "breed": "Yorkie",
  "type": "Dog",
  "age": "1 Year",
  "gender": 0,
  "profileImage": 1265,
  "owner": {
    "id": 1054,
    "profileImage": 4197,
    "socialImageUrl": null,
    "name": "Carle dickerson"
  },
  "entries": [
    {
      "id": 2242,
      "image": 4196
    },
    {
      "id": 2241,
      "image": 4194
    },
    {
      "id": 2240,
      "image": 4192
    }
  ]
}
```

This endpoint returns the pet profile for the specific petId passed as a parameter.

### HTTP Request

`GET http://api.parade.pet/pet/profile/<id>`

### Header Parameters

None

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | petId value, passed in the url path

<aside class="success">
Returns the pet profile for the specific petId.
</aside>

## Edit Pet Profile

```shell
curl "http://api.parade.pet/pet/update"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'id=1003'
```

> The above command returns JSON structured like this:

```json 
"OK"
```

This endpoint updates the pet profile for the specific petId passed as a parameter.

### HTTP Request

`POST http://api.parade.pet/pet/update/<id>`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true | petId value, passed in the url path
name | false | The name of the pet  
petBreed | false | The name of the pet's breed.    
birthYear | false | The pet's birth year in yyyy format. Compute from the pet's age.
birthMonth | false | The pet's birth month in integer format.
birthDay | false | The pet's birth day in integer format.
gender | false | 1 for boy, 0 for girl.
profileImage | false | The id of the pet's profile image.

<aside class="success">
Returns OK if success or an error message.
</aside>

## Create Pet

```shell
curl "http://api.parade.pet/pet/create"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'name=Joel'
  -d 'petType=1'
  -d 'petBreed=Alaskan Husky'
  -d 'birthYear=2015'
  -d 'birthMonth=10'
  -d 'birthDay=1'
  -d 'gender=1'
  -d 'profileImage=21982'
```

> The above command returns JSON structured like this:

```json 
{
  "pet": {
    "name": "Radiant",
    "petType": 2,
    "owner": 11422,
    "petBreed": 13,
    "gender": 2,
    "birthYear": 2016,
    "birthMonth": 10,
    "birthDay": 20,
    "profileImage": 39960,
    "id": 14893
  }
}
```

This endpoint creates the pet with the owner set to the authorized user. The endpoint returns the ID of the newly created pet.  

### HTTP Request

`POST http://api.parade.pet/pet/create`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
name | true | The name of the pet  
petType | true | The ID of the pet's type.  Call /pettype to get the list of pet types.   
petBreed | false | The name of the pet's breed.    
birthYear | false | The pet's birth year in yyyy format. Compute from the pet's age.
birthMonth | false | The pet's birth month in integer format.
birthDay | false | The pet's birth day in integer format.
gender | true | 1 for boy, 0 for girl.
profileImage | true | The id of the pet's profile image.

<aside class="success">
Returns the newly created pet object.
</aside>


## Pet Types

```shell
curl "http://api.parade.pet/pettype"
```

> The above command returns JSON structured like this:

```json 
[
  {
    "name": "Dog",
    "id": 1,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  },
  {
    "name": "Cat",
    "id": 2,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  },
  {
    "name": "Bird",
    "id": 3,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  },
  {
    "name": "Horse",
    "id": 4,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  },
  {
    "name": "Other",
    "id": 16,
    "createdAt": "2016-07-21T05:35:37.000Z",
    "updatedAt": "2016-07-21T05:35:37.000Z"
  }
]
```

Return list of pet types.

### HTTP Request

`GET http://api.parade.pet/pettype`


<aside class="success">
Return list of pet types.
</aside>

## Pet Breeds

```shell
curl "http://api.parade.pet/petbreed"
```

> The above command returns JSON structured like this:

```json 
[
  {
    "name": "Pitbull",
    "id": 16,
    "createdAt": "2016-07-21T05:35:38.000Z",
    "updatedAt": "2016-07-21T05:35:38.000Z"
  },
  {
    "name": "Norwegian Forest",
    "id": 17,
    "createdAt": "2016-07-21T05:35:38.000Z",
    "updatedAt": "2016-07-21T05:35:38.000Z"
  },
  {
    "name": "American Dingo",
    "id": 18,
    "createdAt": "2016-07-21T05:35:38.000Z",
    "updatedAt": "2016-07-21T05:35:38.000Z"
  },
  {
    "name": "American Shorthair",
    "id": 19,
    "createdAt": "2016-07-21T05:35:38.000Z",
    "updatedAt": "2016-07-21T05:35:38.000Z"
  }
]
```

Return list of pet types.

### HTTP Request

`GET http://api.parade.pet/petbreed`


<aside class="success">
Return list of pet breeds.
</aside>
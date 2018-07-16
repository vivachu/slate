# Contests

## List All Available Contests

```shell
curl "http://api.parade.pet/contests"
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[{
    "id": 8,
    "name": "#bling",
    "active": true,
    "description": "Bling out your pet with costumes, collars, & clothing.",
    "numFollowers": 0,
    "numEntries": 0,
    "sponsor": null,
    "isFollowing": false
  },
  {
    "id": 9,
    "name": "#healthyPet",
    "active": true,
    "description": "Show off your pet eating nutritious food, getting groomed, or exercising. ",
    "numFollowers": 0,
    "numEntries": 0,
    "sponsor": {
      "id": 2,
      "name": "VitaPup",
      "path": "vp",
      "hexCode": "123456",
      "numFans": 0
    },
    "isFollowing": false
  },
  {
    "id": 2,
    "name": "#play",
    "active": true,
    "description": "Chase, run, jump, chew, pull, scratch, & play, play, play!",
    "numFollowers": 1,
    "numEntries": 0,
    "sponsor": null,
    "isFollowing": true
  }
]
```

This endpoint returns all available contests.

### HTTP Request

`GET http://api.parade.pet/contests`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
The list of available contests are returned.
</aside>

## Get Contest 

```shell
curl "http://api.parade.pet/contest/:id"
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 5,
  "name": "#naptime",
  "description": "Zzzzz",
  "numFollowers": 10,
  "isFollower": true,
  "sponsor": {
    "id": 2,
    "name": "VitaPup",
    "path": "vp",
    "hexCode": "123456"
  },
  "entries": [
    {
      "id": 590295,
      "image": 800725
    },
    {
      "id": 587950,
      "image": 797815
    },
    {
      "id": 580962,
      "image": 788946
    }
  ]
}
```

Retrieve detailed information about Contest, along with their entries.

### HTTP Request

`GET http://api.parade.pet/contest/:id`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  contestId value, passed in the url path

<aside class="success">
Detailed information about contest is returned.
</aside>

## Get Sponsor 

```shell
curl "http://api.parade.pet/sponsor/:id"
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "VitaPup",
  "path": "vp",
  "hexCode": "123456",
  "numFans": 10,
  "isFan": false,
  "contests": [
    {
      "id": 9,
      "name": "#healthyPet",
      "description": "Show off your pet eating nutritious food, getting groomed, or exercising. "
    }
  ],
  "entries": [
    {
      "id": 596517,
      "image": 808247
    },
    {
      "id": 581614,
      "image": 789726
    },
    {
      "id": 575625,
      "image": 782469
    }
  ]
}
```

Retrieve detailed information about Sponsor, along with their entries and available contests.

### HTTP Request

`GET http://api.parade.pet/sponsor/:id`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  sponsorId value, passed in the url path

<aside class="success">
Detailed information about sponsor is returned.
</aside>

## Follow a Contest

```shell
curl "http://api.parade.pet/follow/2"
  -H "Authorization: Bearer meowmeowmeow"
  -d 'type=1'
```

> The above command returns JSON structured like this:

```json
{
  "followers": 10
}
```

This endpoint will add current user as a follower of a contest, and return the contest's updated follower number.

### HTTP Request

`POST http://api.parade.pet/follow/:contestId`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
contestId | true |  The id of the contest passed in the url path
type | false | The target pet type. Use 1 for dog, 2 for cat, or a number greater than 3 for critter.  Or unknown otherwise.

<aside class="success">
The number of contest followers is returned.
</aside>

## Unfollow a Contest

```shell
curl "http://api.parade.pet/unfollow/2"
  -H "Authorization: Bearer meowmeowmeow"
  -d "type=1"
```

> The above command returns JSON structured like this:

```json
{
  "followers": 10
}
```

This endpoint will remove current user as follower of a contest, and return its updated followers number.

### HTTP Request

`POST http://api.parade.pet/unfollow/2`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
contestId | true |  The contest id passed in the url path
type | false | petType, please use 1 for dog, 2 for cat, or above 3 for critter, or empty if unknown.

<aside class="success">
Updated number of contest followers is returned.
</aside>

## Fan a Sponsor

```shell
curl "http://api.parade.pet/fan/1"
  -H "Authorization: Bearer meowmeowmeow"
  -d "contest=2"
```

> The above command returns JSON structured like this:

```json
{
  "fans": 10
}
```

This endpoint will add current user as a fan of a sponsor, and return the sponsor's number of fans.

### HTTP Request

`POST http://api.parade.pet/fan/:sponsor`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
sponsor | true |  The sponsor id value passed in the url path
contest | false | The contest id that the sponsor is sponsoring 

<aside class="success">
Updated number of sponsor fans is returned.
</aside>

## Unfan a Sponsor

```shell
curl "http://api.parade.pet/unfan/1"
  -H "Authorization: Bearer meowmeowmeow"
  -d "contest=2"
```

> The above command returns JSON structured like this:

```json
{
  "fans": 10
}
```

This endpoint will remote current user from a fan of a sponsor, and return its updated fans number.

### HTTP Request

`POST http://api.parade.pet/unfan/:id?type=:type`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  sponsorId value, passed in the url path
contest | false | The contest id that the sponsor is sponsoring 

<aside class="success">
Updated number of sponsor fans is returned.
</aside>



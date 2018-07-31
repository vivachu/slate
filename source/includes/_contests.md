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
    "hexCode": "123456",
    "isFan": true
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

This endpoint will remove current user from a fan of a sponsor, and return its updated fans number.

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

## Contest Prizes

```shell
curl "http://api.parade.pet/contest/5/prizes"
  -H "Authorization: Bearer meowmeowmeow"
  -d "contest=2"
```

> The above command returns JSON structured like this:

```json
{
  "weekCountdown": 433281.421,
  "monthCountdown": 87681.421,
  "prizes": [
    {
      "id": 16,
      "place": 1,
      "weekType": "silverTickets",
      "weekAmount": 10,
      "monthType": "prize",
      "monthAmount": 1,
      "prize": {
        "id": 196,
        "name": "T-Shirt with Your Cat's Photo",
        "imageUrl": "https://www.parade.pet/assets/images/T-Shirt-Cat.png"
      }
    },
    {
      "id": 17,
      "place": 2,
      "weekType": "silverTickets",
      "weekAmount": 10,
      "monthType": "goldTickets",
      "monthAmount": 10,
      "prize": null
    },
    {
      "id": 18,
      "place": 3,
      "weekType": "silverTickets",
      "weekAmount": 10,
      "monthType": "goldTickets",
      "monthAmount": 10,
      "prize": null
    }
  ]
}
```

This endpoint will returns a list of contest's prizes.

### HTTP Request

`GET http://api.parade.pet/contest/:id/prizes`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  contestId value, passed in the url path

<aside class="success">
List of Prizes for current Contest, along with remaining time until the end of the week and the end of the month in seconds.
</aside>

## Contest Rules

```shell
curl "http://api.parade.pet/contest/4/rules"
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "name": "Header",
    "rule": "The \"#GOODEATS\" Contest (the “Contest”) begins at 12:00 a.m., Eastern Time (“ET”) on July 1, 2018 and ends at 11:59 p.m., (“ET”) on August 15, 2018 <br/>(\"Contest Period\"). The Contest is sponsored by Good Boy Studios, Inc, 47 Benjamin St, Old Greenwich CT 06870 (the \"Sponsor\"). Participation constitutes <br />entrant's full and unconditional agreement to and acceptance of these Official Rules."
  },
  {
    "name": "Eligibility",
    "rule": "The Contest is open to residents of the fifty (50) United States and the District of Columbia and Canada (excluding Quebec) who are 13 years of age or older as of the Contest start date. Employees, officers and representatives of the Sponsor, their parents, affiliates, subsidiaries, agents, prize providers, advertising and promotion agencies, and American Sweepstakes &amp; Promotion Co. Inc. (“Administrator”) (collectively, “Released Parties”) and members of the immediate family (mother, father, sons, daughters and spouse, regardless of where they reside) and household members of each, whether or not related, are not eligible to participate in the Contest. Participation constitutes entrant's full and unconditional agreement to and acceptance of these official rules. <strong>Void in Puerto Rico and where prohibited by law.</strong>"
  },
  {
    "name": "Timing",
    "rule": "<p>The Contest Period consists of a Submission Period (the \"Submission Period\"), a Month Voting Period (the \"Voting Period\") and a Judging Period (the \"Judging Period\") as set forth in the chart below. All times are in Eastern Time.</p><table class=\"timing\"><thead><tr><td>Period</td><td>Start</td><td>End</td></tr></thead><tbody><tr><td>Contest Period:</td><td><span>Start: </span>July 1, 2018, 12:00 am</td><td><span>End: </span>August 15, 2018, 11:59 pm</td></tr><tr><td>Submission Period:</td><td><span>Start: </span>July 1, 2018, 12:00 am</td><td><span>End: </span>July 31, 2018, 11:59 pm</td></tr><tr><td>Voting Period:</td><td><span>Start: </span>July 1, 2018, 12:00 am</td><td><span>End: </span>July 31, 2018, 11:59 pm</td></tr></tr><tr><td>Judging Period:</td><td><span>Start: </span>July 1, 2018 12:00 am</td><td><span>End: </span>August 15, 2018, 11:59 pm</td></tr><tr><td>Winners Announced:</td><td><span>Start: </span>August 15, 2018</td><td></td></tr></tbody></table>"
  }
]
```

This endpoint will returns list of rules for current Contest.

### HTTP Request

`GET http://api.parade.pet/contest/:id/rules`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  contestId value, passed in the url path

<aside class="success">
List of rules for current Contest, returned as an array. Each of array consisting the Section header, and Rule content, formatted in HTML.
</aside>


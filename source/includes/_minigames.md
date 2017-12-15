# Minigames

## Start

```shell
curl "http://api.parade.pet/minigame/start"
  -d 'faceOffSet=930703'
  -d 'user=25'
```

> The above command returns JSON structured like this:

```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzaWQiOjEsImlhdCI6MTQ5NzkwMDY5NH0.2Iwv-6tXzy5CHz1mC8opIDrCF0v5L8Pn8fnp9GrjwB4"
}
```

Retrieve the minigame session token to be used in other minigame endpoints for authentication.

### HTTP Request

`POST http://api.parade.pet/minigame/start`

### Header Parameters

None

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
faceOffSet | true | id value of current FaceOffSet
user | true | id value of signed in user

<aside class="success">
Returns minigame session token.
</aside>

## Get Pets

```shell
curl "http://api.parade.pet/minigame/getPets"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
    {
        "id": 127477,
        "image": 161327
    },
    {
        "id": 73202,
        "image": 95041
    },
    {
        "id": 49130,
        "image": 64121
    },
    {
        "id": 127349,
        "image": 161161
    }
]
```

Returns the list of entries to use for the minigame.

### HTTP Request

`GET http://api.parade.pet/minigame/getPets`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the minigame session token


### Query Parameters

None

<aside class="success">
Returns list of entries to be used in the current minigame.
</aside>

## End

```shell
curl "http://api.parade.pet/minigame/end"
  -H "Authorization:  Bearer meowmeowmeow"
  -d "score=10"
```

> The above command returns JSON structured like this:

```json
{
    "coinBonus": {
        "amount": 190,
        "type": "silver"
    },
    "pointBonus": 100,
    "pet": {
        "id": 111668,
        "name": "Sammy",
        "profileImage": 474438,
        "user": {
            "id": 112944,
            "profileImage": null,
            "socialImageUrl": "https://graph.facebook.com/v2.7/10213976261738231/picture?height=100&width=100",
            "name": "Sunshine Stone",
            "initials": "SS",
            coins: { 
                silver: 425, 
                gold: 620 
            }
        }
    },
    "nextSession": {
        "friendPet": {
            "name": "Coder",
            "image": 476501
        },
        "message": "Walk Coder in 6 h 0 m 0 s"
    }
}
```

Updates the minigame session with coin bonus and ends the session, updates user (silver or gold coin count) and userevent (minigamesPlayed) tables, and returns the coin bonus for this minigame session.

### HTTP Request

`POST http://api.parade.pet/minigame/end`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the minigame session token


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
score | true | score for this minigame session

<aside class="success">
Returns coin bonus.
</aside>

## Get Minigame Session

```shell
curl "http://api.parade.pet/minigame/session"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
    "firstName": "Jessica",
    "lastName": "Wang",
    "userId": 136746,
    "profileImage": null,
    "socialImageUrl": null,
    "numEntries": 298,
    "petName": "Munchkin",
    "petImage": 703842,
    "petPoints": 25,
    "path": "pet-walk",
    "actionPhrase": "walked Munchkin",
    "pets": [
        {
            "id": 148882,
            "name": "Cookie",
            "entry": 474310,
            "image": 649371,
            "points": 1961,
            "type": "Cat"
        },
        {
            "id": 148876,
            "name": "Oreo",
            "entry": 474293,
            "image": 649353,
            "points": 1044,
            "type": "Cat"
        },
        {
            "id": 140358,
            "name": "Mimi",
            "entry": 443373,
            "image": 608152,
            "points": 1015,
            "type": "Cat"
        },
        {
            "id": 136777,
            "name": "Xiao Guai",
            "entry": 430676,
            "image": 591033,
            "points": 1460,
            "type": "Cat"
        }
    ]
}
```

Returns the list of entries to use for the minigame.

### HTTP Request

`GET http://api.parade.pet/minigame/session/:sessionId`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the minigame session token


### Query Parameters
Parameter | Required | Description
--------- | ------- | -----------
sessionId | true | id value of the MinigameSession to return.


<aside class="success">
Returns the minigame session story.  The user returned is the user who played the game with the target pet.  The pets array is the list of pets to treat back.  
</aside>




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
  -d "bonusType=silver"
  -d "user=25"
```

> The above command returns JSON structured like this:

```json
{
    "coinBonus": 50
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
user | true | id value of signed in user

<aside class="success">
Returns coin bonus.
</aside>






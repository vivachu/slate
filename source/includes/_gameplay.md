# Game Play

## Initialize the game

```shell
curl "http://api.parade.pet/game/init"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
'entries':
  [{
    "entry_id": 123,
    "image_id": 789,
  }],
  'current_faceoffset': 224789
]
```

This endpoint returns:
  - an array of Entries (including Entry id, Image id) that the current user has not yet seen in a FaceOff
  - the current FaceOffSet, if there is one

### HTTP Request

`GET http://api.parade.pet/game/init`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns array of Pet id values that will be used for future FaceOffs for this user.
</aside>


## Start a new FaceOff

```shell
curl "http://api.parade.pet/game/faceoff/start"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'entryA=123'
  -d 'entryA=456'
  -d 'current_faceoffset=224789'
```

> The above command returns JSON structured like this:

```json
{
  "current_faceoffset": 224789,
  "active_faceoff": 274661
}
```

This endpoint is called at the start of a new FaceOff.

### HTTP Request

`POST http://api.parade.pet/game/faceoff/start`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
entryA | true | id value of Pet entry A
entryB | true | id value of Pet entry B
current_faceoffset | false | id value of current FaceOffSet, if we are in the middle of a set

<aside class="success">
Returns id values for the current FaceOffSet and new active FaceOff.
</aside>


## End a FaceOff

```shell
curl "http://api.parade.pet/game/faceoff/end"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'active_faceoff=274661'
  -d 'winner=123'
```

> The above command returns "OK" or an error message

```
"OK"
```

This endpoint is called at the end of a FaceOff.

### HTTP Request

`POST http://api.parade.pet/game/faceoff/end`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
active_faceoff | true | id value of active FaceOff
winner | true | id value of winning Pet

<aside class="success">
Returns "OK" or an error message.
</aside>

## End a FaceOffSet

```shell
curl "http://api.parade.pet/game/faceoffset/end"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'current_faceoffset=224789'
```

> The above command returns JSON structured like this:

```json
{
  "id": 224789,
  "silverAwarded": 10,
  "goldAwarded": 5,
  "numJudged": 10
}
```

This endpoint is called at the end of a FaceOffSet.

### HTTP Request

`POST http://api.parade.pet/game/faceoffset/end`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
current_faceoffset | true | id value of current FaceOffSet

<aside class="success">
Returns silverAwarded, goldAwarded, numJudged for completed FaceOffSet.
</aside>


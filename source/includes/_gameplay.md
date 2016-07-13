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

This endpoint retrieves the authorized user's active FaceOffSet.  If no FaceOffSet is currently active or all the FaceOffs in the set have been completed then a new FaceOffSet is created and returned.

### HTTP Request

`GET http://localhost:1337/faceoffset/active`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns the active FaceOffSet for the user to begin the game play session.
</aside>


## Get Pet Entries

```shell
curl "http://localhost:1337/entries"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  1, 2, 3,
]
```

This endpoint gets a list of X Pet id values that the current user has not yet seen in a FaceOff.

### HTTP Request

`GET http://localhost:1337/entries`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns array of Pet id values that will be used for future FaceOffs for this user.
</aside>


## Start a new FaceOff

```shell
curl "http://localhost:1337/faceoff/start"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'entryA=123'
  -d 'entryA=456'
  -d 'current_faceoffset_=224789'
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

`POST http://localhost:1337/faceoff/start`

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
curl "http://localhost:1337/faceoff/end"
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

`POST http://localhost:1337/faceoff/end`

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
curl "http://localhost:1337/faceoffset/end"
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

`POST http://localhost:1337/faceoffset/end`

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



## Judge FaceOff

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
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

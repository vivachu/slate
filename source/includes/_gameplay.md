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

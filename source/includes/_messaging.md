# Messaging

## Create Group Message

```shell
curl "https://api.parade.pet/message/group/create"
  -H "Authorization: Bearer meowmeowmeow"
  -d "withUser=123"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2
}
```

This endpoint will create a new group message between two users.

### HTTP Request

`POST http://api.parade.pet/message/group/create`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
withUser | true |  The id of the opponent user that will be joined in the group

<aside class="success">
The newly created message group ID is returned.
</aside>

## Create Message

```shell
curl "https://api.parade.pet/message/create"
  -H "Authorization: Bearer meowmeowmeow"
  -d "messageGroup=1"
  -d "message=Content of the message"
```

> The above command returns JSON structured like this:

```json
{
  "id": 10
}
```

This endpoint will create a new message that belong to a message group.

### HTTP Request

`POST http://api.parade.pet/message/create`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
messageGroup | true |  The id of the messageGroup  
message | false | Content of the message

<aside class="success">
The newly created message ID is returned.
</aside>

## Delete Message

```shell
curl "https://api.parade.pet/message/:id"
  -X DELETE
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
"OK"
```

This endpoint delete a message.

### HTTP Request

`DELETE http://api.parade.pet/message/:id`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  The id of the message  

<aside class="success">
Returns OK
</aside>

## Delete Group Message

```shell
curl "https://api.parade.pet/message/group/:id"
  -X DELETE
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
"OK"
```

This endpoint delete a group message.

### HTTP Request

`DELETE http://api.parade.pet/message/group/:id`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  The id of the group message  

<aside class="success">
Returns OK
</aside>

## Get Group Message

```shell
curl "https://api.parade.pet/messages/messageGroup/:id"
  -H "Authorization: Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "entry": {
      "state": 1,
      "id": 50,
      "image": 136,
      "isAnimated": false
    },
    "sticker": null,
    "message": "Message with entry data but no sticker info.",
    "user": {
      "id": 104,
      "name": "Paula Pickles",
      "profileImage": 713,
      "socialImageUrl": "https://graph.facebook.com/v2.7/10204723564482688/picture?height=100&width=100"
    },
    "timestamp": 12088301.566
  },
  {
    "id": 2,
    "entry": null,
    "sticker": {
      "isAnimated": 1
      "path": "animated_sticker/ladybug"
    },
    "message": "Message with sticker data, but has no entry attached.",
    "user": {
      "id": 104,
      "name": "Paula Pickles",
      "profileImage": 713,
      "socialImageUrl": "https://graph.facebook.com/v2.7/10204723564482688/picture?height=100&width=100"
    },
    "timestamp": 12088196.566
  },
  {
    "id": 7,
    "entry": null,
    "sticker": null,
    "message": "Message without both entry and sticker data",
    "user": {
      "id": 1090,
      "name": "Viva Chu",
      "profileImage": 1301079,
      "socialImageUrl": null
    },
    "timestamp": 238855.566
  }
]
```

This endpoint will returns a list of last 200 messages that belong to a message group.

### HTTP Request

`GET http://api.parade.pet/message/group/:id`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
id | true |  The id of the messageGroup

<aside class="success">
List of last 200 messages from the messageGroup are returned. Each message object has a sender, entry info, path of sticker, message, and timestamp.
</aside>

## Report Message

```shell
curl "http://api.parade.pet/message"
  -H "Authorization: Bearer meowmeowmeow"
  -d "message: 123"
  -d "reason: Inappropiate"
```

> The above command returns JSON structured like this:

```json
"OK"
```

This endpoint report a message.

### HTTP Request

`POST http://api.parade.pet/message/report`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
message | true | The id of the message
reason | true | The reason the user is reporting. Valid reasons: Spam, Inappropiate, Not pet related

<aside class="success">
Returns OK
</aside>




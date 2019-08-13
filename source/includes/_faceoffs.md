# FaceOffs

## Collect XP

```shell
curl "http://api.parade.pet/faceOffs/collectXP"
  -H "Authorization: Bearer meowmeowmeow"
  -d 'faceOffId=1565666813'
  -d 'petId=132045'
  -d 'winner=416769'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint updates the collectXP field in the faceOff cache to 1 for the faceOff retrieved using petId and faceOffId.  It also updates the totalXP field on the user object based on whether the faceOff entry was the winner or loser.

### HTTP Request

`POST http://api.parade.pet/faceOffs/collectXP`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
faceOffId | true | faceOff id from /alerts/faceoffs
petId | true | pet id from /alerts/faceoffs
winner | true | winning entry id from /alerts/faceoffs

<aside class="success">
Returns OK
</aside>

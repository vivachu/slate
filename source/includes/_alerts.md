# Alerts

## Get Treats To Accept

```shell
curl "http://api.parade.pet/alerts/treats"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
	"alerts": [
		{
		  "timestamp": 99749.137,
		  "new": true,
		  "accepted": false,
		  "sender": {
		  	"id": 2912,
		  	"name": "John Snow",
		  	"image": 9287,
			"socialImageUrl": null,
			"pets": [
			  {
				"id": 3089,
				"name": "Grendel",
				"entry": 9728,
				"points": 993,
				"type": "Dog"
			  },
			  {
				"id": 966,
				"name": "Velveteen",
				"entry": 2179,
				"points": 8732,
				"type": "Cat"
			  }
			]		  	
		  },
		  "pet": {
		  	"id": 282,
		  	"name": "Petunia",
		  	"entry": 32192,
		  	"image": 2928,
		  	"points": 9287
		  },
		  "treat": {
			  "accept": 129,
			  "name": "Ribeye",
			  "points": 100
		  }	  	
		},
		{
		  "timestamp": 99749.137,
		  "new": false,
		  "accepted": true,
		  "sender": {
		  	"id": 2812,
		  	"name": "Taylor Swift",
		  	"image": 276,
			"socialImageUrl": "https://graph.facebook.com/v2.7/10211118676179859/picture?height=100&width=100",
        	"pets": null
		  },
		  "pet": {
		  	"id": 958,
		  	"name": "Fluffy",
		  	"entry": 32193,
		  	"image": 28892,
		  	"points": 300
		  },
		  "treat": {
			  "accept": 2982,
			  "name": "Cute Sushi",
			  "points": 100
		  }	  	
		}		
	]
}
```

This endpoint retrieves the list of treats that the pet owner must accept in order to collect points for their pet. Only treats that have not been accepted are returned by this endpoint. Each time this endpoint is called a timestamp is recorded on the backend which is used to determine whether the Alert is new or not.   

### HTTP Request

`GET http://api.parade.pet/alerts/treats`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns an array of Alert objects.  Each Alert has a timestamp, sender, receiving pet, and array of one or more treats. The Sender is the user who sent the treat(s).  The Pet is the receiving pet along with the winning entry that prompted the treat. The image and points are the entry's image and points balance (not the pets).  
</aside>

## Get FaceOff Results

```shell
curl "http://api.parade.pet/alerts/faceoffs"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
	"alerts": [
		{
		  "timestamp": 99749.137,
      "faceOffId": 1565666911,
      "pet": 132045,
      "xpCollected": 0,
		  "new": true,
		  "entryA": {
		  	"id": 282,
		  	"name": "Petunia",
		  	"pet": 32192,
		  	"image": 2928
		  },
		  "entryB": {
		  	"id": 2787,
		  	"name": "Donald",
		  	"pet": 12198,
		  	"image": 4928
		  },
		  "winner": {
		  	"id": 2787,
		  	"points": 10
		  }
		},
		{
		  "timestamp": 99749.137,
      "pet": 132045,
      "faceOffId": 1565666888,
      "xpCollected": 1,
		  "new": false,
		  "entryA": {
		  	"id": 398,
		  	"name": "Petunia",
		  	"pet": 32192,
		  	"image": 2928
		  },
		  "entryB": {
		  	"id": 2787,
		  	"name": "Walton",
		  	"pet": 1219,
		  	"image": 498
		  },
		  "winner": {
		  	"id": 398,
		  	"points": 10
		  }
		},

	]
}
```

This endpoint retrieves the list of FaceOff results for the past 30 days. Each time this endpoint is called a timestamp is recorded on the backend which is used to determine whether the Alert is new or not.   

### HTTP Request

`GET http://api.parade.pet/alerts/faceoffs`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns an array of Alert objects.  Each Alert has a timestamp, entryA, entryB and winner.
</aside>

## Get Comments

```shell
curl "http://api.parade.pet/alerts/comments"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "alerts": [
    {
      "comment": {
        "id": 2572,
        "comment": "Fido eats my socks too"
      },
      "entry": {
        "id": 6280,
        "image": 9998
      },
      "user": {
        "id": 2531,
        "name": "Jacob McGinley",
        "profileImage": null,
        "socialImageUrl": "https://graph.facebook.com/v2.7/10210721727656243/picture?height=100&width=100"
      },
      "timestamp": 99749.137,
      "new": false
    },
    {
      "comment": {
        "id": 2571,
        "comment": "Like crusty time"
      },
      "entry": {
        "id": 6280,
        "image": 9998
      },
      "user": {
        "id": 2531,
        "name": "Jacob McGinley",
        "profileImage": null,
        "socialImageUrl": "https://graph.facebook.com/v2.7/10210721727656243/picture?height=100&width=100"
      },
      "timestamp": 99785.137,
      "new": false
    },
    {
      "comment": {
        "id": 2570,
        "comment": "My cat loves stinky feet"
      },
      "entry": {
        "id": 6280,
        "image": 9998
      },
      "user": {
        "id": 2531,
        "name": "Jacob McGinley",
        "profileImage": null,
        "socialImageUrl": "https://graph.facebook.com/v2.7/10210721727656243/picture?height=100&width=100"
      },
      "timestamp": 99884.138,
      "new": false
    }
  ]
}
```

This endpoint retrieves the list of Comments on entries owned by the authenticated user for the past 30 days. Each time this endpoint is called a timestamp is recorded on the backend which is used to determine whether the Alert is new or not.   

### HTTP Request

`GET http://api.parade.pet/alerts/comments`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns an array of Alert objects.  Each Alert has a timestamp, comment, entry, and user who sent the comment.
</aside>

## Get Prizes and Awards

```shell
curl "http://api.parade.pet/alerts/prizesAwards"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "user": {
    "id": 1090,
    "name": "Viva Chu",
    "profileImage": 11012,
    "socialImageUrl": null,
    "silverTickets": 10,
    "goldTickets": 5
  },
  "alerts": [
      {
            "type": "award",
            "timestamp": 204588.979,
            "new": false,
            "pet": {
                "id": 23658,
                "name": "Pebbles",
                "profileImage": 242840
            },
            "award": "Pebbles won 22nd Place All Pets for the Week of Aug 6, 2017.",
            "ticketAward": {
                "id": 16872,
                "numTickets": 6,
                "isGold": true,
                "opened": true
            }
      },
      {
            "type": "prize",
            "timestamp": 204517.935,
            "new": false,
            "prize": {
                "name": "Grooming Glove",
                "image": "https://images-na.ssl-images-amazon.com/images/I/81eizom38cL._SL600_.jpg",
                "status": "Shipped",
                "statusDetail": "Your order is expected to arrive by 8/15/17."
            }
      },
      {
      "type": "award",
      "timestamp": 234506.893,
      "new": true,
      "pet": {
        "id": 1039,
        "name": "Coder",
        "profileImage": 5981
      },
      "award": "Coder won 8th for the Month of Jan 2017.",
      "ticketAward": {
        "id": 2001,
        "numTickets": 10,
        "isGold": false,
        "opened": false
      }
    },
    {
      "timestamp": 234506.893,
      "new": true,
      "pet": null,
      "award": "You won the \"Most Generous Pet Parent Award\" for the Week of Jan 3, 2017.",
      "ticketAward": {
        "id": 1928,
        "numTickets": 10,
        "isGold": true,
        "opened": false
      }
    }
  ]
}
```

This endpoint retrieves the user object with current ticket balance and a list of Prize alerts awarded to the user for the past 60 days. Each prize alert contains the award text and the ticketAward object to accept.  If the prize box has been opened, then display the alert in the opened state.  If the prize box has not been opened then show the Open button to allow the user to accept the ticketAward.  

### HTTP Request

`GET http://api.parade.pet/alerts/prizesAwards`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns an array of Alert objects.  Each Alert has a timestamp, award, and the profileImage or socialImageUrl of the person or pet who received the award.  If socialImageUrl is not null, use that as the image.   
</aside>

## Get Messages

```shell
curl "http://api.parade.pet/alerts/messages"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "new": true,
    "user": {
      "id": 104,
      "name": "Paula Pickles",
      "profileImage": 713,
      "socialImageUrl": "https://graph.facebook.com/v2.7/10204723564482688/picture?height=100&width=100"
    },
    "timestamp": 3524.368,
    "message": {
      "type": "messageGroup",
      "messageGroup": {
        "id": 1,
        "message": "That's great! Your dog is georgeous",
        "sticker": {
          "state": 1,
          "id": 1070,
          "path": "animated_sticker/ladybug",
          "isAnimated": 1
        },
        "entry": null
      }
    }
  },
  {
    "new": true,
    "user": {
      "id": 166628,
      "name": "007 Pups",
      "profileImage": 1262147,
      "socialImageUrl": "https://graph.facebook.com/v2.7/10212733827974172/picture?height=100&width=100"
    },
    "timestamp": 23955487.368,
    "message": {
      "type": "comment",
      "comment": {
        "id": 1504083,
        "comment": "Thank you",
        "entry": {
          "state": 1,
          "id": 594908,
          "image": 806313,
          "isAnimated": 0
        }
      }
    }
  }
]
```

This endpoint retrieves the a combined list of comments and messages. Each time this endpoint is called a timestamp is recorded on the backend which is used to determine whether the Alert is new or not.

### HTTP Request

`GET http://api.parade.pet/alerts/messages`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns an array of Alert objects.  Each Alert has a timestamp, sender, and message object. Please notice that a message object can be a Comment or a MessageGroup, determined by its "type" property.
</aside>

## Get Alert Settings

```shell
curl "http://api.parade.pet/alerts/settings"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "notifyAnnouncements": false,
  "notifyFaceOffSummary": true,
  "notifyFaceOffSummaryHour": 9,
  "notifyTreatAlerts": false,
  "notifyTreatSummary": true,
  "notifyTreatSummaryHour": 11,
  "notifyCommentAlerts": true,
  "notifyPrizes": true,
  "notifyWeeklyWinners": false,
  "notifyMonthlyWinners": false,
  "notifyCoinPromos": false,
  "notifyPetBirthdays": false,
  "id": 1,
  "user": 104
}
```

This endpoint retrieves the user's alert settings.

### HTTP Request

`GET http://api.parade.pet/alerts/settings`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

<aside class="success">
Returns the user's alert settings.  
</aside>

## Set Alert Settings

```shell
curl "http://api.parade.pet/alerts/settings"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'notifyAnnouncements=false'
  -d 'notifyFaceOffSummary=true'
  -d 'notifyFaceOffSummaryHour=8'
```

> The above command returns JSON structured like this:

```
"OK"
```

This endpoint reports an entry that the user finds questionable.

### HTTP Request

`POST http://api.parade.pet/alerts/settings`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
notifyAnnouncements | false | true or false
notifyFaceOffSummary | false | true or false
notifyFaceOffSummaryHour | false | The hour to send
notifyTreatAlerts | false | true or false
notifyTreatSummary | false | true or false
notifyTreatSummaryHour | false | The hour to send
notifyCommentAlerts | false | true or false
notifyPrizes | false | true or false
notifyAnnouncements | false | true or false
notifyWeeklyWinners | false | true or false
notifyMonthlyWinners | false | true or false
notifyCoinPromos | false | true or false
notifyPetBirthdays | false | true or false

<aside class="success">
Returns OK
</aside>

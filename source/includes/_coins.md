# Coins

## Coins For Sale

```shell
curl "http://api.parade.pet/coins/forSale"
  -H "Authorization:  Bearer meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "gold": [
    {
      "productId": "com.goodboystudios.petparade.gold.pile",
      "name": "Pile of Gold",
      "numGold": 40,
      "numSilver": 0,
      "price": 1.99,
      "id": 7
    },
    {
      "productId": "com.goodboystudios.petparade.gold.bag",
      "name": "Bag of Gold",
      "numGold": 125,
      "numSilver": 0,
      "price": 4.99,
      "id": 8
    }
  ],
  "silver": [
    {
      "productId": "com.goodboystudios.petparade.silver.pile",
      "name": "Pile of Silver",
      "numGold": 0,
      "numSilver": 100,
      "price": 0.99,
      "id": 1
    },
    {
      "productId": "com.goodboystudios.petparade.silver.bag",
      "name": "Bag of Silver",
      "numGold": 0,
      "numSilver": 350,
      "price": 2.99,
      "id": 2
    }
  ]
}
```

Retrieve the list of CoinBundle objects for sale organized by gold and silver.  The productId is the unique app store productId whereas the id is the CoinBundle.id used for the /coins/buy Pet Parade endpoint.    

### HTTP Request

`POST http://api.parade.pet/coins/forSale`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
store | true | Either apple, google, or amazon.

<aside class="success">
Returns CoinBundle objects for sale in the app store organized as two separate arrays silver and gold.
</aside>


## Buy Coins

```shell
curl "http://api.parade.pet/coins/buy"
  -H "Authorization:  Bearer meowmeowmeow"
  -d 'coinBundle=10'
  -d 'receipt=DKSHNE-NSNHE'
  -d 'signature=SIGNED-AHSEKWNNWNBN922k2ndAAJ'
  -d 'transactionId=GPA.0021-2k22-2021-2122'
  -d 'store=google'
```

> The above command returns JSON structured like this:

```json
{
  "goldBalance": 100,
  "silverBalance": 220
}
```

Call this endpoint to inform the server of a successful in-app purchase of coins and to persist the sale record and increment the user's coin balance.  The server verifies the receipt with the specified store (apple, google, or amazon) and increments the user's coin balance.   

### HTTP Request

`POST http://api.parade.pet/coins/buy`

### Header Parameters

Parameter | Required | Description
--------- | ------- | -----------
Authorization:  Bearer meowmeowmeow | true | Replace "meowmeowmeow" with the token of the authenticated user


### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
store | true | Either apple, google, or amazon.
coinBundle | true | The id of the coinBundle purchased.  
receipt | true | The unique sales receipt to verify with the specified store
signature | false | If store is google, then this is the signature for the encoded receipt string
transactionId | false | If store is google, then this is the unique transactionId for the sale

<aside class="success">
Returns the user's coin balance upon success. Returns an error if the receipt is invalid.  
</aside>


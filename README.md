# open_api_en
sirex api service 

[Btrade API Document for Developer]
 

[API Info]
          Btrade provides an API for developers to help them develop a variety of apps and programs.

          Now, with the API provided by Btrade, anyone can easily use features

          such as user information, wallet information, orders, trade history, and order cancellation.

          We also provide Wallet APIs to help build cryptocurrency-related services.

       Generating an API Key (API Key can be generated from the Btrade My page.)
 

 

[API Notice]
Open API Changes Guide
   
   The last trading information API(ticker) on the previous exchange has been deprecated,
   and a Ticker with market information has been added.

 

 

[INDEX]
1. Public API
     1-1. Ticker1        - Final trading information of Btrade Exchange (Deprecated)
     1-2. Ticker2        - Final trading information of Btrade Exchange (Added market information)
     1-3. Orderbook  - Exchange's Sell / Buy order history info

2. Token
     2-1. Create         - Initial Token Generation
     2-2. Refresh       - Refreshing Access Token

3. Private API
     3-1. Account       - View user's Info
     3-2. Balance       - User Wallet Info
     3-3. Transaction - Trade History
     3-4. Cancel         - Cancel Open Orders (Sell / Buy)
     3-5. Place           - Place and Execute orders (Sell / Buy)

4. Status
     4-1. Token Error
     4-2. Exception

 

 

[Reference]
1. Public API
1-1. Ticker - Final trading information of Btrade Exchange (Deprecated)
[GET]    https://api.btrade.co.kr/api/ticker/currency/{coin_code}

[Curl]    curl -X GET --header 'Accept: application/json' 'https://api.btrade.co.kr/api/ticker/currency/{coin_code}'

[Response Body]

{
  "status": "0000",
  "data": {
    "open_price": "10000",
    "close_price": "10000",
    "low": "10000",
    "high": "10000",
    "average_price": "0.0",
    "units_traded": "0E-18",
    "volume_1day": "0E-18",
    "volume_7day": "431.699880000000000000",
    "buy_price": "0000000000.00000000",
    "sell_price": "0000000000.00000000",
    "date": 1548933680756
  }
}
[Input Parameters]

   Parameter Name   	Description
coin_code	               Coin Name (ALL, BTC, ETH, ETC, LTC, ZEC, etc.)               
[Response]

   Response Field   	Description
status: 0000	Normal
open_price	Opening price in last 24 hours
close_price	Closing price in last 24 hours
low	Lowest price in last 24 hours
High	Highest price in last 24 hours
average_price	Average price in last 24 hours
units_traded	                     Currency trading volume in last 24 hours                        
volume_1day	Currency trading volume for the last 1 day
volume_7day	Currency trading volume for the last 7 days
buy_price	Highest buy price in pending orders
sell_price	Lowest sell price in pending orders
date	Current Timestamp
 
1-2. Ticker - Final trading information of Btrade Exchange (Added market information)
[GET]    https://api.btrade.co.kr/api/v1/ticker/currency/{coin_code}

[Curl]    curl -X GET --header 'Accept: application/json' 'https://api.btrade.co.kr/api/v1/ticker/currency/{coin_code}'

[Response Body]

{
    "status": "0000",
    "data": {
        "KRW": {
            "open_price": "1000",
            "close_price": "10001000",
            "low": "1000",
            "high": "10003000",
            "average_price": "8594071.364285713",
            "units_traded": "6.014550000000000000",
            "volume_1day": "6.014550000000000000",
            "volume_7day": "30.019550000000000000",
            "buy_price": "0010001000.00000000",
            "sell_price": "0000000000.00000000",
            "date": 1564475297693
        },
        "BTC": {
            "open_price": "1.12345678",
            "close_price": "1.12345678",
            "low": "1.12345678",
            "high": "1.12345678",
            "average_price": "1.123456780000000000000000000000",
            "units_traded": "2.000000000000000000",
            "volume_1day": "2.000000000000000000",
            "volume_7day": "2.000000000000000000",
            "buy_price": "0000000001.12345678",
            "sell_price": "0000000000.00000000",
            "date": 1564475297863
        }
    }
}
[Input Parameters]

   Parameter Name   	Description
coin_code	               Coin Name (ALL, BTC, ETH, ETC, LTC, ZEC, etc.)               
[Response]

   Response Field   	Description
status: 0000	Normal
open_price	Opening price in last 24 hours
close_price	Closing price in last 24 hours
low	Lowest price in last 24 hours
High	Highest price in last 24 hours
average_price	Average price in last 24 hours
units_traded	                     Currency trading volume in last 24 hours                        
volume_1day	Currency trading volume for the last 1 day
volume_7day	Currency trading volume for the last 7 days
buy_price	Highest buy price in pending orders
sell_price	Lowest sell price in pending orders
date	Current Timestamp
 
1-3. Orderbook - Exchange's Sell/Buy order history info
[GET]    https://api.btrade.co.kr/api/orderbook/currency/{coin_code}

[Curl]    curl -X GET --header 'Accept: application/json' 'https://api.btrade.co.kr/api/orderbook/currency/{coin_code}'

[Response Body]

{
  "status": "0000",
  "data": {
    "timestamp": 1548934145839,
    "order_currency": "BTC",
    "payment_currency": "KRW",
    "bids": [
      {
        "it_action": "buy",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
      {
        "it_action": "buy",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
    ],
    "asks": [
      {
        "it_action": "sell",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
      {
        "it_action": "sell",
        "it_market_cost": "0000000000.00000000",
        "nResCoin": "00000000.00000000"
      },
    ]
  }
}
[Input Parameters]

   Parameter Name   	Description
coin_code	               Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)               
[Response]

   Response Field   	Description
timestamp	Current Time
order_currency	Coin
payment_currency	Payment Currency
it_action	                                  [bids]: buy / [asks]: sell                                  
it_market_cost	Market Price
nResCoin	Available Coin
 

 

2. Token
2-1. Create - Initial Token Generation
[POST]    https://api.btrade.co.kr/api/v1/access_token

{
  "nonce":"1548998552194",
  "hstr":"54c25b135d6e80129b71e399fecf522016ab528be7459b1c33c73730de67fad6",
  "apikey":"BTkYXt3hv5BxzieKxHiE9zovAsDSVXraNpJ",
  "grant_type":"APIKEY",
  "expires_in":60
}
[Curl]

curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' -d '{ \ 
   "nonce":"1548998552194", \ 
   "hstr":"54c25b135d6e80129b71e399fecf522016ab528be7459b1c33c73730de67fad6", \ 
   "apikey":"BTkYXt3hv5BxzieKxHiE9zovAsDSVXraNpJ", \ 
   "grant_type":"APIKEY", \ 
   "expires_in":60 \ 
 }' 'https://api.btrade.co.kr/api/v1/access_token'
[Response Body]

{
  "status": "0000",
  "message": "success",
  "data": {
    "access_token": "fb2050d52602edd7798efff6fd7ed289a8d743a4bdda510e0aa374c50e3b2023",
    "access_token_expire": "1549002045865",
    "refresh_token": "48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7",
    "refresh_token_expire": "1551590445856"
  }
}
[Input Parameters]

   Parameter Name   	Description
nonce	Request Time (Unix Time)
hstr	sha256( apikey + secretkey + nonce ) → Hex converted string
apikey	User API Key
grant_type	APIKEY
expires_in	          Access Token Access Token Expiration Time
                           (Minute Time, min 30 minutes to max 60 minutes)                    
[Response]

        Response Field         	Description
status	0000: Normal / others: error
message	Result Message
access_token	Access Token for Btrade API
access_token_expire	Access Token Expiration Time (Unix Time)
refresh_token	                Refresh Token to refresh your access tokenToken                  
refresh_token_expire	Refresh Token Expiration Time (Unix Time)
 
2-2. Refresh - Refreshing Access Token
[POST]   https://api.btrade.co.kr/api/v1/access_token

{
  "refresh_token":"48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7", 
  "expires_in":60, 
  "grant_type":"REFRESH"
}
[Curl]

curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' -d '{ \ 
   "refresh_token": "48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7", \ 
   "expires_in":60, \ 
   "grant_type":"REFRESH" \ 
 }' 'https://api.btrade.co.kr/api/v1/access_token'
[Response Body]

{
  "status": "0000",
  "message": "success",
  "data": {
    "access_token": "fb2050d52602edd7798efff6fd7ed289a8d743a4bdda510e0aa374c50e3b2023",
    "access_token_expire": "1549002045865",
    "refresh_token": "48f9b90cee15348744b0da1a8e995c5d3833fd985d8f9dd138c04755b18731c7",
    "refresh_token_expire": "1551590445856"
  }
}
[Input Parameters]

   Parameter Name   	Description
refresh_token	                  Refresh Token generated by Token Create API                 
expires_in	Access Token Expiration Time (Minute Time, min 30 minutes to max 60 minutes)
grant_type	REFRESH
[Response]

   Response Field   	Description
status	0000: Normal / others: error
message	Result Message
access_token	Access Token for Btrade API
access_token_expire	Access Token Expiration Time (Unix Time)
refresh_token	                    Refresh Token to refresh your access token                     
refresh_token_expire	Refresh Token Expiration Time (Unix Time)
 

 

3. Private API
3-1. Account - View user's Info
[GET]    https://api.btrade.co.kr/api/private/v1/account?currency={currency}

[Curl]

curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer 125543745d3c2712529a579d1383e89469e3cc9601cd08f22e4dd6c482b5d7b9' 'https://api.btrade.co.kr/api/private/v1/account?currency=BTC'
[Response Body]

{
  "status": "0000",
  "data": {
    "account_id": 3,
    "balance": 5532123.7132,
    "trade_fee": 0.005,
    "created": 1521439134000
  }
}
[Input Header]

   Parameter Name   	Description
Authorization	                              Access Token                              
[Input Parameters]

   Parameter Name   	Description
currency	                  Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)                  
[Response]

   Response Field   	Description
status	0000: Normal / others: error
account_id	User Unique Number
balance	Remaining Coin
trade_fee	Applied Fee Rate
created	                                      Join Time (Unix Time)                                      
 
3-2. Balance - User Wallet Info
[GET]    https://api.btrade.co.kr/api/private/v1/balance?currency={currency}

[Curl]

curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer 7488eeb56b924e369c2d60f738e795072d3e90740339dc42205f50743619cfb4' 'https://api.btrade.co.kr/api/private/v1/balance?currency=BTC'
[Response Body]

{
  "status": "0000",
  "data": {
    "total_krw": 9999613666.0878,
    "in_use_krw": 7598430736.27575,
    "available_krw": 2401182929.81205,
    "total_btc": 5532121.7132,
    "in_use_btc": 8.8742,
    "available_btc": 5532112.839
  }
}
[Input Header]

   Parameter Name   	Description
Authorization	                              Access Token                              
[Input Parameters]

   Parameter Name   	Description
currency	                  Coin Name (ALL, BTC, ETH, ETC, LTC, ZEC, etc.)                  
[Response]

   Response Field   	Description
status	0000: Normal / others: error
total_{currency}	Total Currency
in_use_{currency}	Currency in Use
available_{currency}	                                   Available Currency                                   
 
3-3. Transaction - Trade History
[GET]

https://api.btrade.co.kr/api/private/v1/transaction?currency={currency}&deal_status={deal_status}&trd_state={trd_state}
[Curl]

curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer 7488eeb56b924e369c2d60f738e795072d3e90740339dc42205f50743619cfb4' 'https://api.btrade.co.kr/api/private/v1/transaction?currency=BTC&deal_status=0&trd_state=OK'
[Response Body]

{
  "status": "0000",
  "data": [
    {
      "search": 0,
      "orderId": "1901251726297700000003",
      "price": 3905.5,
      "trd_state": "OK",
      "fee": 0.0015,
      "trd_type": "BUY",
      "units": 0.001,
      "transfer_date": 1548404789817,
      "btc1krw": 3905500
    },
    {
      "search": 0,
      "orderId": "1901151956097700000003",
      "price": 41636.34,
      "trd_state": "OK",
      "fee": 0.005,
      "trd_type": "SELL",
      "units": 0.01019,
      "transfer_date": 1547549769770,
      "btc1krw": 4086000
    },
    {
      "search": 0,
      "orderId": "1901151956026220000003",
      "price": 44828.905,
      "trd_state": "OK",
      "fee": 0.005,
      "trd_type": "SELL",
      "units": 0.01097,
      "transfer_date": 1547549762618,
      "btc1krw": 4086500
    },
    ...
[Input Header]

   Parameter Name   	Description
Authorization	                              Access Token                              
[Input Parameters]

   Parameter Name   	Description
currency	Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)
deal_status	                    Status - 0 (total), 1 (sell), 2 (buy), 3 (cancel), 4 (correct)                    
trd_status	Order Status - OK, WAIT
[Response]

   Response Field   	Description
status	0000: Normal / others: error
search	0 (total), 1 (sell), 2 (buy), 3 (deposit), 4 (withdraw)
orderId	Order Number
price	Trading Amount
trd_state	                    Order Status (OK:Total executed, WAIT:Trading in Progress)                    
fee	Trading Fee
trd_type	Status (BUY: Sell, SELL: Buy, C: Cancel, M: Correct)
units	Trade Currency Amount
transfer_date	Trading Date
{currency}1krw	Usual Market Price
 
3-4. Cancel - Cancel Open Orders (Sell/Buy).
[POST]   https://api.btrade.co.kr/api/private/v1/order/cancel

{
  "currency" : "BTC",
  "org_ord_no" : "190208154943577"
}
[Curl]

curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' --header 'Authorization: Bearer 7603c80ddcd596c6fffb642e44470b9cea0d79e2e67a7b9de9ff5b957d46c1c7' -d '{ \ 
   "currency" : "BTC", \ 
   "org_ord_no" : "190208154943577" \ 
 }' 'https://api.btrade.co.kr/api/private/v1/order/cancel'
[Response Body]

{
  "status": "0000",
  "data": "Success"
}
[Input Header]

   Parameter Name   	Description
Authorization	Access Token
Content-Type	The Content-Type entity header is used to indicate the media type of the resource.
(application/json;charset=UTF-8)
[Input Parameters]

   Parameter Name   	Description
apikey	User API Unique Key
currency	Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)
org_ord_no	Order Number
nonce	Current Date (ex: 20190208)
hstr	                 sha-256(nonce, currency, secretKey, sheckSum)                 
[Response]

   Response Field   	Description
status	                                     0000: Normal / others: error                                   
 
3-5. Place - Place and Execute orders (Sell/Buy).
[POST]   https://api.btrade.co.kr/api/private/v1/order/place

{
  "currency" : "BTC",
  "deal_type" : "B",
  "deal_money" : "10000",
  "amount" : "1",
  "fee_type" : "K"
}
[Curl]

curl -X POST --header 'Content-Type: application/json;charset=UTF-8' --header 'Accept: application/json' --header 'Authorization: Bearer 7603c80ddcd596c6fffb642e44470b9cea0d79e2e67a7b9de9ff5b957d46c1c7' -d '{ \ 
   "currency" : "BTC", \ 
   "deal_type" : "B", \ 
   "deal_money" : "10000", \ 
   "amount" : "1", \ 
   "fee_type" : "K" \ 
 }' 'https://api.btrade.co.kr/api/private/v1/order/place'
[Response Body]

{
  "status": "0000",
  "data": "Success",
  "order_id": "1902081549435770000003"
}
[Input Header]

   Parameter Name   	Description
Authorization	Access Token
Content-Type	The Content-Type entity header is used to indicate the media type of the resource.
(application/json;charset=UTF-8)
[Input Parameters]

   Parameter Name   	Description
currency	                                 Coin Name (BTC, ETH, ETC, LTC, ZEC, etc.)                                    
deal_type	Type of trade (B-Buy, S-Sell)
deal_money	Order Price
amount	Order Amount
fee_type	Fee Type (K-KRW Fee, C-Coin Fee)
* Only KRW fee is available when selling.
[Response]

   Response Field   	Description
status	0000: Normal / others: error
order_id	                                                          Order Number                                                         
 

 

Status
4-1. Token Error
   Status Value   	Description
2001	Member api key is not exist.
2002	INCONSISTENCY HSTR
2003	Refresh Token is not exist.
2004	Access Token is not exist or expired.
2005	No Access Token in Header.
2006	                           IP information has changed. Again create_access_token api call.                           
2007	MEMBER_API_KEY is disabled.
2008	MEMBER API is not authorized.
2009	MEMBER API is not allow ip.
 
4-2. Exception
   Status Value   	Description
0001	Wrong currency entered
0002	Order id is not exist
0003	Price is not correct / Your order price is less than minimum price. (1,000 KRW)
0006	Amount is not correct / Your order amount is exceeded maximum amount
/ Trading unit is not correct / It is already registered to cancel the entire list.
1001	Invalid Parameter
1004	The data does not exist.
2000	No data
3000	Order State Ready
9999	Interval Server Error

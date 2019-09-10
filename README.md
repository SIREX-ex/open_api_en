# [SIREX API Document for Developer]




### [API Info]
          SIREX provides an API for developers to help them develop a variety of apps and programs.

          Now, with the API provided by SIREX, anyone can easily use features

          such as user information, wallet information, orders, trade history, and order cancellation.

          We also provide Wallet APIs to help build cryptocurrency-related services.

####     [Generating an API Key](https://sirex.exchange/mypage/mypage.do?menu=api) (API Key can be generated from the SIREX My page.)



------------------



### [API Notice]

#### Open API Changes Guide
   
         The last trading information API(ticker) on the previous exchange has been deprecated,
         and a Ticker with market information has been added.
         
         
  
------------------



### [INDEX]  

> #### 1. Public API
>> 1-1. Ticker1     - Final trading information of Btrade Exchange (Deprecated)  
>> 1-2. Ticker2     - Final trading information of Btrade Exchange (Added market information)  
>> 1-3. Orderbook   - Exchange's Sell / Buy order history info


> #### 2. Token 
>> 2-1. Create      - Initial Token Generation  
>> 2-2. Refresh     - Refreshing Access Token


> #### 3. Private API
>> 3-1. Account     - View user's Info  
>> 3-2. Balance     - User Wallet Info  
>> 3-3. Transaction - Trade History  
>> 3-4. Cancel      - Cancel Open Orders (Sell / Buy)  
>> 3-5. Place       - Place and Execute orders (Sell / Buy)  


> #### 4. Status 
>> 4-1. Token Error   
>> 4-2. Exception  



------------------



### [Reference]  

#### 1. Public API
> 1-1. Ticker1     - Final trading information of Btrade Exchange (Deprecated)  
#### [GET] 
`https://api.sirex.exchange/api/ticker/currency/{coin_code}`

#### [Curl] 
`curl -X GET --header 'Accept: application/json`
`https://api.sirex.exchange/api/ticker/currency/{coin_code}`

#### [Response Body]
```json
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
```

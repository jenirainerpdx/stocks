# High volume analytics 


We are building an app that will accept requests to buy stocks.  

It will allow the “user” to submit a <b>request</b> to purchase a <b>stock</b> based upon: 
- Stock <b>symbol</b>
- <b>Quantity</b> to purchase
- Purchase <b>price</b>
- <b>Date/time</b> of purchase

We need to feed these <b>transactions</b> to a <b>settlements system</b> to acquire the stock.  We are not concerned with the payment flow, at this time.  We will deal with that later.  (consider using https://www.trade.it/quickstart#get-started#simulation-broker as <b>broker</b>) 

The real purpose of our effort is to aggregate data related to trades.  Anticipate 200,000+ transactions per second.  Every <b>minute</b>, we need to catch a <b>snapshot</b> of each stock symbol.  We want to understand:  <b>minimum, maximum and average bid</b> <i>for that minute</i> and over <i>the lifetime</i> of the application.

Users can <b>query</b> for data related to a stock symbol and get back <b>trend data</b> over time related to stock prices.

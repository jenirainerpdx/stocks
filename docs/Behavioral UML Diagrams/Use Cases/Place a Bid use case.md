Note:  if you find it awkward to author use cases in markdown format, please feel free to use any other means.

| Use Case Name: | Place a bid|  |
|----------------|------------|---|
| Priority: | MVP| |
| Altitude: | 50k feet| |
| Primary Business Actor: | Investor | |
| Primary System Actor: | N/A | |
| Other Participating Actors: | None | |
| Description: | Investor chooses a stock to purchase and places a bid to buy | |
| Trigger: | Investor wants to own stock | |
| *Normative Flow/Happy Path:* | **Actor Action** | **System Response** |
| | 1.  Investor enters stock symbol | -- | 
| | 2.  Investor enters quantity | --|
| | 3.  Investor enters price per share | System updates total amount for quantity of stock and purchase price. |
| | 4.  Investor submits request to purchase | System provides tracking number for transaction request. |
| *Alternative Flows* |
| | 1a.  Investor enters an unrecognizable or otherwise invalid value for stock symbol. | System informs user that the value entered is not a valid stock symbol. Other fields are disabled. |
| | 2a.  Investor enters < 1 for quantity. | System informs user that they must enter a quantity of 1 or more. | 
| | 2b.  Investor enters a quantity that is greater than the amount of stock available on the trading market. | System informs user that the quantity entered cannot exceed the amount of shares currently being traded. |
| | 3a.  Investor enters price per share < $1 | System informs user that the minimum bid price is $1 per share. | 
| | 4a.  Bid application cannot communication with settlements api. | System informs user that bids cannot be placed at this time.  Data is discarded. |


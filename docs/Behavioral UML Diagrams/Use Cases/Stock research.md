| Use Case Name: | Place a bid|  |
|----------------|------------|---|
| Priority: | MVP| |
| Altitude: | 50k feet| |
| Primary Business Actor: | Analyst | |
| Primary System Actor: | N/A | |
| Other Participating Actors: | None | |
| Description: | Analyst wants to evaluate stocks to determine which have best value.| |
| Trigger: | Analyst has identified stock symbols to evaluate. | |
| *Normative Flow/Happy Path:* | **Actor Action** | **System Response** |
| | 1.  Analyst enters stock symbol | -- | 
| | 2.  Analyst enters date range | --|
| | 3.  Analyst submits query | System returns a table that summarizes the minimum bid, maximum bid and average bid, by the minute, for the stock symbol for the duration specified. |
| *Alternative Flows* |
| | 1a.  Analyst enters an unrecognizable or otherwise invalid value for stock symbol. | System informs user that the value entered is not a valid stock symbol. Other fields are disabled. |
| | 1b.  Analyst enters multiple stock symbols for comparative analysis. | System returns data for all stock symbols specified. | 
| | 1c.  Analyst enters more than 5 stock symbols for comparative analysis.  | System informs user that they can specify a maximum of 5 stock symbols at a time for comparative data. |
| | 2a.  Analyst enters a date range that includes days in which the stock was not traded. | System informs user that the stock was not traded on the specific dates as a warning but otherwise displays data. |
| | 2b.  Analyst enters a date range that exceeds 2 months | System informs the user that they can only specify a 2 month date range at a time.  Otherwise they should use the stock 'summary data' | 
| | 2c.  Analyst enters a date range for which the stock was not traded at all.  | System informs user that the stock was not traded for the specified duration and, therefore, no data is available. | 
| | 3a.  Data store service does not respond. | System informs user that the query cannot be completed at this time.  |
| | 3b.  System does not have any data related to the stock symbol. | System returns a 40x status code with message that the data could not be found. | 

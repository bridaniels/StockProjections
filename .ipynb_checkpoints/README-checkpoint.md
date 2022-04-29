# **Stock Projections**
---
Creating Machine Learning Models to Predict Future Stock Prices, Using [Alpha Vantage API](https://www.alphavantage.co/documentation/#)

# Stock Prices: 
---
- Supply of Stock: shares outstanding, or total amount of shares held by investors issued by a company 
- Value directly linked to market capitalization (total valuation of a company, or `(shares outstanding * current share price)`)
- Markets run by humans, thus irrational emotion/bias also factors into price 
- Market Capitalization of a publicly traded firm directly linked to stock price 
- High amount of buyers compared to sellers -> price increase 
- High amount of sellers and few buyers -> price decreases 
- Primary Markets: buying at IPO
- Secondary Markets: Investors selling stocks to one another (aka stock market), prices change rapidly 
- Earnings Calls, Annual Meetings, M&A (suspected or finalized), Media Coverage, Price Trends/Patterns, and Inflation all major contributors 



---
# [Predicting Next Day's Market Price](longShortTermMemory/lstmStockPrices.ipynb) 
#### via: [Long Short-Term Memory (LSTM)](longShortTermMemory)
- Deep Learning Framework
- Recurrent Neural Network
- Supervised Machine Learning
    - use labeled datasets to train algorithms to classify data/predict outcomes 
---


#### Download data using Alpha Vantage API and plot original data 
![PricesTillMarch8](longShortTermMemory/dailyClose/dclose03_08.png "Daily Close Prices through March 8th")


#### Data Preparation: Training vs. Validation
- generate training and validation data sets by normalizing via a Z-Score and splitting the data over a predetermined window_size 
- training data: section of data to train LSTM problem on
- validation data: section of separate data to test LSTM's accuracy 
- z-score: measurement of data point's relationship to the mean -> normalizer 
![TrainValidateMarch8](longShortTermMemory/trainValidate/tv03_08.png "Training and Validation Data through March 8th")


#### DataLoader
- via PyTorch and requires Dataset object 
- Automatic batching through parallelization of the data loading process, leveraging GPU during training. 
- Boosts speed and saves memory in the program.

#### Long Short-Term Memory (LSTM) deep learning framework: 
- Input Modulation Gate = `linear_1`: maps input values into high dimensional feature space
    - transforming features for LSTM layer so non-linear and zero-mean
- Input Gate = `lstm`: learns data in sequence
- Output Gate = `linear_2`: produce predicted value based on LSTM's output 
- Forget Gate = Dropout: randomly selected neurons ignored during training
    - prevents overfitting 
- Model Training: 
    - Loss Function: Mean Square Error of difference between predicted and actual values
    - Bakcpropagation: backtracking to improve predictions 
    - Adam Optimizer: update parameters based on learning rate 
    - StepLR Scheduler: reduce learning rate during training 
- Model Evaluation: 
    - Predict on training data and plot predicted vs. actual data for validation dataset 
![PredictedVsActualMarch8th](longShortTermMemory/predictVsActual/pva03_08.png "Predicted VS. Actual Prices through March 8th")
    - Zoomed-In LSTM Model 
![ZoomedPredictedPrice](longShortTermMemory/zoomIn/zoomed03_08.png "Zoomed-In Predicted Price on Validation Data")


#### Predicting Next Day's Close Price
- using Tensor via PyTorch for unseen data 
- tensor: matrix of data -> turning unseen data into a matrix 
![PredPriceForMarch9](longShortTermMemory/tomorrowPrice/pred03_09.png "Predicted Price for March 9th")
- actual future price: 
![ActualPriceforMarch9](longShortTermMemory/tomorrowPrice/close03_09.png "Actual Close Price for March 9th")




## References: 
- [Tokenist: How are Stock Prices Determined](https://tokenist.com/investing/how-are-stock-prices-determined/)





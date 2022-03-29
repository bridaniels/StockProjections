# **Stock Projections**
Creating Machine Learning Models to Predict Future Stock Prices 

Using [Alpha Vantage API](https://www.alphavantage.co/documentation/#)

---
# [Long Short-Term Memory (LSTM)](longShortTermMemory)
## [Predicting Next Day's Market Price](longShortTermMemory/lstmStockPrices.ipynb) 
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
- actual Future Price
![ActualPriceforMarch9](longShortTermMemory/tomorrowPrice/close03_09.png "Actual Close Price for March 9th")





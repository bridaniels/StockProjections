# **[Predicting Stock Prices with Deep Neural Networks](https://www.alphavantage.co/academy/#ai-for-finance)**
---

# Long Short-Term Memory [(LSTM)](https://www.geeksforgeeks.org/long-short-term-memory-networks-explanation/)
---
- Deep Learning Framework
- Variant of Deep Recurrent Neural Network (RNN)
- Avoids Vanishing Gradient Problem
    - *[Vanishing Gradient Problem:](https://towardsdatascience.com/the-vanishing-gradient-problem-69bf08b15484)* 
        - Issue that sometimes arises when training ML algorithms through gradient descent 
        - Common in neural networks with many layers such as in deep learning
        - Calculated partial derivatives used to compute the gradient get too small
            - Derivatives: change of a function for a given input 
            - Gradient: derivative of a function with multiple input variables (vector) 
            - Gradients small or zero than little to no training of the model can take place 
        - Grdients of the neural network found via *backpropagation*
            - finding derivatives of network moving backwards layer by layer 
    - *[Gradient Descent:](https://www.ibm.com/cloud/learn/gradient-descent) Optimization Technique*
        - minimize the error between predicted and actual (cost function)
            - two data points: direction and learning rate
            - Learning Rate: step size or alpha -> steps taken to reach the minimum 
                - feature values in the model affect step size and skew the LSTM model
            - Direction: Cost Function -> error between actual vs. predicted 
        - requires data to be scaled for LTSM
        - 3 types: Batch, Stochastic, and Mini-Batch 
- Feedback connections to process single data points as well as sequences of data
    - Good at classifying, processing, and making predictions from time-series data 
- Tries to 'remember' all past knowledge from the network and 'forget' irrelevant data 
    - Introducing function layers called **gates**:
        - Forget Gate: what previous data to forget
        - Input Gate: what information to be written onto Internal Cell State 
        - Input Modulation Gate: modulate the information written onto the Internal Cell State
            - make information *non-linear* and *zero-mean*
            - reducing the learning time as the *zero-mean* converges 
        - Output Gate: what output (hidden state) to generate from the current Internal Cell State 
- Similar to workflow of a Recurrent Neural Network, but the Internal Cell State and gate unit is also passed forward with the Hidden State 

    
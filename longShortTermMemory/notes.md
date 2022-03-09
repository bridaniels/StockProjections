

    
    
- Data Normalization: 
    - help gradient descent algorithm converge more quickly 
    - bring input data on the same scale and reduce variance 
        - weights in neural network won't be wasted on normalizing
        - LTSM model can more efficiently learn and store patterns 
    - LTSM sensitive to scale of input data -> faster to noramlize it prior 
    
    
- [Supervised Machine Learning Models:](https://en.wikipedia.org/wiki/Supervised_learning)
    - learning function that maps an input to an output based on IO pairs 
    - learns from specific training data (teacher knows the answers)
    - vecor: input (X variables)
    - supervisory signal: output (Y Variables)
    - generalizes from training data and performs on testing data
    - longer the sequence -> longer the training time 
    
    
- Loss Function: Mean Squared Error
    - step-by-step "loss" values calculated by how well the model is learning 
    - `loss train` tells us how well model is learning 
    - `loss test` tells us how well the model generalizes to the validation dataset
    -  well-trained model will have a training and validation loss that decreases to negligible differences between two values 
        - model has 'converged'
    - loss values usually lower on training than validation dataset 
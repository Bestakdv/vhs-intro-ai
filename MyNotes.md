## Q1. How can different epochs have very different val_loss but very similar val_accuracy?

Loss is the probability so if model is less confident but is still correct the loss will increase while the accuracy stays the same. 
This causes ths val_loss to spike while accuracy remains sames/increases.

## Q2. Explain Binary Cross Entropy Loss Formula
$$\frac{-1}{N}\sum_{i=1}^{N}y_{i}*log(p(y_{i})) + (1-y_{i}) * log(1-p(y_{i}))$$

## Q3. Explain Categorical Cross Entropy Formula. How is this different from sparse categorical cross entropy?




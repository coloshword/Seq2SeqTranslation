## Benchmarking nn.Linear vs nd.Linear in a Sequence To Sequence Machine Translation Model
### Overview
**this is my application to Ensemble AI's ML research intern & ML engineering intern positions** 

- We will be implementing a Sequence To Sequence model for English to Chinese machine translation. 
- The attention mechanism we will be implementing will be Luong Attention, general form, as it makes use of another Linear layer. 
- We will run 2 experiments benchmarking nn.Linear vs nd.Linear:

1. **Performance Benchmarking**
We will compare final performance between the Seq2Seq models using nn.Linear and nd.Linear, keeping model size the same. 

2. **Parameter size analysis**
We will evaluate whether a Seq2Seq model using nd.Linear will perform similarly to the same model architecture using nn.Linear, but with a lower parameter count; specifically, the hidden dim will be 256 in the nn.Linear implementation, vs 192 in the nd.Linear implementation, representing a ~25% reduction in parameter count.
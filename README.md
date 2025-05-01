## Benchmarking nn.Linear vs nd.Linear in a Sequence To Sequence Machine Translation Model
## Overview
**This is my application to Ensemble AI's ML research intern & ML engineering intern positions**

We will develop and benchmark two English → Chinese sequence to sequence translators built on an LSTM encoder decoder with Luong (general) attention.
The models share the same data pipeline, tokenizer, training schedule, and hyper-parameters; they diverge only in the final output linear layer. 

a. In the baseline (nn.Linear) model, we generate a context tensor through the attention mechanism, and concatenate the context tensor to the end of the hidden state tensor. This results in a linear layer with parameters: **nn.Linear(2 * hidden_dim, vocab_size)**. 

- Weights parameter count: $$ 
2 H × V
$$

b. In the NdLinear version, we take advantage of ndLinear's strength for multidimensional inputs, and treat the context tensor as another row, resulting in an input of shape (2, hidden_dim). This results in a linear layer **NdLinear((2, hidden_dim), (1, vocab_size))**, which is **~50%** the parameters of the standard linear layer.
- Weights parameter count:
$$
(2 * 1) + (H * V)
$$


We will benchmark the performance of the standard Seq2Seq model to this augmented model using NdLinear, and see how the smaller NdLinear model performs, compared to the larger standard model. 

### Notes

- notes for the papers

### 1. Paper # 1: Sequence to Sequence Learning with NN's

We use LSTMs to solve general sequence to sequence problems. 

- we use the first LSTM to read input sequences one timestep at a time, which gives us a large fixed-dimensional vector representation (is this the hidden state we are talking about?). This is important I guess because it solves the issue of varible length input which is associated with sequences 

-  reverse the words in the source sentence but not the target sentence -- this allows for some optimization and also learned depedencies. 

- for LSTM's deep LSTM's outperformed shallow LSTM's, (4 layers in the paper)

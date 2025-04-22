### Notes

- notes for the papers

### 1. Paper # 1: Sequence to Sequence Learning with NN's

We use LSTMs to solve general sequence to sequence problems. 

- we use the first LSTM to read input sequences one timestep at a time, which gives us a large fixed-dimensional vector representation (is this the hidden state we are talking about?). This is important I guess because it solves the issue of varible length input which is associated with sequences 

-  reverse the words in the source sentence but not the target sentence -- this allows for some optimization and also learned depedencies. 

- for LSTM's deep LSTM's outperformed shallow LSTM's, (4 layers in the paper)



## Making the model
- 2 LSTM's
- 2 dictionaries (created)
- still need to create 2 nn.Embedding layers, trainable 
- first step, turn token indices into the embedding layer 
- gives you a sequence of dense vectors
- this vector goes into the encoder LSTM, step by step
- final hidden and cell states from the encoder will summarize the input 

2. Decoder:
-  pass chinese tokens into the chinese embedding layer 
- those embeddings go into the decoder LSTM, which is initialized with the encoder's final states 



hidden state:
    - hidden state should follow shape:
        (num_layers, batch_size, hidden_size)
            - num layers (how many stacked LSTM layers, )default is 1
            - batch-size: number of sequences you process at once 
            - hidden_size: this is your hidden_dim. The size of the LSTM's internal representation (what it rememebers) !!It is directly correlated to the value of the LSTM
    
    - nn.LSTM(input_size=128, hidden_size=256, num_layers=1)

        - hidden state should be equal to the hidden size
            lstm = nn.LSTM(input_size=128, hidden_size=256, num_layers=1)
            h_0 = torch.zeros(1, batch_size, 256)


cell_state (c_t): The LSTM's internal memory. It carries long-term information across many timestemps
    - allows the LSTM to learn both short-tterm and long-term dependencies


**In code**
output, (h_n, c_n) = lstm(input, (h_0, c_0))

    - h_n = final hidden state (used for things like initializing the decoder)
    - c_n = final cell state(also passed to the decoder, needed for continuity)

- both can be initialized as 
    h_0 = torch.zeros(num_layers, batch_size, hidden_size)
    c_0 = torch.zeros(num_layers, batch_size, hidden_size)

        - cell_size is the asme as the hidden state 
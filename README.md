# NMT (Neural Machine Translation)
This is an implementation of Machine Translation using Encoder-Decoder Mechanism along with Attention 
The architecture used here uses an encoder that encodes a source sentence into a fixed-length vector from which a decoder generates a translation. Although effective, the Encoder-Decoder architecture has problems with long sequences of text to be translated. Fixed-length vector is a bottleneck in improving the performance of this basic encoder-decoder architecture, which can be solved using an attention mechanism that allows the model to learn where to place attention on the input sequence as each word of the output sequence is decoded.
In this project the translation is from English -> French but, this network can be applied to any other languages given the data.
Encoder.py -> The encoder of a seq2seq network is a RNN that outputs a value for every word from the input sentence. For every input word the encoder outputs a vector and a hidden state, and uses the hidden state for the next input word.

DecoderWithAttention.py -> This is also a seq2seq network but with attention. This additional mechanism allows the decoder network to “focus” on a different part of the encoder’s outputs for every step of the decoder’s own outputs. First we calculate a set of attention weights. These will be multiplied by the encoder output vectors to create a weighted combination. The result (called attn_applied in the code) should contain information about that specific part of the input sequence, and thus help the decoder choose the right output words.
Calculating the attention weights is done with another feed-forward layer, using the decoder’s input and hidden state as inputs. Because there are sentences of all sizes in the training data, to actually create and train this layer we have to choose a maximum sentence length (input length, for encoder outputs) that it can apply to. Sentences of the maximum length will use all the attention weights, while shorter sentences will only use the first few.

#### Run
To run the NMT network run the main.py file.

    'run : python main.py'
This will take the file kept in **data** folder. Default eng-fra.txt. 

In **main.py** enter your input sentence to be translated in source language.

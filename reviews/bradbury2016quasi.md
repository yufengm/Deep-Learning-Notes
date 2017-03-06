# Quasi-Recurrent Neural Networks

James Bradbury, Stephen Merity, Caiming Xiong, Richard Socher, ICLR, 2017

## Summary

RNN's dependence of each timestep's computation on previous ones make it infexible to prallelism. In this paper, the authors proposed a quasi-recurrent neural neworks, which is based convolution & recurrent pooling layers. Their proposed model achieves up to 16 times faster at train and test time, with sota or comparable results on language modelling, sentiment classification and character-level neural machine translation.

- Model/Key points in paper
  - Bank of convolution filters in timestep dimension, R^{T x n} -> R^{T x m}
  - In terms of prediction future words, not given access to future words in convolution window, using masked convolution
  - Additional convolution for input, forgating and output gates, for pooling layers
  - Convolution window of 2 analogous to LSTM block
  - Variants with regularization, dense connection and Encoder-decoder model
    - variational inference-based not allowed as no recurrent weights here
    - zone out mechanism: stochastically choose a subset of channels to be directly transferred to next timestep, can be implemented via dropout on 1-f
    - skip-connection between QRNN blocks, word embeddings and QRNN
    - Encoder-Decoder: append encoder state to every decoder pooling layer to allow encoder state to affect the convolution and pooling gates; soft attention of encoder state for final decoder state encoding

- Dataset
  - IMDb movie review: 25000 positive and 25000 negative
  - Penn Treebank
  - IWSLT German-English: 209772 sentence pairs

- Experiments & Results
  - Sentiment classification: 4-layer densely-connected QRNN with 256 units per layer and 300-dimensional Glove word; Trained with RMSprop with learning rate of 0.001 alpha=0.9 and epsilon=10^-8; 3.2x speedup and interpretable visualization result for intermediate layers;
  - Language modeling: gated QRNN with 2 layers of 640 units in each layer; zoneout for best regularization performance; Trained with SGD without momentum, with L2 regularization; Without zoneout, early stopping is conducted to prevent overfitting; Achieved comparable results with medium LSTM;
  - Character-level neural machine translation: 4-layer encoder-decoder QRNN with 320 units per layer without dropout or regularization; Trained with Adam and decoding is performed with beam search; QRNN outperformed the character-level LSTM and almost matching word-level ones;

## Strengths
  - Extend convolution and pooling mechanism to recurrent structures;
  - With parallelism, great speedup is achieved;
  - Good results with comprehensive experiments on three tasks;
  - Clear diagram for model explanation;

## Weaknesses/Notes
  - It's incremental creation, brand new novlty is lacking; QRNN block is just a mix of various new techniques in different aspects of designing a neural network
  - Notes:
    - Masked convolution for future word prediction, no access to future embeddings;
    - Gating pooling layers is worth learning;
    - RNN regularization: variational inference and zoneout;
    - Densely-connected layer: motivation from skip connection for better gradient flow;
    - Encoder-decoder model: append hidden state of encoder to decoder to make encoder state affect the pooling layer of decoder;
    - Visualization of activations in sentiment classification is really interpretable;
  

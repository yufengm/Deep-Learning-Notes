# Knowing When to Look: Adaptive Attention via A Visual Sentinel for Image Captioning

Jiasen Lu, Caiming Xiong, Devi Parikh, Richard Socher, ArXiv, 2016

## Summary

This paper introduces an adaptive attention based image captioning model. They extended the standard LSTM module with a visual sentinel, which encodes what the whole model already knows. Based on the sentinel, an attention module was attached to learn when to attend to the image feature when generating the captions.

- Model
  - Encoder-Decoder for Image Captioning: ordered conditionals with chain rule; unnormalized log probability with LSTM embedding; 
  - Two kinds of image context encoding: frozen CNN with the last fully connected layer; context is based on both encoder CNN and the decoder RNN with the attention-based framework
  - Spatial Attention Model: k regions of the images along with the hidden state are encoded to calculate the visual attention distribution; based on the attention scalars, image context vector is weighted summed;
  - Adaptive Attention Model: LSTM was extended to produce a visual sentinel vector; this sentinel along with the k region embeddings helped give the adaptive attention distribution

- Dataset
  - Flickr30k with 31783 images, each paired with 5 crowd-sourced captions
  - COCO: 82783, 40504 and 40775 images for training, val and test; Each also has 5 human annotated captions
  - Preprocessing: caption truncation, vocabulary building
  
- Experiments
  - LSTM with hidden size of 512
  - Adam optimizer, finetune CNN after 20 epochs using early stopping
  - Beam search of size 3 when sampling captions
  
## Strengthes

- Besides normally where to look at with visual attention, when to look is also important when the visual sentinel is introduced here.
- LSTM extension with visual sentinel embedding(extend LSTM when required)
- Adaptive attention distribution building

## Weaknesses/Notes

- During preprocessing, captions longer than 18/22(COCO/Flickr30k) were truncated which should be a limitation in real world scenarios. May due to memory restrictions with Torch on GPU?
- They used the current hidden state h_t to guide when to look, which they proposed as stemming from the ResNet design. Not quite understood!

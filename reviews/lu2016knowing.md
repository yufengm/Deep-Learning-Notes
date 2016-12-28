# Knowing When to Look: Adaptive Attention via A Visual Sentinel for Image Captioning

Jiasen Lu, Caiming Xiong, Devi Parikh, Richard Socher, ArXiv, 2016

## Summary

This paper introduces an adaptive attention based image captioning model. They extended the standard LSTM module with a visual sentinel, which encodes what the whole model already knows. Based on the sentinel, an attention module was attached to learn when to attend to the image feature when generating the captions.

- Model
  - Encoder-Decoder for Image Captioning: 
  ``
  $\theta^* $
  ``

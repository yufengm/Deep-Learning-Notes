# Plug & Play Generative Networks: Conditional Iterative Generation of Images in Latent Space

Anh Nguyen, Jason Yosinski, Yoshua Bengio, Alexey Dosovitskiy, Jeff Clune, ArXiv, 2016

## Summary

Based on Activation Maximization approach, authors proposed a plug and play fasion generative network, which can be conditioned on different kinds of supervised neural networka, in order to train the generator more robustly. In terms of the loss function, L_2 reconstruction errora based on abstract features or images are combined with GAN loss to generate images of better quality. Besides, incorporating noise on different levels can result in a little faster mixing speed. In all the models, MALA-approx is used as a sampler.

- Model
  - PPGN-x: include prior p(x) through a DAE, which has no explicit form of p(x), so we may approximate using dlog p(x)/dx \approx (R(x)-x)/sigma^2; (models data distribution poorly, chain mises slowly)
  - DGN-AM: mixing in higher layers can result in faster exploration of the space, thus comes this model; argmax_h P(y_c|G(h)), trained with reconstruction loss, GAN loss, L_2 loss on hidden space h; sampling based on Equa. 10;(mode collapes - may converge to the same mode despite different initialization; poor mixing speed)
  - PPGN-h: incorporating prior p(h) via a DAE; sampling based on Equa. 11; (single MLP DAE poorly models hidden layer fc6 features)
  - Joint PPGN-h: treat G as the decoder in DAE and also train with intermediate layer h_1 of the encoder; Although G+E is pretty much like an DAE, there is neither noise added nor L2 reconstruction error for h; Thus it's not a theoretical formal h-DAE; Trained with reconstruction error for h, x, h_1, which may push G to generate more robust results, and GAN loss for x; Noises are added to x, h, and h_1;
  - Ablation study: noise sweep; different combination of losses, feature matching of h_1 gives best image quality
  - Noiseless Joint PPGN-h: h_1, x reconstruction loss and GAN loss;
  
- Dataset
  - ImageNet with 1000 classes;
  - MIT Places with 205 categories;
  - MS-COCO for image captioning; 
  
- Experiments
  - PPGN with different kinds of priors for p(x) and p(h);
  - Condition network from training E to another test C network;
  - Change condition network with LRCN for image captioning;
  - Inpainting experiment for image repair, besides Eq.11 sampling, addition operation with Eq.12;

## Strengths
  - Change the traditional Discriminator into a class specific classifier for conditioning is worth trying;
  - Extremely complete experiments with different prior modelling for h, h_1 and x via DAE;
  - Activation Maximization for neurons besides the outputs is also very useful for DNN's layer understanding;

## Weaknesses/Notes
  - Equation. 6 for approximation of gradients to log probability when trained with Gaussian is worth noting;
  - As for MALA based sampling, models with implicit p(x) can use DAE for modeling in this respect;
  - Normally, GAN can result in mode collapse to model distribution, L2 reconstruction error can push it apart from p_model(x);
  - In a supervised manner, h captures semantically meaningful codes behind for expressing images or other kind of data;
  - Plug and Play fashion for training;

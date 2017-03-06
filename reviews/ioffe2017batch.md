# Batch Renormalization: Towards Reducing Minibatch Dependence in Batch-Normalized Models

Sergey Ioffe, ArXiv, 2017

## Summary

In terms of dependence of models layers w.r.t. the training examples in a minibatch, the computation in training and testing will be different as the latter uses statistics of running averages instead of the minibatch. So the auther proposed Batch Renormalization, which ensures that output of each example during training and testing are dependent only on its own. Such models can converge faster with competing results, and perform substantially better than BN with small or non-i.i.d. minibatches.

- Model/Key points in paper
  - BN reduces internal covariate shift: gradient descent based approach updates parameters under the assumption that other layers are kept the same, but we update parameters simultaneously which can result in that first order gradient is not enough for accomodating the change; With normalized layer, current layer does not need to account much on previous ones, which alleviate the gradient exploding or vanishing; Like the intuition given in paper from looking at the the gradients, with BN, the norm of gradients is always the variance of the loss function in the though experiment. This really helps to solve the gradient vanishing or exploding problem.
  - (x_i - mu) / sigma = ( x_i - mu_B ) / sigma_B * r + d, where r = simga_B / sigma, d = (mu_B - mu) / sigma: affine transform on top of batch norm can tranform it to the one used in inference model;
  - BRN: r and d are retained and fixed as constant within one minibatch for gradient computation; it helps to correct for the fact that the minibatch statistics differ from the population ones, and allow layers during training to observe the correct statistis/activations in inference;
  - Moving average is updated using exponentially-decayed rule based on each minibatch;
  - In practice, r & d are set to 1 & 0 respectively during first certain # of iterations and then gradually relaxed;
  - Interpretation of BRN from gradient equations: scale and null-space projection; allows using moving average mu and sigma in traing by using extra projection in backprop;

- Dataset
  - ImageNet training and validation dataset

- Experiments & Results
  - Baseline: batchnorm with minibatch size of 32; normalized within minibatch but gradients are aggregated over the whole minibatches; Top-1 accuracy of 78.3%;
  - Small minibatches: split minibatch of 32 into ones of 4; BRN achieves 76.5% vs 74.2% with BN, still not as good as larger minibatch normalization size;
  - Non-i.i.d. minibatches: metric learning needs sampling with dependencies; sample with replacement of 16 labels out of 1000, each with 2 images; Training accuracy (72.8%) of BN are much smaller than in i.i.d. case, which may be due to overfitting; Verify using statistics of test minibatches instead of moving averages, which present better acc (76.5%); Reduce dependence via half the minibatches, which is more i.i.d. with each minibatch (77.4%); BRN achieves 78.5% which is the same as i.i.d. minibatches;
  
## Strengths
- Good extention of Batch Normalization to BRN, which makes computation of each individual example in training and testing quite the same.
- Exponential decay rule for updating the moving average;
- Faster convergence and better performance compared wit BN;
- *Experimental design of i.i.d. test is quite worth learning;
  
## Weaknesses/Notes
- Extension to RNN?
- Not quite understand the Null space projection explanation;

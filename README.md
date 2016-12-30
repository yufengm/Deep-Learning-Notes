Summary of Papers on Deep Learning

2017

- Knowing When to Look: Adaptive Attention via A Visual Sentinel for Image Captioning [[Paper](https://arxiv.org/abs/1612.01887)] [[Review](https://github.com/yufengm/Papers/blob/master/reviews/lu2016knowing.md)]
  - Jiasen Lu, Caiming Xiong, Devi Parikh, Richard Socher, ArXiv, 2016
- Hierarchical Question-Image Co-Attention for Visual Question Answering [[Paper](https://arxiv.org/abs/1606.00061)] [[Review](https://github.com/yufengm/Papers/blob/master/reviews/lu2016hierarchical.md)]
  - Jiasen Lu, Jianwei Yang, Dhruv Batra, Devi Parikh, NIPS, 2016

Review of Deep Learning Book

- Chapter 6: Deep Forward Networks
  - Why ReLU and its generalization
  - Chain rule and Backpropagation
  - Dynamic programming for backpropagation in order to avoid repeating subexpression computing
  - Reverse and forward mode accumulation, Krylov methods
- Chapter 7: Regularization for Deep Learning
  - L^2 regularization analysis of eigenvalues of Hessian matrix to cost function J: high eigenvalue with high curvature of function -> high change of gradient -> weight decay along this direction will affect little;
  - L^1 norm results in sparsity which can be interpreted as feature selection;
  - Constrained optimization with reprojection, which can help prevent numerical overflow if the weights continue to increase; it is also recommended by Hinton that in this way we can enable rapid exploration of parameter space given high learning rate;
  - Underdetermined problems like X^TX is not invertible for linear regression: regularization can be employed here;
  - Data augmentation is particularly effective for object recognition; injecting noise into input or hidden units is also helpful provided that noise magnitude is carefully tuned;
  - Besides adding noise to input, weight noise can also be manipulated: Bayesian inference or stability of function; label smoothing with injecting noise at the output targets; (not quite understand small eta part with an additional regularization term)
  - Semi-supervised learning: combine -log P(X) and -log P(Y|X); multitask learning with shared representation;
  - Early stopping: limiting the searching of parameter space - alpha = 1 / ( tau * epsilon )
  - Parameter sharing: CNN or Tying: regularize parameter of one model to be close to another
  - Place sparse representation on hidden units besides L1 for feature selection like parameter restrictions;
  - Bagging and boosting techniques: Dropout as a bagging strategy - \sum p(\mu)p(y|x, \mu) [it may be more preferable to use geometric mean as compared with arithmetic mean here]; Exact inference when no nonlinear hidden units exists - see the example with softmax regression;
  - Adversarial Training: due to excessive linearity; with adversarial examples to train NN to resist local perturbation.
  - Tangent Prop vs Data augmentation - Double backprop vs Adversarial training

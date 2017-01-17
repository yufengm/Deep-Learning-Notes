# Stochastic Multiple Choice Learning for Training Diverse Deep Ensembles

Stefan Lee, Senthil Purushwalkam, Michael Cogswell, Viresh Ranjan, David Crandall, Dhruv Batra, NIPS, 2016

## Summary
Typically, single prediction rarely exists in practical modern systems. The prediction results are always followed by selection or oracle mechanisms that can choose the right option. So in this paper, they propose to demonstrate Multiple Choise Learning's importance and introduced sMCL, which can use SGD to train ensembel models without having to provide extra parameters and is agnostic to loss function and underlying architectures.

- Model
  - L_o(D) = \sum_{i=1}^n \min_{m\in [M]} l(y_i, f_m(x_i)) - oracle loss function over the whole dataset D;
  - Minimization: introducing k-means like strategy for hard-assignment of whether the ensemble has the lowest error on example i; Reference [8] applied coordinate descent, i.e., k-means like of hard-EM for optimizatio, which alternates between assigning examples to the min-loss and convergence of partition of examples. This methodology is not feasible for deep networks as single model takes weeks to train;
  - \frac{L_o}{f_m(x_i)} = p_{i,m}\frac{l(y_i, f_m(x_i))}{f_m{x_i}}, in which p_{i,m} only equals to 1 when f_m is the min error predictor. In that case, we can just step forward as training a single model
- Dataset
  - CIFAR-10 for Image Classification
  - Pascal VOC dataset for Semantic Segmentation
  - MSCOCO dataset for Image Captioning
- Experiments
  - Compared with Classical ensembles in which each model is trained independently; MCL in [8]; Models trained sequentially in a boosting-like fashion; Oracle Evaluation under proposed model;
  - Image classification: accuracy from 75% to 95%; 5x faster; Interpretable Expertise under sMCL like some member becomes specialist for some classes;
  - Semantic Segmentation: FCN as base model; class-averaged IoU(Intersection over Union); Again see some members are better at segmenting some categories.
  - Image captioning: beam search; CIDEr-D score for measurement; Generated captions are not similar anymore; 

## Strengthes
- Apply hard-EM or k-means like strategy to SGD-based training deep networks is really awesome, which can inspire lots of powerful ensemble models in the future as training process is alleviated.
- Lots of comparison experiments done to prove sMCL's effectiveness.

## Weaknesses/Notes
- The idea in this paper is good but the maths behind is short as written in the paper although they provide clear statement of how they work; So this paper is better considered an engineering design paper instead of principle derivation;
- It's good to borrow ideas from like hard-EM or k-means unsupervised methods;

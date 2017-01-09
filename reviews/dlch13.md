Chapter - Linear Factor Models
- Probablistic model p_model (x) = E_h p_model(x|h)
- x = Wh + b + noise;
- Probablistic PCA and Factor Analysis
  - factor analysis - h follows unit variance normal distribution, x_i are conditionally independent given h with noise drawn from diagonal covariance Gaussian distribution;
  - probablistic PCA - conditional variance are equal to each other, when it becomes zero comes the exact PCA;
- Independent Component Analysis: latent variables h are independent to each other like the mirophone example depicted in P482; prior P(h) should be non-Gaussian, otherwise W will not be identifiable; nonlinear ICE; learn groups of features, while in group features can have dependence
- Slow Feature Analysis: slowness principle - important characteristics of scenes change very slowly compared to the individual measurements that make up a description of a scene, difference between two time steps is slow, with zero mean and unit variance, linearly decorrelated; theoretically predictable;
- Sparse Coding: linear factors with Gaussian noise with isotropic precision beta, prior h is chose to be one with sharp peaks around zero like laplace and student t-distribution; often produce poor samples - factorial prior includes random subsets of all the features;
- Manifold Interpretation of PCA: flat region manifold as learned from pancake-shaped region

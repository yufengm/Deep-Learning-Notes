# Wasserstein GAN

Martin Arjovsky, Soumith Chintala, Léon Bottou, ArXiv, 2017

## Summary

Instead of applying Jensen-Shannon divergence in the canonical form of GAN training, this paper proposed to use Earth-Mover distance or Wasserstein distance to measure the distance between real and model distributions, which sidesteps saturate gradient during training and results in samples generated with higher visual quality. Moreover, loss can be correlated with sample quality as shown in the first time to their best knowledge and no mode collapse problems are observed in generated samples.

- Model/Key points in paper
  - Various measures of how close are the model and real distributions
    - Total Variance distance
    - KL-divergence
    - Jensen-Shannon divergence
    - Earth-Mover distance / Wasserstein-1
  - The Example 1 shows only EM distance can converge over low dimensional manifold as other metric loss function is not continuous and differentiable everywhere.
  - GAN only proves p_g converges to p_data if p_g is updated as a whole given optimal D(x); But in practice, we are optimizing based on parameter theta, for which in this paper they provide the proof for EM distance;
  - KL convergence -> TV distance & JSD -> EM distance;
  - By KR duality, intractable infimum in EM distance can be dealt with by supremum as in Equation 2 with 1-Lipschitz functions;
  - Through proof of Theorem 3, we can define optimization algorithm for EM distance based GAN as in Algo 1; In order to restrain parameters w in compact spaces, clamping is applied. Critic function should be trained till optimality before turning into generator tuning.

- Dataset
  - LSUN-Bedrooms dataset

- Experiments
  - EM distance loss explaination: correlation with sample qualities;
  - During training, JS distance can saturate easily when the discriminator has learnt to distinguish between real and fake, thus giving zero-approaching gradients.
  - WGAN can become unstable if trained with momentum or high learning rate;
  - WGAN is more robust to architecture variance as demonstrated by MLP, DCGAN, etc. components;

## Strengths
  - Gradients never get saturated during training as the loss function has piece-wise linear properties;
  - Stronger proof as compared with the classical GAN for function of the parameters; It proves continuous on theta and differentiable for parameter update;
  - Theoretical math proof is really awesome in this paper;

## Weaknesses/Notes
  - Experiments with dataset is so limited that only one data category is played on;
  - Normally, in MLE form/KL divergence measure we will need the model density P_theta to be existed, which is not the case with distributions of low dimensional manifolds; That's why we may need to add some noise components in classical generative models of ML literatures; Alternatively, we can define a random variable z with some fixed distributions and pass it through some parametric function to form the distribution P_theta, which is taken be VAE and GAN;
  - Design loss functions that can provide non-saturated gradients is very important, as with the emergence of ReLU for nonlinearity in deep nets;

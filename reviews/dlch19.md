Chapter 19 - Approximate Inference
- Inference as Optimization: evidence lower bound formed from KL divergence; As D_KL >=0, L can be a lower bound of MLE for p;
- Expectation Maximization: learning with approximate posterior q, as an approximation for p; coordinate ascent; 
  - E-step: q(h|v) = p(h|v; \theta_t)
  - M-step: maximize L w.r.t. to current q(h|v)
  - Stochastic Gradient Ascent: special case of EM; based on current prediction, we update parameters
  - Gap from L and true log p(v): in M-step same q is applied for all values of parameter theta
- MAP inference and Sparse coding
  - During maximizing L: use MAP to provide q; restrict q to take on Dirac Distribution, L = log p(h=mu, v) which is equivalent to MAP inference; MAP for infering h and update theta for maximing L;
  - Sparse Coding: laplace for p(h) and Gaussian for p(v|h) - posterior is intractable, turn to MAP with Dirac Distribution; 
- Variational Inference and Learning: maximize L over a restricted family of q, which makes it easy to compute E_q log p(h,v): common approach is mean field which assumes that q is a factorial distribution; The beauty behind is that we don't need to specifiy the specific distribution as it can be learnt automatically. All we need is to specify how it is factorized; Difference between D_kl(q|p) and D_kl(p|q) - D_kl(p|q) encourages q to be high on where p is high while D_kl(q|p) encourages q to be low on where p is low.
  - Discrete Latent Variables: each factor of q is like a lookup table over discrete states; fixed point equations for optimization over h; 
    - Binary Sparse Coding Model example!(really good for understanding why variational learning is suitable); h_i is just like a recurrent neural network; reformulation of 19.44 into 19.45, we can see a autoencoder like form neural network;
  - Calculus of Variations: functional derivatives; optimize a functional with an optimum function; maximum entropy example with the optimum pdf - apply constraints with lagrangian multipliers, we can get the form of p(x), which is derived automatically without prior specification of distributions; no specific function achieves minimal entropy;
  - Continuous Latent Variables: with mean field assumption, q always has the form of 19.56, in which we can apply fixed-point equation; see example for how calculus of variations can be applied; again we see a form of Gaussian of p(h|v) without assuming its distribution type;
  - Interactions between Learning and Inference
- Learned Approximate Inference: we may think of the multistep process as being function, then we can use a neural network to approximate f;
  - Wake-sleep speculation: MC assumes that samples drawn from p(h,v) for dream sleep, while here samples are drawn from p(h,v);
  

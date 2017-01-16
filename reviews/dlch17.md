Chapter 17 - Monte Carlo Methods
- Sampling to reduce computation cost or speedup; Basics of MC sampling: view sum or integral as expectation and approximate it by a corresponding average; Empirical average is unbiased and can converge to the expected value provided that variance is bounded; Can also use CLT to estimate confidence intervals;
- Importance Sampling: p(x)f(x) = q(x) p(x)f(x)/q(x), and biased importance sampling with unnormalized p and q;
- MCMC methods: p(a|b) and p(b|a), a chicken-and-egg problem; can use ancestral sampling; 
  - work with EBM, Markov Chain defined by a random state x and a transition T(x'|x) and we also should have an initial distribution q^0;
  - v^(t) = A v^(t-1): eigenvalue decomposition analysis; burning in and mixing; 
- Gibbs Sampling: sample T(x'|x) from P(x_i|x_-i) in undirected models; and we may only rely on its neighbors; Block Gibbs Sampling if we can update simultaneously; after x transitted to x', we may update the current state;
- Challenges: difficult to mix between separated modes like the EBM example in P592; In deep models, learning p(x|h) and p(h|x) are at odds with each other;
  - Tempering with exp(-\beta E(x));
  - Add more depth to help mixing;
  
Notes: needs to really understand the sampling mechanism, especially for Gibbs Sampling

# Label-Free Supervision of Neural Networks with Physics and Domain Knowledge

Russell Stewart, Stefano Ermon, AAAI, 2017, Outstanding paper award

## Summary

Deep neural networks with supervised learning has achieved great success with labeled dataset of high volume. But in order to get such dataset, it is usually quite expensive. In this paper, the authors transformed classical supervised learning with labels to learning with constraints on top of predicted outputs. Such conditions can come from prior domain knowledge or laws of physics. Such approaches are demonstrated on real world and simulated computer vision tasks like object detection and tracking.

- Model
  - Normally, prior knowledge is incoporated as a regularization term in the loss function;
  - Here, X x Y -> R is used as prior knowledge for constraints and the sufficiency of such form is explored in the paper for three real world computer vision tasks;
  - If fortunate enough, optimizing Equ. 2 (Sufficient enough) can be solved via SGD, which frees us from ground truth labels; Otherwise, we may add additional regularization terms;
  - Object Tracking in free fall: elementary physics of free falling objects under the impact of gravity; Equ.3 is a necessary condition that the precdited trajectory should satisfy;
  - Position tracking of walking man: constant velocity assumption condition, yet not sufficient for convergence; add greater standard deviation of values, restrict output to be within some fixed range;
  - Object detection with causal relationship: y_1 => y_2, i.e., Mario will always appear whenever Peach appears; Transformation invariance with h_1, high standard variance with h_2, and high entropy outputs with h_3

- Dataset & Experiments
  - Own collected data for free fall object tracking;
  - Previously collected data where constant velocity assumption hold for tracking of walking man
  - Images containing a stochastic collection of up to 4 characters for object detection

## Strengths
  - Great extension from standard supervised learning of neural networks to constraint learning, and showed some sufficiency analysis for convergence research;

## Weaknesses/Notes
  - Kind of weak for mathematical analysis of necessity and sufficiency for convergence;
  - Datasets are all own collected, which is a little bit weak. It's kind of toy dataset. Might show stronger results if experimented with larger and public datasets;
  - It's really good idea to bring in constraints as the target instead of exact ground truth labels. It's worth noting for all other future problems.

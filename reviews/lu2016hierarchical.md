# Hierarchical Question-Image Co-Attention for Visual Question Answering

Jiasen Lu, Jianwei Yang, Dhruv Batra, Devi Parikh, NIPS, 2016

## Summary
This paper introduced the co-attention model based hierarchical question embeddings, in which both image and question attention are learned to interpret the scenario and beste answer the question. The co-attention model is implemented through both parallel and sequential version, and both of them have their own advantages. The hierarchical question embedding, which involves conv and pooling to learn n-gram invariant features, is really worth reading!

- Model
  - Question Hierarichy: end-to-end learnt word vector; n-gram conv & pooling for phrase embedding; LSTM on top of phrase level vector for question level embedding;
  - Parallel Co-Attention: C = tanh( Q^T W_b V ) as affinity matrix, max pooling over locations among other modality (simple way); treat C as a feature then use C to transform attention space between question and images;
  - Alternating Co-Attention: H = tanh( W_x X + (W_g g)1^T ), X is V or Q alternatively as we move along the question; 
  - Treat VQA as a classification problem, recursively combine word, phrase, and question level together to predict answer
- Dataset
  - VQA: 248349 training questions, 121512 validation questions, 244302 testing questions; sub-category question types like yes/no, number, and other;
  - COCO-QA: automatically generated from captions of MS-COCO; 78736 train question and 38948 test questions, which are based on 8000 and 4000 images; 4 types of question including object, number, color and location; Ansers are all single word;
- Experiments
  - Torch implementation with Rmsprop optimizer;
  - Hidden size of W_s is 512 for COCO and 1024 for VQA;
  - Last pooling layer of VGGNet and ResNet for image features;
  - Ablation Study: replace each component with uniform distribution to quantify the role of the component;

## Strengthes
- Really like the Co-Attention idea here, which mimics the mechanism of people looking at both images and sentences to select out both highlights and combine them to infer;
- Hierarchical embedding of question is also awesome. As conv & pooling is for learning features that are invariant to some kinds of transformations, this idea can be borrowed in NLP to learn invariant n-gram features that are most suitable for target inference;
- Lots of baseline experiments are done for comparison, which provide solid foundations;
- Ablation study is also an important concept for future reseach;

## Weaknesses/Notes
- Some misleading equation expressions like in equation (4), the dimensions between factor matrices are not compatible;
- Also in this section, they only provide result saying that performance is improved but without why behind? Any principle or design science behind?

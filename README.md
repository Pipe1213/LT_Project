# Self-Supervised Dataset Distillation for Transfer Learning
This is the Pytorch implementation for the paper ["**Self-Supervised Dataset Distillation for Transfer Learning**", in ICLR 2021.](https://openreview.net/forum?id=h57gkDO2Yg)

## Abstract
<img align="middle" width="1000" src="https://github.com/db-Lee/selfsup_dd/blob/main/assets/concept.png">
Dataset distillation aims to optimize a small set so that a model trained on the set achieves performance similar to that of a model trained on the full dataset. While many supervised methods have achieved remarkable success in distilling a large dataset into a small set of representative samples, however, they are not designed to produce a distilled dataset that can be effectively used to facilitate self-supervised pre-training. To this end, we propose a novel problem of distilling an unlabeled dataset into a set of small synthetic samples for efficient self-supervised learning (SSL). We first prove that a gradient of synthetic samples with respect to a SSL objective in naive bilevel optimization is biased due to the randomness originating from data augmentations or masking for inner optimization. To address this issue, we propose to minimize the mean squared error (MSE) between a model's representations of the synthetic examples and their corresponding learnable target feature representations for the inner objective, which does not introduce any randomness. Our primary motivation is that the model obtained by the proposed inner optimization can mimic the self-supervised target model. To achieve this, we also introduce the MSE between representations of the inner model and the self-supervised target model on the original full dataset for outer optimization. We empirically validate the effectiveness of our method on transfer learning.





__Contribution of this work__
- We propose a new problem of \emph{self-supervised dataset distillation} for transfer learning, where we distill an unlabeled dataset into a small set,  
    pre-train a model on it, and fine-tune it on target tasks. 
- We have observed training instability when utilizing existing SSL objectives in bilevel optimization for self-supervised dataset distillation. Furthermore, we prove that a gradient of the SSL objectives with data augmentations or masking inputs is \emph{a biased estimator of the true gradient}.
- To address the instability, we propose \textbf{KRR-ST} using MSE without any randomness at an inner loop. For the inner loop, we minimize MSE between a model representation of synthetic samples and target representations. For an outer loop, we minimize MSE between the original data representation of the model from inner loop and that of the model pre-trained on the original dataset. 
- We extensively validate our proposed method on numerous target datasets and architectures, and show that ours outperforms supervised dataset distillation methods.

# K-LITE: Learning Transferable Visual Models with External Knowledge
Shen, S., Li, C., Hu, X., Xie, Y., Yang, J., Zhang, P., Rohrbach, A., Gan, Z., Wang, L., Yuan, L., Liu, C., Keutzer, K., Darrell, T., & Gao, J. (2022). K-LITE: Learning Transferable Visual Models with External Knowledge. https://doi.org/10.48550/arxiv.2204.09222

https://arxiv.org/abs/2204.09222

## Abstract
Recent state-of-the-art computer vision systems are trained from natural
language supervision, ranging from simple object category names to descriptive
captions. This free form of supervision ensures high generality and usability
of the learned visual models, based on extensive heuristics on data collection
to cover as many visual concepts as possible. Alternatively, learning with
external knowledge about images is a promising way which leverages a much more
structured source of supervision. In this paper, we propose K-LITE
(Knowledge-augmented Language-Image Training and Evaluation), a simple strategy
to leverage external knowledge to build transferable visual systems: In
training, it enriches entities in natural language with WordNet and Wiktionary
knowledge, leading to an efficient and scalable approach to learning image
representations that can understand both visual concepts and their knowledge;
In evaluation, the natural language is also augmented with external knowledge
and then used to reference learned visual concepts (or describe new ones) to
enable zero-shot and few-shot transfer of the pre-trained models. We study the
performance of K-LITE on two important computer vision problems, image
classification and object detection, benchmarking on 20 and 13 different
existing datasets, respectively. The proposed knowledge-augmented models show
significant improvement in transfer learning performance over existing methods.

## Highlights
Extensions with Modularized Modeling. In our study, we found it is key to ensure consistency between training and evaluation stages: if a model is trained with knowledge, the model is favored to be evaluated with knowledge. Similarly, if a model is trained without knowledge (e.g., CLIP/UniCL), adding knowledge directly in the evaluation stage results in a performance drop. However, due to the limited knowledge coverage in existing knowledge bases, s could be empty for a large number of queries q. When the low coverage happens for a downstream evaluation dataset, we hypothesize that it may result in a train-evaluation inconsistency for our knowledge-augmented models, and thus lower performance.
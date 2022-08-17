# Domain adaptation with multi-modal embeddings

## Field

While huge volumes of unlabeled data are generated and made available in many domains, the cost of acquiring data labels remains high. To overcome the burden of annotation, alternative solutions have been proposed in the literature in order to exploit the unlabeled data (referred to as semi-supervised learning), or data and/or models available in similar domains (referred to as transfer learning). The performance gain of transfer learning is determined by generalizability of learned representations across different domains. Domain Adaptation (DA) is a particular case of transfer learning (TL) that leverages labeled data in one or more related source domains, to learn a model for unseen or unlabeled data in a target domain. One of the most prevalent domain adaptation technique is to minimize discrepancy between source and target domains.

Recently, there have been breakthroughs in computer vision models that are more generalizable with the advent of models such as CLIP and ALIGN. We'll refer these models as self-supervised language vision models (SSLVM). These type of models are composed of image encoder and text encoder. They are trained on web-scale dataset consisting of image-text pairs with contrastive loss. After pre-training, natural language is used to reference learned visual concepts enabling zero-shot transfer of the model to downstream tasks. They achieve comparable performance on many vision benchmarks to fully supervised alternatives. It's been also shown that their performances improve further with few-shot learning. 
Zero-shot image generation model DALL-E, which is built upon CLIP, has been shown to understand abstract, unseen or imaginary concepts. Hence, it is stated that SSLVM produce generalizable representations that reflect compositionality proporty of language.

Two main limitations of these models are observed as:
1. They perform poorly on very specific domains and tasks, similar to non-expert human labellers. 
2. They require finding the best performing prompt for a task, also known as prompt-engineering.

How these representations can be leveraged to adapt an existing task-specific model is an open research area.

## Proposal

In this thesis, new techniques will be explored to leverage capabilities of such large multi-modal pretrained models for domain adaptation. We hypothesize that the representations produced by these models contain world knowledge which can be utilized for adapting task-specific models. For instance, an image-segmentation model trained on day-time images can be adapted to night-time images by using the embeddings from SSLVM representing this domain shift. Human generated or learned prompts or combination of them can be used for this manner.
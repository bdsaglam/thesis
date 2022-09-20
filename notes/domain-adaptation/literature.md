
## Unsupervised Domain Adaptation by Backpropagation
TLDR: Minimize classification loss, maximize domain discrimination loss

## Adversarial Discriminative Domain Adaptation
TLDR: 
1. Train a source backbone and classifier head on source data
2. Train a domain discriminator, which consists of source backbone, target backbone and discriminator head, on source features and target features by freezing source backbone
3. Stack target backbone and source classifier head

We first pre-train a source encoder CNN using labeled source image examples. Next, we perform adversarial adaptation by learning a target encoder CNN such that a discriminator that sees encoded source and target examples cannot reliably predict their domain label. During testing, target images are mapped with the target encoder to the shared feature space and classified by the source classifier. Dashed lines indicate fixed network parameters.

In domain adaptation, this prin- ciple has been employed to ensure that the network cannot distinguish between the distributions of its training and test domain examples [11, 12, 13]. However, each algorithm makes different design choices such as whether to use a gen- erator, which loss function to employ, or whether to share weights across domains. For example, [11, 12] share weights and learn a symmetric mapping of both source and target im- ages to the shared feature space, while [13] decouple some layers thus learning a partially asymmetric mapping.

Several methods have used the Maximum Mean Discrep-
ancy (MMD) [3] loss for this purpose. MMD computes the norm of the difference between two domain means. The DDC method [5] used MMD in addition to the regular clas- sification loss on the source to learn a representation that is both discriminative and domain invariant. The Deep Adapta- tion Network (DAN) [6] applied MMD to layers embedded in a reproducing kernel Hilbert space, effectively matching higher order statistics of the two distributions. In contrast, the deep Correlation Alignment (CORAL) [8] method pro- posed to match the mean and covariance of the two distribu- tions.

Other methods have chosen an adversarial loss to mini-
mize domain shift, learning a representation that is simulta- neously discriminative of source labels while not being able to distinguish between domains. [12] proposed adding a do- main classifier (a single fully connected layer) that predicts the binary domain label of the inputs and designed a domain confusion loss to encourage its prediction to be as close as possible to a uniform distribution over binary labels. The gra- dient reversal algorithm (ReverseGrad) proposed in [11] also treats domain invariance as a binary classification problem, but directly maximizes the loss of the domain classifier by reversing its gradients. DRCN [9] takes a similar approach but also learns to reconstruct target domain images.

However, Liu and Tuzel achieve state of the art results on un- supervised MNIST-USPS using two generative adversarial networks [13]. These generative models use random noise as input to generate samples in image space—generally, an intermediate feature of an adversarial discriminator is then used as a feature for training a task-specific classifier

## Conditional Adversarial Domain Adaptation
TLDR: Condition discriminator by class label
As deep representations can only reduce, but not remove, the cross-domain distribution discrepancy [54], recent research on deep domain adaptation further embeds adaptation modules in deep networks using two main technologies for distribution matching: moment matching [29, 31, 30] and adversarial training [12, 52, 13, 51].

## Multi-Adversarial Domain Adaptation
TLDR: Train multiple discriminator and condition them by class prediction

To match the source and target domains upon the mul-
timode structures underlying data distributions, we notice that the source domain labeled information provides strong signals to reveal the multimode structures. Therefore, we split the domain discriminator Gd in Equation (1) into K class-wise domain discriminators Gk
d, k = 1, . . . ,K, each is
responsible for matching the source and target domain data associated with class k, as shown in Figure 2. Since target domain data are fully unlabeled, it is not easy to decide which domain discriminator Gk
d is responsible for each target data
point. Fortunately, we observe that the output of the label predictor ˆyi = Gy(xi) to each data point xi is a probability distribution over the label space ofK classes. This distribu- tion well characterizes the probability of assigning xi to each of the K classes. Thus, it is a natural idea to use ˆyi as the probability to indicate how much each data point xi should be attended to the K domain discriminators Gk
d, k = 1, . . . ,K.
The attention of each point xi to a domain discriminator Gk
d can be modeled by weighting its features Gf(xi) with probability ˆyk
i . Applying this to all K domain discriminators Gk

## Contrastive Adaptation Network for Unsupervised Domain Adaptation
TLDR: 
Minimize intra-class discrepancy and maximize inter-class discrepancy 
Train a shared feature exractor
Attach weak labels to target data by k-means clustering on target features

The domain shift exists between the source and target data before adaptation. Middle: Class- agnostic adaptation aligns source and target data at the domain- level, neglecting the class label of the sample, and hence may lead to sub-optimal solutions. Consequently, the target samples of one label may be misaligned with source samples of a different la- bel. Right: Our method performs class-aware alignment across domains. To avoid the misalignment, only the intra-class domain discrepancy is minimized. The inter-class domain discrepancy is maximized to enhance the model’s generalization ability.


## Model Adaptation: Unsupervised Domain Adaptation without Source Data 
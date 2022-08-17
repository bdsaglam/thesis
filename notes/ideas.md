## Ideas

### Cross modal domain adaptation with language
A vision model trained for a task T1 in domain D1.
We aim to adapt this model for domain D2.

The idea is to utilize the world knowledge of a language model for domain adaptation by conditioning the model by the description of the task and the domain.


Sketches:
A model is trained with image and text tokens for mask prediction task. The text consists of the descriptions of task and domain, and the label. Then, the model is adapted to another domain or task by changing the descriptions.
# Neural Machine Translation

This section contains implementations of papers presenting novel architectures for Neural Machine Translation (NMT).

### [Sequence to Sequence Learning with Neural Networks](https://github.com/ThanmayJ/neural-machine-translation/blob/main/seq2seq-pytorch.ipynb)
This paper proposes the pioneering paradigm for nerual machine translation using a simple yet applaudable encoder-decoder RNN pair. Although, being the poorest of performers in this list, it earns a spot due to its novely.\
**<ins>Note:</ins>** A few changes have been made in order to improve performance.
1. Unlike the paper, reversing the input sequences resulted in a lower BLEU Score. Hence, the input sequences have not been reversed.
2. Further an additional parameter called ```teacher_forcing_ratio```, which is the probability of using the ground truth tokens as inputs while decoding has been introduced. It is usually set to 1 while training and 0 while sampling. However, setting it to 0.5 resulted in a better BLEU Score than setting it to 1.

The model was trained on the [Multi30k](https://arxiv.org/abs/1605.00459) dataset which contains roughly 30 thousand English, German and French sentences, each sentence being 10-20 words long. Training and evaluation was done from German to English.

Below is a table addressing some common data and optimization related parameters.

| Parameter      |       Value        |
| -------------- |:------------------:|
| Training Set   |    29000/31014     |
| Testing Set    |     1000/31014     |
| Validation Set |     1014/31014     |
| Loss Function  | Cross Entropy Loss |
| Optimizer      |       AdamW        |

## Other open-source contributions

### 1. [Neural Machine Translation by Jointly Learning to Align and Translate](https://github.com/IvLabs/Natural-Language-Processing/blob/master/neural_machine_translation/notebooks/Seq2Seq_with_Attention.ipynb)
This paper presents a remarkable improvement in the Sequence to Sequence architecture by introducing a (soft)alignment metric called "attention". This metric induces a sense of similarity between tokens of the source and decoded sentences, which increases the BLEU score by almost 1.5 times and is much more robust with regards to the length of source and target sentences.\
**<ins>Note:</ins>** In this implementation, setting the ```teacher_forcing_ratio``` to 1 resulted in a better BLEU score (even with higher validation and test perplexities) than setting it to 0.5.

### 2. [Attention Is All You Need](https://github.com/IvLabs/Natural-Language-Processing/blob/master/neural_machine_translation/notebooks/Attention_Is_All_You_Need.ipynb)
This paper can be said to have revolutionized almost all of Natural Language Processing, all owing to its tremendous simplicity and efficiency which makes it the backbone of almost all present State Of The Art architectures. The proposed *Transformer* architecture introduces a novel metric called *Self-Attention* which induces a sense of (soft)alignment amongst the source sentence tokens too. Additionally architecture uses simple feed-forward layers which makes it almost 4 times lighter than the Convolutional Sequence to Sequence architecture, while attaining the highest BLEU score amongst all the above mentioned architectures.


## Summary
Below is a table, summarising the number of parameters and the BLEU scores achieved by each architecture.

| Architecture                        | No. of Trainable Parameters | BLEU Score |
| ----------------------------------- |:---------------------------:|:----------:|
| Sequence to Sequence                |         13,926,691          |   20.59    |
| Sequence to Sequence with Attention |         20,518,917          |   31.24    |
| Attention Is All You Need           |          9,038,853          |   37.50    |

### Reference(s):
* [PyTorch Seq2Seq by Ben Trevett](https://github.com/bentrevett/pytorch-seq2seq)
* [IvLabs/Natural-Language-Processing](https://github.com/IvLabs/Natural-Language-Processing/tree/master/neural_machine_translation)

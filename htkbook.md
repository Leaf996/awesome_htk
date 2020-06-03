## 3.10 Discriminative Training
- Discriminative training can bring considerable improvements in recognition accuracy and is increasingly being used in large vocabulary speech recognition systems.
    - generation of Initial Maximum Likelihood Models
    - training data LM creation
    - word lattice creation
    - phone marking of Numerator and Denominator lattices
## 8.9 Discriminative Training
- Hence the criteria take into account not only the actual word-level transcription of the training data, but also **confusable** hypotheses which give rise to similar language mode/acoustic model log likelihoods.
- To make the operation of HMMIRest more efficient, the times of the HMM/phone boundaries are also marked in the lattices, this is so-called `phone-marked lattices`, and it is the form that used by HMMIRest.
- For each utterance used for discriminative training, two lattices need to be created. The first is a phone-marked lattice that represents the correct word sequence(also known as a `numerator` lattice), the second is a phone-marked lattice for competing hypotheses(also known as `denominator` lattice).
- When the training data lattices are generated with these weak language models, the lattice tned to be larger, and there is an increased focus on improvedacoustic discrimination.
## 10.4 Data-Driven Clustering
- Applying the argument thatcontext will not greatly affectthe centre states of triphone models, one way to reduce the total number of parameters without significantly altering the models' ability to represent the different contextual effects might to be `tie all of the centre states across all models derived from the same monophone`.
- Explicit typings such as these can have some positive effect but overall they are not very satisfactory. Tying all centre states is too severe and worse still, the problem of `undertraining` for the left and right states remains. A much better approach is to use clustering to decide which states to tie.
## 10.5 Tree-Based Clustering
- One limitation of the data-driven clustering procedure described above is that it does not deal with triphones for which there are no examples in the training data.
# Chapter 14
## Fundamentals of language modelling
- An n-gram is a sequence of n symbols(e.g. words, syntactic categories, etc) and an n-gram language model(LM) is used to predict each symbol in the sequence given its `n-1` predecessors. **In general, the better a language model then the lower its test-set perplexity.** A final difficulty is that the `vocabulary` of an n-gram LM is finite and fixed at construction time.
## 14.1 Wrod n-gram models
- Due to reasons of data sparsity, however, values of n in the range of 1 to 4 inclusive are typically used, and there arealso practicalities of storage space for these estimates to consider.
## 3.10 Discriminative Training
- Discriminative training can bring considerable improvements in recognition accuracy and is increasingly being used in large vocabulary speech recognition systems.
    - generation of Initial Maximum Likelihood Models
    - training data LM creation
    - word lattice creation
    - phone marking of Numerator and Denominator lattices
# Chapter 8
## 8.7 Two-model Re-Estimation
- A typical use of two-model re-estimation is the initialisation of state clustered triphone models.
## 8.9 Discriminative Training
- Hence the criteria take into account not only the actual word-level transcription of the training data, but also **confusable** hypotheses which give rise to similar language mode/acoustic model log likelihoods.
- To make the operation of HMMIRest more efficient, the times of the HMM/phone boundaries are also marked in the lattices, this is so-called `phone-marked lattices`, and it is the form that used by HMMIRest.
- For each utterance used for discriminative training, two lattices need to be created. The first is a phone-marked lattice that represents the correct word sequence(also known as a `numerator` lattice), the second is a phone-marked lattice for competing hypotheses(also known as `denominator` lattice).
- When the training data lattices are generated with these weak language models, the lattice tned to be larger, and there is an increased focus on improvedacoustic discrimination.

# Chapter 9
- It is possible to build improved acoustic models by tailoring a model set to a specific speaker. Such systems are commonly known as `speaker dependent` systems, and on a typical word recognition task, may have half the errors of a speaker independent system. The drawback of speaker dependent systems is that a large amount of data(typically hours) must be collected in order to obtain sufficient model accuracy.
## 9.1 Model adaptation using Linear Transformations
- Maximum Likelihood Linear Regression(MLLR): 最大似然线性回归

# Chapter 10
## 10.2 Constructing Context-Dependent Models
- The first stage of model refinement is usually to convert a set of initialised and trained context-independent monophone HMMs to a set of context dependent models.
## 10.4 Data-Driven Clustering
- Applying the argument thatcontext will not greatly affectthe centre states of triphone models, one way to reduce the total number of parameters without significantly altering the models' ability to represent the different contextual effects might to be `tie all of the centre states across all models derived from the same monophone`.
- Explicit typings such as these can have some positive effect but overall they are not very satisfactory. Tying all centre states is too severe and worse still, the problem of `undertraining` for the left and right states remains. A much better approach is to use clustering to decide which states to tie.
## 10.5 Tree-Based Clustering
- One limitation of the data-driven clustering procedure described above is that it does not deal with triphones for which there are no examples in the training data.
# Chapter 14
## Fundamentals of language modelling
- An n-gram is a sequence of n symbols(e.g. words, syntactic categories, etc) and an n-gram language model(LM) is used to predict each symbol in the sequence given its `n-1` predecessors. It is built on the assumption that the probability of a specific n-gram in some unknown test text can be estimated from the frequency of its occurrence in some given training text. **In general, the better a language model then the lower its test-set perplexity.** A final difficulty is that the `vocabulary` of an n-gram LM is finite and fixed at construction time.
- Although the basic principle of an n-gram LM is very simple, in practice there are usually many more `potential n-grams` than can ever be collected in a training text in sufficient numbers to yield robust frequency estimates. Furthermore, for any real application such as speech recognition, the use of an `essentially static and finite training text` makes it difficult to generate a single LM which is well-matched to varying test material. A final diffculty is that the vocabulary of an n-gram LM is finite and fixed at construction time, thus, if the LM is word-based, it can only predict words within its vocabulary and furthermore new words cannot be added without rebuilding the LM.
## 14.1 Wrod n-gram models
- Language models estimate the probability of a word sequence.
- Due to reasons of data sparsity, however, values of n in the range of 1 to 4 inclusive are typically used, and there arealso practicalities of storage space for these estimates to consider.
- Estimates of probabilities in n-gram models are commonly based on maximum likelihood estimates - that is, by counting events in context on some given training text.
- It is not only the storage space that must be considered, however - it is also necessary to be able to attach a reasonable degree of confidence to the derived estimates.
- One method of reducing the number of word history equivalence classes to be modelled in the n-gram case is to consider some words as equivalent. A deterministic word-to-class mapping like this has some advantages over a word n-gram model since the reduction in the number of distinct histories reduces the storage space and training data requirements whilst improving the robustness of the probability estimates for a given quantity of training data.
## 14.2 Statistically-derived Class Maps
- Methods of statistical class map construction seek to maximise the likelihood of the training text given the class model by making iterative controleld changes to an initial class map.
## 14.3 Robust model estimation
- A language model should not give any unseen event zero probability.
## 14.4 Perplexity
- 
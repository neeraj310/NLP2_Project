# NLP2_Project
NLP2 Semster Project
Project submission contains a Jupyter Notebook and Project Report

# NLP2_Project: Concurrent Learning of Semantic Relations
Authors:<br>
Neeraj Kumar<br>
Mariann Burk<br>


## Problem statement
To understand whether learning a classifier for one semantic relation (e.g. hypernymy) can gain from concurrently learning another classifier for a cognitively-linked semantic relation (e.g. co-hyponymy). 

## Multi Task Problem
As we want to concurrently learn multiple semantic relationships like hypernomy/Synonyms, we will use multitask classification with hard parameter sharing. Our hypothesis is is that if the tasks are cognitively linked, multi-task learning approaches should improve the performance on the tasks as the decision functions are learned concurrently. We propose a hard parameter sharing architecture based on a feed-forward neural network
(NN) to perform the classification task.

![image](https://user-images.githubusercontent.com/57225473/117209105-35bbeb00-adf6-11eb-915f-4cf8acf0a587.png)



## Our Contribution
 - Compare classification performance of semantic relations among various models like logistic regression, mlp , cnn
 - Show that multi-task learning consistently improves the classification performance of semantic relations.
 - we show that semi-supervised learning can benefit performance depending on the used dataset and semantic relation.
 
Brief Description of Dataset

## Rumen Dataset 
Rumen Dataset contains 18,978 noun pairs automatically gathered fromWordNet 3.010 [24] and equally organized amongst three classes (hypernymy, synonymy and random). Note that the words in the pairs are single words and do not contain multiword expressions. In particular, the RUMEN dataset contains 9,125 word types (i.e. unique nouns) distributed as follows for each semantic relation: 5,054 for hypernymy,
5,201 for synonymy and 6,042 for random.

## Roots Dataset
Roots dataset contains 9,600 word pairs, randomly extracted from three well-known datasets: EVALution [33], Lenci/Benotto [5] and BLESS [4]. The word pairs are equally distributed among three classes (hypernymy, co-hyponymy and random) and involve several part-of-speech tags (adjectives, nouns and verbs). Here, we exclusively focus on nouns and keep 1,212 hypernyms, 1,604 co-hyponyms and 549 random pairs that can be represented by GloVe
embeddings

# Lexical Split

Using distributional representations in the context of supervised learning tends to perform lexical memorization.In this case, the model mostly learns independent properties of single terms in pairs. For instance, if the training set contains word pairs like (bike, tandem), (bike, off-roader) and (bike, velocipede) tagged as hypernyms, the algorithm may learn that bike is a prototypical hypernym and all new pairs (bike, y) may be classified as hypernyms,regardless of the relation that holds between bike and y. To overcome this situation and prevent the model from overfitting by lexical memorization, it has been suggested to to split the train and test sets such that each one contains a distinct vocabulary. This procedure is called lexical split. For our model, lexical repetition exists in the train, validation and the unlabeled subsets, but the test set is exclusive in terms of vocabulary


# Semi-supervision via self-learning
Semi-supervised learning approaches perform well in a variety of tasks such as text classification and text summarization. As in the supervised learning framework, we assume that we are given access to a set L that consists of K pairs of words labeled according to the relationship rel. Complementary to that, we also assume to have access to a set of K0 words pairs U distinct from those of L, and totally unlabeled. The challenge in this setting is to surpass the perfo=rmance of classification models trained exclusively on L by using the available data in U.

Train Classifier C using word pairs L
progressively expand L, by pseudo-labeling 10 pairs within U, for which the current prediction function is the most confident and adding them to L

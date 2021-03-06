---
layout: post
title: GloVe-Global Vectors for Word Representation
subtitle: Title of paper - GloVe-Global Vectors for Word Representation
category: NLP papers - Word Embedding
tags: [nlp, word embedding]
permalink: /2018/10/31/GloVe_Global_Vectors_for_Word_Representation/
css : /css/ForYouTubeByHyun.css
bigimg: 
  - "/img/Image/BigImages/carmel.jpg" : "Carmel-by-the-Sea, CA (2016)"
  - "/img/Image/BigImages/monterey.jpg" : "Monterey, CA (2016)"
  - "/img/Image/BigImages/stanford_dish.jpg" : "Stanford Dish, CA (2016)"
  - "/img/Image/BigImages/marian_beach_in_sanfran.jpg" : "MRINA of San Francisco, CA (2016)"
  - "/img/Image/BigImages/carmel2.jpg" : "Carmel-by-the-Sea, CA (2016)"
  - "/img/Image/BigImages/marina.jpg" : "MRINA of San Francisco, CA (2016)"
  - "/img/Image/BigImages/sanfrancisco.jpg" : "San Francisco, CA (2016)"
---

{% include MathJax.html %}


This posting is summary for my study about the paper, "[GloVe: Global Vectors for Word Representation (Pennington et al., EMLNP 2014)](https://www.aclweb.org/anthology/D14-1162/)"


There are two methodologies for distributional word representations.

one is to be learned from count-based method like latent semantic anlaysis-LSA(Deer-wester et al., 1990) and hyperspace analogue to Language-HAL(Lund and Burgess, 1996).

  - based on frequencies of terms.
  
    1) In LSA, matrix of term-document type like bag-of-words matrix: rows correspond to words or terms, and the columns correspond to different documents in corpus.
    
    2) In HAL, matrix of term-term type like co-occurence matrix: rows correspond to words, and the columns correspond to the entries which is the number of times a given word occurs in the context of another given word.
       - In particular, co-occurence matrix could be transformed to an entropy- or correlations-based normalization.

    3) PPMI(Bullinaria and Levy 2007), square root type HPCA-Hellinger PCA(Lebret and Collobert, 2014) and so on.
    
The other is prediction-based method like Word2Vec(Mikolov et al., 2013), vLBL and ivLBL(Mnih and Kavukcuoglu 2013), Bengio et al.(2003), Collobert and Weston(2008), Collobert et al.(2011).


All the methods above could be separated into the Matrix Factorization Method(i.e. NMF:Non-negative Factorization) and the Shallow Window-Based Methods.


### GloVe

GloVe paper said the statistics of word occurrence in a corpus is the primary source of information available to al unsupervised methods for learning  word representation.

So, GloVe utilized are the matrix word-word co-coccurence with context window size.

Above all, Let's see notation for equation of GloVe.


Let the matrix of word-word co-occurrence counts be denoted by X, whose entries \\(X_{ij}\\) tabulate the number of times word j occurs in the context of word i.

Let \\( X_{i}=\sum_{k}X_{ik} \\) be the number of times any word appears in the context of word i.

Finally, let \\( P_{ij}=P(j\|i)=X_{ij}/X_{i} \\) be the probability that word j appear in the context of word i.


The following would explain how to correlate the ratio of co-occurrence of target words for information to embed the distinction of words. 

![Pennington et al., EMLNP 2014](/img/Image/NaturalLanguageProcessing/NLPLabs/Paper_Investigation/Word2Vec/2018-10-31-GloVe_Global_Vectors_for_Word_Representation/Co-occurence_matrix_probability.png)


GloVe is log-bilinear regression model and then the cost function is the same from the following


![Pennington et al., EMLNP 2014](/img/Image/NaturalLanguageProcessing/NLPLabs/Paper_Investigation/Word2Vec/2018-10-31-GloVe_Global_Vectors_for_Word_Representation/Cost_function.png)

As you can see above, \\( f(X_{ij}) \\) is weighting function. The weighting function should be obey the following properties:

 - f(X) should be non-decreasing so that rare co-occurences are not overweighted.
 
 - f(X) should be relatively small for large value of X, so that frequent co-occurences are not overweighted.

f(X) function below was used in the GloVe paper

![Pennington et al., EMLNP 2014](/img/Image/NaturalLanguageProcessing/NLPLabs/Paper_Investigation/Word2Vec/2018-10-31-GloVe_Global_Vectors_for_Word_Representation/Weighting_function.png)

![Pennington et al., EMLNP 2014](/img/Image/NaturalLanguageProcessing/NLPLabs/Paper_Investigation/Word2Vec/2018-10-31-GloVe_Global_Vectors_for_Word_Representation/Weigting_function_equation.png)


As you can see the cost function, GloVe calculates co-occurence matrix to update 

\\( W_{i} \\), word vector and \\( W_{j} \\), context word vector.

So, if the corpus is changed, you need to update the co-occurence matrix.

The cost function calculates the least square of \\(W_{i}^T\\)*\\(W_{j}\\) - \\(log(X_{ij})\\)

\\(X_{ij}\\) is the number of times word **k** appears in the context of word **i**. 

<div class="alert alert-success" role="alert"><i class="fa fa-check-square-o"></i> <b>Tip: </b>
`\(W_{i}\)` and `\(W_{j}\)` is weight matrix(i.e. vector) and X(co-occurence matrix) is symmetric. the sum of `\(W_{i}\)` and `\(W_{j}\)` is used for word vector which boosts the performance in NLP task of this paper
</div>

<div class="alert alert-info" role="alert"><i class="fa fa-info-circle"></i> <b>Note: </b>
GloVe is another way to represent words into continuous vector space with two ways which are global cooccurence matrix and log-bilinear regression model. GloVe also utilize the families like 1) global matrix factorization method, 2) local context window methods.
</div>
  
  
<div class="alert alert-success" role="alert"><i class="fa fa-paperclip fa-lg"></i> <b>Download URL: </b><br>
  <a href="https://nlp.stanford.edu/projects/glove/">The paper: GloVe:Global Vectors for Word Representation</a>
</div>

<div id="tutorial-section">

  <div id="tutorial-title">GloVe Youtube</div>

  <ul class="nav nav-pills">
    <li class="active"><a data-toggle="tab" href="#refrigerator">Stanford Youtube</a></li>
    <li><a data-toggle="tab" href="#refrigerator_concept">DeepLearning AI</a></li>
  </ul>

  <div class="tab-content">
    <div id="refrigerator" class="tab-pane fade in active">
      <iframe width="560" height="315" src="https://www.youtube.com/embed/ASn7ExxLZws" frameborder="0" allowfullscreen></iframe>
    </div>
    <div id="refrigerator_concept" class="tab-pane fade">
      <iframe width="560" height="315" src="https://www.youtube.com/embed/CE3PXQkbupk" frameborder="0" allowfullscreen></iframe> </div>
  </div>
</div>


# Reference 

- Paper 
  - [GloVe:Global Vectors for Word Representation (Pennington et al., EMLNP 2014)](https://www.aclweb.org/anthology/D14-1162/)
 
- How to use html for alert
  - [how to use icon](http://idratherbewriting.com/documentation-theme-jekyll/mydoc_icons.html)
  
- [What is the GloVe? Part 1 on Towards Data Science](https://towardsdatascience.com/emnlp-what-is-glove-part-i-3b6ce6a7f970)
 
- [What is the GloVe? Part 2 on Towards Data Science](https://towardsdatascience.com/emnlp-what-is-glove-part-ii-9e5ad227ee0)

- [What is the GloVe? Part 3 on Towards Data Science](https://towardsdatascience.com/emnlp-what-is-glove-part-iii-c6090bed114)

- [What is the GloVe? Part 4 on Towards Data Science](https://towardsdatascience.com/emnlp-what-is-glove-part-iv-e605a4c407c8)
  
- [What is the GloVe? Part 5 on Towards Data Science](https://towardsdatascience.com/emnlp-what-is-glove-part-v-fa888272c290) 
  
- [CBOW vs Skip-gram on Stackoverflow](https://stackoverflow.com/questions/38287772/cbow-v-s-skip-gram-why-invert-context-and-target-words)
  
- online Learning
  - [Online Learning of Word Embeddings on Medium](https://medium.com/explorations-in-language-and-learning/online-learning-of-word-embeddings-7c2889c99704)
  
  - [Online Learning on Linkedin Slide](https://www.slideshare.net/queirozfcom/online-machine-learning-introduction-and-examples)
     * I think the aobve links I read a little is very interesting. later on I would read both of them and papers related to it.
  
 - [bilinear regression definition](https://www.statisticshowto.datasciencecentral.com/bilinear-regression/)

 - [StackExchange about bilinear](https://math.stackexchange.com/questions/878325/what-is-a-bilinear-form)
 
 - [word embedding part 1 on Sebastian Ruder blog](http://ruder.io/word-embeddings-1/)
 
 - [word embedding part 2 on Sebastian Ruder blog](http://ruder.io/word-embeddings-softmax/)
 
 - [word embedding part 3 on Sebastian Ruder blog](http://ruder.io/secret-word2vec/)

 - [word embeddings in 2017: Trends and Future directions on Sebastian Ruder blog](http://ruder.io/word-embeddings-2017/)
 
 - [A survey of cross-lingual word embedding models on Sebastian Ruder blog](http://ruder.io/cross-lingual-embeddings/index.html)

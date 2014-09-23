Dependency parsing
==================

Dependency parsing is a method for the syntactic analysis of natural
language text, based on the theory of dependency grammar. Rather than
being a single unified theory, dependency grammar is a tradition
encompassing several theories, which recently has gained additional
popularity due to its value in various natural language processing
tasks, such as relation extraction (e.g. @culotta2004dependency) and
machine translation (e.g. @shen2008new). Additionally, it is well-suited
for the description of languages with free word order
[@kubler2009dependency].

Therefore, in the following section, we will briefly introduce
dependency grammar, and give an overview of the differences among its
various representations.

Dependency grammar
------------------

While dependency grammar has a rich history reaching back as far as the
descriptions of the Sanskrit language, its modern tradition is believed
to have begun with the French linguist Lucien Tesnière. In contrast to
phrase structure grammars, in dependency grammars, the central means of
describing linguistic structure is through words or tokens that are
linked by directed dependency relations. The elements of a dependency
relation are two words: the syntactically subordinate *dependent* and
the word on which it depends, called the *head* (or *governor*).
Furthermore, each dependency between two words is labeled by the *type*
of their relation, such as *subject*, *direct object* or *attribute*.
Consider, for example, the simple dependency tree in
Figure [fig:simpledep].

[theme=simple,label style=<span>font=</span>, group
style=<span>font=</span>]]

[column sep=1em, font=] **ROOT** & Peter & likes & Mary\

[fig:simpledep]

In this example, *likes* is the head of both *Peter* and *Mary* and
their dependency relations indicate that *Peter* is the subject () and
*Mary* is the object () dependent on the verb *likes*, while the verb
itself is a dependent of the artificial node. The node is inserted into
the tree as a technical simplification to ensure that every word has a
syntactic head.

### Formal definition {#sec:depgraph_definiton}

As we will rely on these definitions in the following chapters and
sections of this thesis, here we introduce the formal definition of
dependency trees and their properties by following the formulation from
@kubler2009dependency [p. 11].

A sentence $S$ is a sequence of tokens $S = w_0w_1...w_n$. The token
$w_0$ is treated as the artificial root token, which we labeled in
Figure [fig:simpledep]. While the term token is commonly used as a
synonym for a word in a sentence, depending on the language and
conventions used, it does not have to be a full word but can represent
single morphemes or punctuation.

Dependency relations are the relations between two words in the
sentence. $R = \{r_1, ..., r_m\}$ is the finite set of dependency
relation types that can hold between any two words. There are no further
assumptions about the set $R$, and the final set of relations depends on
the convention of the dependency format and the underlying linguistic
theory. In the example in Figure [fig:simpledep], the dependency types
are displayed as the labels of the arcs between the words: , and .

In order to define dependency trees, which are a special type of
dependency graphs, we first need to define dependency graphs. A
dependency graph can be defined as the following (slightly adapting the
definition from @kubler2009dependency [p. 12]): A dependency graph
$G = (V, A)$ is a labeled directed graph consisting of nodes (vertices,
$V$) and edges (arcs, $A$), such that the following holds for
$S=w_0w_1...w_n$ and the set of dependency types $R$:

1.  $V \subseteq \{ w_0, w_1, ..., w_n \}$

2.  $A \subseteq V \times R \times V$

3.  if $(w_i, r, w_j) \in A$ then $(w_i, r', w_j) \not\in A$ for all
    $r' \not= r$

An edge $(w_i, r, w_j) \in A$ represents a dependency relation from the
word $w_i$ to the word $w_j$ with the dependency type $r$. In this
dependency relation, $w_i$ is the head, and $w_j$ is the dependent node.
While the third condition disallows multiple dependency relations
between two words, it does not restrict words from having more than one
head. Most dependency grammar theories are based on dependency trees,
which are a further restriction of dependency graphs that we will define
now.

A *dependency tree* is defined as a *well-formed* dependency graph. A
dependency graph $G$ for a sentence $S$, and a dependency relation set
$R$ is called *well-formed* if it is a directed tree originating in the
root node and if it has a spanning node set (i.e. a set of nodes
containing all words of the sentence). A tree is an undirected graph in
which any two nodes are connected by one and only one path. This means
that a connected graph can only be a tree if it contains no cycles. In a
directed tree, the edges between nodes are directed.

In a dependency graph, while it is possible for a word to have multiple
heads, the tree property of dependency trees prohibits this. A node in
the dependency tree can only have one single incoming edge. If a node in
a dependency tree would have multiple heads, it would mean that there
exist more than one paths between this node and the root node and other
nodes common to both paths.

### Projective and non-projective dependency trees

A further restriction on dependency trees is the distinction between
projective and non-projective dependency trees. The following notations
are required for the definition of projective and non-projective
dependency trees:

-   $w_i \to w_j$ indicates an unlabeled dependency relation between
    $w_i$ and $w_j$ in a tree $G = (V, A)$. Hence, $w_i \to w_j$ means
    that there is some dependency relation type $r \in R$ such that
    $(w_i, r, w_j) \in A$.

-   $w_i \to^* w_j$ indicates a *reflexive transitive closure* of the
    dependency relation in a tree $G = (V, A)$. This is defined as
    $w_i \to^* w_j$ if and only if $i = j$ (*reflexive*) or both
    $w_i \to^* w_{i'}$ and $w_{i'} \to w_j$ hold for some
    $w_{i'} \in V$.

An edge in a dependency tree is projective if and only if
$w_i \to^* w_k$ for all $i < k < j$ when $i < j$, or $j < k < i$ when
$j < i$. Following this definition, an edge $(w_i, r, w_j)$ is
projective if there is a path from the head $w_i$ to all the words
between the two endpoints of the edge ($i$ and $j$). Accordingly, a
dependency tree $G = (V, A)$ is *projective* if all
$(w_i, r, w_j) \in A$ are projective. A dependency tree that is not
projective is *non-projective*.

As examples of projective and non-projective dependency trees, consider
the two dependency trees in Figure [fig:projectivedeptree] and
Figure [fig:nonprojectivedeptree], which are dependency trees for
commonly used English example sentence from the Penn treebank (both
dependency trees are taken from @kubler2009dependency [p. 17]).

[theme=simple,label style=<span>font=</span>, group
style=<span>font=</span>]]

[column sep=1em, font=] **ROOT** & Economic & news & had & little &
effect & on & financial & markets & .\

[fig:projectivedeptree]

In this representation of dependency trees, with all words at the same
level, the dependency tree in Figure [fig:projectivedeptree] can be
drawn without crossing edges as all edges in this tree are projective.
For the dependency tree in Figure [fig:nonprojectivedeptree], however,
it is not possible to draw the tree without crossing edges. For the
dependency relation between *hearing* and *on*, there is no path from
the head of the relation *hearing* to the words in between the two
end-points of the edge, namely the words *is* and *scheduled*. Hence,
the edge between *hearing* and *on* is not projective.

[theme=simple,label style=<span>font=</span>, group
style=<span>font=</span>]]

[column sep=1em, font=] **ROOT** & A & hearing & is & scheduled & on &
the & issue & today & .\

[fig:nonprojectivedeptree]

Data-driven dependency parsing
------------------------------

The task of a dependency parsing algorithm is to find the dependency
structure for the words in a sentence. In this dependency structure,
words, including the artificial node, are connected by labeled
dependencies. While the set of dependency labels is determined by the
dependency representation format; most dependency parsing algorithms are
independent of the specific labels, and they can be trained for various
types of dependencies.

Parsing in general, and specifically dependency parsing, are nontrivial
tasks since the dependencies between the words of a sentence need to be
determined while both adhering to linguistic and syntactic constraints,
and at the same time ensuring that the resulting dependency graph is
well-formed. This process is complicated by the tendency of natural
language to be inherently ambiguous. For a given sentence, a parser may
find multiple possible analyses, and as a result, it is required to make
an optimal decision taking into account both local syntactic constraints
as well as the complete analysis.

Data-driven methods for dependency parsing are based on machine learning
techniques, most notably supervised methods. In supervised learning, a
model is trained on a set of manually annotated instances. Using this
trained model, the structure of new instances can be inferred. Hence, a
data-driven parsing method must address two problems: First, in the
*Learning* task, a parsing model $M$ is learned from a set of annotated
training instances (dependency trees). Then, in the *Parsing* or
*Decoding* task, the parsing model $M$ is used to produce the optimal
dependency graph $G$ for a sentence $S$.

Maximum-spanning tree parsing
-----------------------------

The *learning* and *parsing* tasks are implemented in various ways by
different parsers. A well-known algorithm is the Maximum Spanning Tree
parser (MST, @mcdonald2005non). In the following section, we will
briefly summarize how these two tasks are approached in the MST parser.

#### Learning: Online Large Margin Learning

The *learning* task in this parser is approached as a supervised
learning problem for structured output. The score of a dependency tree
is factored as the sum of the scores of all edges in the tree. The score
for each edge is calculated as the dot product of a feature vector for
the edge, and the weight vector $\vect{w}$.

$$s(i, j) = \vect{w} \cdot \mathbf{f}(i, j)$$

Given a sentence $\boldsymbol{x}$, the score for a dependency tree
$\boldsymbol{y}$ is:

$$s(\boldsymbol{x}, \boldsymbol{y}) = \sum_{(i,j) \in \boldsymbol{y}}{s(i, j)}$$

To determine the weight vector $\vect{w}$, a learning algorithm based on
the Margin Infused Relaxed Algorithm (MIRA,
@crammer2003ultraconservative) is used. MIRA is an online learning
algorithm similar to the online version of the basic Perceptron learning
algorithm [@rosenblatt1958perceptron]. Unlike a batch learning method,
the online algorithm works by updating the weight vector $\vect{w}$
after each training instance it considers.

Pseudo-code for the MIRA algorithm is given in Algorithm [alg:MIRA].
$dt(\boldsymbol{x})$ is the set of possible dependency trees for the
sentence $\boldsymbol{x}$. The algorithm runs for $N$ iterations, and
during each of the iterations, it traverses all training instances, and
determines the optimal weight with regard to the loss function $L$. In
the case of dependency parsing, $L$ is the number of words in the
dependency tree with incorrect parent words compared to the correct
tree. After $N$ iterations, the intermediate weights stored in
$\vect{v}$ are averaged, which has been shown to decrease the risk of
the model overfitting to the training data [@collins2002discriminative].

[1] **Training data:** $\tau = \{ (x_t, y_t) \}^T_{t=1}$ min
$|| \vect{w}^{(i+1)} - \vect{w}^{(i)} ||$ s.t.
$s(x_t, y_t) - s(x_t, y') \geq L(y_t, y'), \forall y' \in dt(x_t) $

#### Decoding: Projective and non-projective trees

In the MST parser, the task of finding the optimal parse tree is
formulated as finding a maximum spanning tree for the words of the input
sentence, by using the edge scores, which were introduced above as
weights within the graph. For the projective and the non-projective
case, separate decoding algorithms are used. The projective decoding
algorithm is the Eisner algorithm [@eisner1996three], which is a
frequently used $O(n^3)$ algorithm for maximum projective spanning
trees. In the non-projective case, the search for a suitable parse tree
is performed by searching for a maximum spanning tree in a directed
acyclic graph using the Chu-Liu-Edmonds algorithm
[@chu1965shortest; @edmonds1967optimum]. Specifically, an implementation
of the algorithm for dense graphs which has complexity $O(n^2)$ is used.

Parsing and domain adaptation {#sec:domainadapt}
=============================

Domain adaptation
-----------------

According to the Concise Oxford Dictionary of Linguistics [@domain], a
domain in the cultural or in another setting is a situation, or a text
form in which different forms of speech may be appropriate; such as the
different forms of speech in the domain of a law court or of sports
commentary, compared to the domain of a family at home. In natural
language processing, domains are conventionally delimited collections of
texts or literary genres such as news wire articles or biomedical
literature. However, especially since the emergence of the World Wide
Web has weakened traditional forms of publishing and categorization, the
definition and delimitation of domains has become more difficult. Some
authors go as far as arguing that on the World Wide Web, each document
is its own domain [e.g. @mcclosky2010automatic]. Methods for domain
adaption vary in the extent to which strict boundaries between domains
are assumed. In the following section, we will introduce the most widely
used methods for domain adaption in parsing.

Methods for domain adaption
---------------------------

In the relevant literature, it is commonly acknowledged that parsing
accuracy degrades when a parsing model trained on a certain domain is
applied to a different domain. In order to investigate this issue,
various methods and specific task settings have been brought forward. In
this section, we will briefly summarize the most important findings and
methods; and will also outline how they relate to the topic of this
thesis.

One of the first issues requiring to be addressed in domain adaptation
is the lack of a precise definition of what a domain constitutes.
Approaches differ in whether they assume that domains are given or in
whether they attempt to select data similar to a target domain
automatically.

### Single source parser adaptation

The CoNLL 2007 Shared Task on dependency parsing [@conll2007] contained
a track on domain adaptation, in which the participants were asked to
produce the best possible parsing results across domains. Participants
were provided with a large syntactically annotated corpus from the
source domain as well as data from three target domains (biomedical
abstracts, chemical abstracts and parent-child dialogues). Like the
source domain data, the target domain data contained full dependency
trees; however, the set of biomedical abstracts was only used as a
development set, while the set of chemical abstracts was used as a test
set. Additionally, large unlabeled data sets, i.e. data sets without any
annotation, were provided as training data for each of the target
domains. Hence, in this setting only a single source domain, in this
case the Wall Street Journal sections of the Penn Treebank, was used.

The most successful systems participating in the domain adaptation part
of the CoNLL 2007 Shared Task used two major approaches: Firstly, in
feature-based approaches, the features of the parsing system were either
reduced to features mostly valid across various domains, or features
from the source domain were transferred to the target domain
[@conll2007]. And secondly, in ensemble-based approaches, several
parsers are trained, and run; and then their output was combined in a
new classifier. Other approaches included tree revision rules and
filtering of the training set based on similarity to the target domain.

Other methods that have gained in popularity recently are
*self-training* and *up-training*. *Self-training* is a method for
effective parser adaptation that was introduced by @mcclosky06. In self
training, a parser is learned on labeled data, and then it is used to
annotate unlabeled data, possibly from the target domain. Together with
the original labeled data, the parsed unlabeled data is used afterwards
as training data for a new model. This process can be repeated several
times. Intuitively, since errors can propagate into the parsing model,
one may expect this method to degrade parsing accuracy. However, the
authors found that the self-training method provided a 12% error
reduction over the previous best result of Wall Street Journal parsing.
The authors’ error analysis suggests that improvements were not obtained
as a result of better unknown word handling; and furthermore, the
accuracy for sentences of a length between 20 and 50 words improved in
general.

*Uptraining* [@petrov2010] is a method for domain adaptation similar to
*self-training*. This method is focused more on deterministic parsers,
such as shift-reduce dependency parsers. In *uptraining*, a
deterministic parser is trained on the output of a slower but more
accurate constituent parser. The authors demonstrate that a
deterministic parser trained on 100.000 questions parsed by a more
accurate parser provides results comparable to a deterministic parser
trained on 2.000 manually annotated questions.

For closely related languages, @zeman08 describe an approach to parser
adaptation to a new language in the special case that the target
language—which has only few resources available—is related to the source
language. The authors demonstrate that a de-lexicalization method works
well in an experiment with data from Danish and Swedish. In
de-lexicalization task, the words of the source language are replaced by
their morphological tags in the training data, and the same tagset is
used when applied to the target language. Parsing the Swedish data with
a de-lexicalized Danish parsing model achieved parsing performance
equivalent to a parser trained on 1546 Swedish gold trees.

### Multiple source parser adaptation

@mcclosky2010automatic take a different approach for the parser
adaptation problem by introducing a new task, which include baseline
systems for what they call *multiple source parser adaptation*. In this
setup, a system is trained on corpora from various domains, and it
learns the plain parsing models, as well as models of domain differences
and their influence on parsing accuracy. Given this knowledge, the
parser applies a linear combination of plain parsing models to new
input.

### Automatic selection of relevant training data

The approaches to domain adaption mentioned so far involve the
assumption that domains are given in advance. @plank2011 evaluate
methods to select training data similar to the target domain
automatically, by using an unsupervised method based on topic modeling.
This method does not rely on predefined domains. Instead, in order to
gather relevant data for the particular target domain from the source
domain corpus, measures of domain similarity are used.

Parsing and the noisy-channel model {#sec:noisychannel}
===================================

The noisy-channel model
-----------------------

The noisy-channel model [@shannon1948mathematical] is a mathematical
model for communication that has been successfully applied to a wide
variety of natural language processing tasks. The original model was
motivated by the wish to transmit the maximum possible amount of
information over a noisy means of communication @manning1999foundations
[p. 60]. Today, this model is the basis for a number of successful
approaches to problems such as machine translation and automatic
spelling correction.

![Schematic diagram of a general communication system
@shannon1948mathematical [p. 2]](figs/noisy_channel.pdf)

In the noisy-channel model, a message is generated by the information
source and passed trough a noisy channel. The receiver is given the
resulting noisy data; and the receiver’s goal is to recover, or in other
words to *decode*, this noisy data in order to determine the original
message. Given observed data $O$ with the original source form $S$ for
which there exists some prior knowledge, this process is typically
modeled by using Bayes’ rule [@lease06]:

$$\begin{aligned}
  \hat{s} = \argmax_{S} \Prob(S|O) = \argmax_{S} \Prob(O|S) \Prob(S)\end{aligned}$$

Sentence comprehension under noisy input
----------------------------------------

In the psycholinguistics literature, a problem that is closely related
to parsing is the problem of human sentence comprehension. While most
research in this area assumes perfectly-formed input; @levy2008noisy
proposes a noisy-channel based model of human sentence comprehension
that can account for some of the outstanding problems in sentence
processing. The model uses a generative probabilistic grammar. In the
standard case that the input string $\vect{w}$ is fully known, the
grammar $G$ can be used to find the best parse $T$ for $\vect{w}$ using

$$\begin{aligned}
  \argmax_T \mathrm{P}_G(T|\vect{w})\end{aligned}$$

However, in the case that the input string is not known, the formulation
changes to the following: Given some noisy evidence $I$ and using the
Bayes’ rule to find the posterior for $\mathrm{P}_G(T|\vect{w})$ and
$\mathrm{P}_G(T|I)$:

$$\begin{aligned}
  \mathrm{P}_G(T|I) &= \frac{ \Prob(T,I) }{ \Prob(I) } \\
  &\propto \sum_{ \vect{w} } \Prob(I|T,\vect{w}) \Prob(\vect{w}|T) \Prob(T) \label{levyI}\end{aligned}$$

While not directly applying this model to parsing, @levy2008noisy
performs a psycholinguistics experiment in which he assumes a noisy
environment distorting an original utterance. A comprehender is
presented a sentence $\vect{w}^*$, which is known by the researchers.
However, the specific noisy representation $I$ of this sentence is not
known. Based on the formula in ([levyI]), for the probability of the
comprehender’s understood sentence $\vect{w}$, we have:

$$\begin{aligned}
  \mathrm{P}_G(\vect{w}|I) &\propto \sum_{ \vect{w} } \Prob(I|T,\vect{w}) \Prob(\vect{w}|T) \Prob(T)\end{aligned}$$

In the controlled experiment of @levy2008noisy, the relevant probability
distribution is $ \Prob(\vect{w}|\vect{w}^*)$, which is given as

$$\begin{aligned}
  \Prob(\vect{w}|\vect{w}^*) &= \int_{ I } \mathrm{P}_C(\vect{w}|I,\vect{w}^*) \mathrm{P}_T(I|\vect{w}^*)  \dif I\label{levyII}\end{aligned}$$

Then, since the comprehender does not know $\vect{w}^*$, it is assumed
that $\vect{w}^*$ and $\vect{w}$ are conditionally independent. Applying
Bayes’ rule to [levyII], the following formulation is proposed
($\mathrm{P}_C$ is the probability distribution of the comprehender):

$$\begin{aligned}
  \Prob(\vect{w}|\vect{w}^*) &= \int_{ I } \frac{ \mathrm{P}_C(I|\vect{w}) \mathrm{P}_C(\vect{w}) }{ \mathrm{P}_C(I) }  \mathrm{P}_T(I|\vect{w}^*) \dif I \\
   &= \mathrm{P}_C(\vect{w}) \int_{ I } \frac{ \mathrm{P}_C(I|\vect{w}) \mathrm{P}_T(I|\vect{w}^*) }{ \mathrm{P}_C(I) } \dif I\label{levyIII} \\
   &\propto \mathrm{P}_C(\vect{w}) Q(\vect{w}, \vect{w}^*)\label{levyIV}\end{aligned}$$

$Q(\vect{w}, \vect{w}^*)$ in ([levyIV]) is proportional to the integral
in ([levyIII]) and given some of the experiment’s assumptions; it is a
symmetric, non-negative function of $\vect{w}$ and $\vect{w}^*$. In the
rest of the paper, $Q(\vect{w}, \vect{w}^*)$ is implemented as a simple
Levensthein distance measure calculated via a token-based finite-state
automaton.

One of the arguments that is presented as supporting this model comes
from a simple prediction the model makes: the prior knowledge
$\mathrm{P}_C(\vect{w})$ of the comprehender can overwrite the actual
linguistic input. Hence, a sentence can be interpreted as meaning
something else than it was originally expressed to mean. This is a
necessary requirement of such a model: A human copy editor, for example,
is without a question, able to read and correct erroneous writing.
Non-noisy models of sentence processing are able to cover this issue in
cases where the sentence is ungrammatical; however, the noisy model can
also account for cases where the sentence is fully grammatical but the
comprehender can still not process the sentence. This is the case in
certain garden path sentences, as in the following example from
@levy2008noisy:

. a. While the man hunted the deer ran into the woods.[ex:gardenpath]\
b. While the man hunted it the deer ran into the woods.[ex:nogardenpath]

In this case, both sentences are grammatical sentences. For the sentence
in [ex:gardenpath], there is a grammatical reading; however, it is
ambiguous whether *the deer* is the object of the verb *hunted*, or the
subject of the verb *ran*. In the case that it is read as the object of
*hunted*, the *ran* will miss a subject, and the comprehender would
re-read the sentence as it “leads nowhere”. However, experiments in
which participants are given this sentence have shown that a large
number of participants initially perceive *the deer* as the object of
*hunted*. Non-noisy models of sentence processing would not predict
this; however, it can be explained by the noisy model that can assume an
underlying sentence such as the sentence in [ex:nogardenpath].

Note the similarity of the final model in ([levyIV]) to well-established
noisy-channel methods for spelling correction, such as
@kernighan1990spelling, where a correction $c$ for a text $t$ is found
by maximizing $\Prob(c) \Prob(t|c)$.

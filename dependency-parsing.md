---
layout: default
title: Dependency parsing
---

# Dependency parsing

Dependency parsing is a method for the syntactic analysis of natural
language text, based on the theory of dependency grammar. Rather than
being a single unified theory, dependency grammar is a tradition
encompassing several theories, which recently has gained additional
popularity due to its value in various natural language processing
tasks, such as relation extraction (e.g. Culotta and Sorensen (2004))
and machine translation (e.g. Shen et al. (2008)). Additionally, it is
well-suited for the description of languages with free word order
(Kübler et al., 2009).

Therefore, in the following section, we will briefly introduce
dependency grammar, and give an overview of the differences among its
various representations.

## Dependency grammar

While dependency grammar has a rich history reaching back as far as the
descriptions of the Sanskrit language, its modern tradition is believed
to have begun with the French linguist Lucien Tesnière. In contrast to
phrase structure grammars, in dependency grammars, the central means of
describing linguistic structure is through words or tokens that are
linked by directed dependency relations. The elements of a dependency
relation are two words: the syntactically subordinate _dependent_ and
the word on which it depends, called the _head_ (or _governor_).
Furthermore, each dependency between two words is labeled by the _type_
of their relation, such as _subject_, _direct object_ or _attribute_.
Consider, for example, the simple dependency tree in
Figure 1.

--PARSETREE--

In this example, _likes_ is the head of both _Peter_ and _Mary_ and
their dependency relations indicate that _Peter_ is the subject () and
_Mary_ is the object dependent on the verb _likes_, while the verb
itself is a dependent of the artificial node. The node is inserted into
the tree as a technical simplification to ensure that every word has a
syntactic head.

### Formal definition

As we will rely on these definitions in the following chapters and
sections of this thesis, here we introduce the formal definition of
dependency trees and their properties by following the formulation from
Kübler et al. (2009).

A sentence $$S$$ is a sequence of tokens $$S = w_0w_1...w_n$$. The token
$$w_0$$ is treated as the artificial root token, which we labeled in
Figure [fig:simpledep]. While the term token is commonly used as a
synonym for a word in a sentence, depending on the language and
conventions used, it does not have to be a full word but can represent
single morphemes or punctuation.

Dependency relations are the relations between two words in the
sentence. $$R = \{r_1, ..., r_m\}$$ is the finite set of dependency
relation types that can hold between any two words. There are no further
assumptions about the set $$R$$, and the final set of relations depends on
the convention of the dependency format and the underlying linguistic
theory. In the example in Figure [fig:simpledep], the dependency types
are displayed as the labels of the arcs between the words: , and .

In order to define dependency trees, which are a special type of
dependency graphs, we first need to define dependency graphs. A
dependency graph can be defined as the following (slightly adapting the
definition from Kübler et al. (2009)): A dependency graph $$G = (V, A)$$
is a labeled directed graph consisting of nodes (vertices, $$V$$) and
edges (arcs, $$A$$), such that the following holds for $$S=w_0w_1...w_n$$
and the set of dependency types $$R$$:

1.  $$V \subseteq \{ w_0, w_1, ..., w_n \}$$
2.  $$A \subseteq V \times R \times V$$
3.  if $$(w_i, r, w_j) \in A$$ then $$(w_i, r', w_j) \not\in A$$ for all
    $$r' \not= r$$

An edge $$(w_i, r, w_j) \in A$$ represents a dependency relation from the
word $$w_i$$ to the word $$w_j$$ with the dependency type $$r$$. In this
dependency relation, $$w_i$$ is the head, and $$w_j$$ is the dependent node.
While the third condition disallows multiple dependency relations
between two words, it does not restrict words from having more than one
head. Most dependency grammar theories are based on dependency trees,
which are a further restriction of dependency graphs that we will define
now.

A _dependency tree_ is defined as a _well-formed_ dependency graph. A
dependency graph $$G$$ for a sentence $$S$$, and a dependency relation set
$$R$$ is called _well-formed_ if it is a directed tree originating in the
root node and if it has a spanning node set (i.e. a set of nodes
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

- $$w_i \to w_j$$ indicates an unlabeled dependency relation between
  $$w_i$$ and $$w_j$$ in a tree $$G = (V, A)$$. Hence, $$w_i \to w_j$$ means
  that there is some dependency relation type $$r \in R$$ such that
  $$(w_i, r, w_j) \in A$$.

- $$w_i \to^* w_j$$ indicates a _reflexive transitive closure_ of the
  dependency relation in a tree $$G = (V, A)$$. This is defined as
  $$w_i \to^* w_j$$ if and only if $$i = j$$ (_reflexive_) or both
  $$w_i \to^* w_{i'}$$ and $$w_{i'} \to w_j$$ hold for some
  $$w_{i'} \in V$$.

An edge in a dependency tree is projective if and only if
$$w_i \to^* w_k$$ for all $$i < k < j$$ when $$i < j$$, or $$j < k < i$$ when
$$j < i$$. Following this definition, an edge $$(w_i, r, w_j)$$ is
projective if there is a path from the head $$w_i$$ to all the words
between the two endpoints of the edge ($$i$$ and $$j$$). Accordingly, a
dependency tree $$G = (V, A)$$ is _projective_ if all
$$(w_i, r, w_j) \in A$$ are projective. A dependency tree that is not
projective is _non-projective_.

As examples of projective and non-projective dependency trees, consider
the two dependency trees in Figure [fig:projectivedeptree] and
Figure [fig:nonprojectivedeptree], which are dependency trees for
commonly used English example sentence from the Penn treebank (both
dependency trees are taken from Kübler et al. (2009)).

--PARSE TREE--

In this representation of dependency trees, with all words at the same
level, the dependency tree in Figure [fig:projectivedeptree] can be
drawn without crossing edges as all edges in this tree are projective.
For the dependency tree in Figure [fig:nonprojectivedeptree], however,
it is not possible to draw the tree without crossing edges. For the
dependency relation between _hearing_ and _on_, there is no path from
the head of the relation _hearing_ to the words in between the two
end-points of the edge, namely the words _is_ and _scheduled_. Hence,
the edge between _hearing_ and _on_ is not projective.

--PARSE-TREE--

## Data-driven dependency parsing

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
_Learning_ task, a parsing model $$M$$ is learned from a set of annotated
training instances (dependency trees). Then, in the _Parsing_ or
_Decoding_ task, the parsing model $$M$$ is used to produce the optimal
dependency graph $$G$$ for a sentence $$S$$.

## Maximum-spanning tree parsing

The _learning_ and _parsing_ tasks are implemented in various ways by
different parsers. A well-known algorithm is the Maximum Spanning Tree
parser (MST, McDonald et al. (2005)). In the following section, we will
briefly summarize how these two tasks are approached in the MST parser.

#### Learning: Online Large Margin Learning

The _learning_ task in this parser is approached as a supervised
learning problem for structured output. The score of a dependency tree
is factored as the sum of the scores of all edges in the tree. The score
for each edge is calculated as the dot product of a feature vector for
the edge, and the weight vector $$\textbf{w}$$.

$$s(i, j) = \textbf{w} \cdot \mathbf{f}(i, j)$$

Given a sentence $$\boldsymbol{x}$$, the score for a dependency tree
$$\boldsymbol{y}$$ is:

$$s(\boldsymbol{x}, \boldsymbol{y}) = \sum_{(i,j) \in \boldsymbol{y}}{s(i, j)}$$

To determine the weight vector $$\textbf{w}$$, a learning algorithm based on
the Margin Infused Relaxed Algorithm (MIRA, Crammer and Singer (2003))
is used. MIRA is an online learning algorithm similar to the online
version of the basic Perceptron learning algorithm (Rosenblatt, 1958).
Unlike a batch learning method, the online algorithm works by updating
the weight vector $$\textbf{w}$$ after each training instance it considers.

Pseudo-code for the MIRA algorithm is given in Algorithm [alg:MIRA].
$$dt(\boldsymbol{x})$$ is the set of possible dependency trees for the
sentence $$\boldsymbol{x}$$. The algorithm runs for $$N$$ iterations, and
during each of the iterations, it traverses all training instances, and
determines the optimal weight with regard to the loss function $$L$$. In
the case of dependency parsing, $$L$$ is the number of words in the
dependency tree with incorrect parent words compared to the correct
tree. After $$N$$ iterations, the intermediate weights stored in
$$\textbf{v}$$ are averaged, which has been shown to decrease the risk of
the model overfitting to the training data (Collins, 2002).

**Training data:** $$\tau = \{ (x_t, y_t) \}^T_{t=1}$$ min
$$|| \textbf{w}^{(i+1)} - \textbf{w}^{(i)} ||$$ s.t.
$$s(x_t, y_t) - s(x_t, y') \geq L(y_t, y'), \forall y' \in dt(x_t) $$

#### Decoding: Projective and non-projective trees

In the MST parser, the task of finding the optimal parse tree is
formulated as finding a maximum spanning tree for the words of the input
sentence, by using the edge scores, which were introduced above as
weights within the graph. For the projective and the non-projective
case, separate decoding algorithms are used. The projective decoding
algorithm is the Eisner algorithm (Eisner, 1996), which is a frequently
used $$O(n^3)$$ algorithm for maximum projective spanning trees. In the
non-projective case, the search for a suitable parse tree is performed
by searching for a maximum spanning tree in a directed acyclic graph
using the Chu-Liu-Edmonds algorithm (Chu and Liu, 1965; Edmonds, 1967).
Specifically, an implementation of the algorithm for dense graphs which
has complexity $$O(n^2)$$ is used.

# Parsing and the noisy-channel model

## The noisy-channel model

The noisy-channel model (Shannon, 1948) is a mathematical model for
communication that has been successfully applied to a wide variety of
natural language processing tasks. The original model was motivated by
the wish to transmit the maximum possible amount of information over a
noisy means of communication Manning and Schütze (1999). Today, this
model is the basis for a number of successful approaches to problems
such as machine translation and automatic spelling correction.

--noisy-channel--

In the noisy-channel model, a message is generated by the information
source and passed trough a noisy channel. The receiver is given the
resulting noisy data; and the receiver’s goal is to recover, or in other
words to _decode_, this noisy data in order to determine the original
message. Given observed data $$O$$ with the original source form $$S$$ for
which there exists some prior knowledge, this process is typically
modeled by using Bayes’ rule (Lease et al., 2006):

$$
\begin{aligned}
  \hat{s} = \text{argmax}_{S} p(S|O) = \text{argmax}_{S} p(O|S) p(S)\end{aligned}
$$

## Sentence comprehension under noisy input

In the psycholinguistics literature, a problem that is closely related
to parsing is the problem of human sentence comprehension. While most
research in this area assumes perfectly-formed input; Levy (2008)
proposes a noisy-channel based model of human sentence comprehension
that can account for some of the outstanding problems in sentence
processing. The model uses a generative probabilistic grammar. In the
standard case that the input string $$\textbf{w}$$ is fully known, the
grammar $$G$$ can be used to find the best parse $$T$$ for $$\textbf{w}$$ using

$$
\begin{aligned}
  \text{argmax}_T \mathrm{P}_G(T|\textbf{w})\end{aligned}
$$

However, in the case that the input string is not known, the formulation
changes to the following: Given some noisy evidence $$I$$ and using the
Bayes’ rule to find the posterior for $$\mathrm{P}_G(T|\textbf{w})$$ and
$$\mathrm{P}_G(T|I)$$:

$$
\mathrm{P}_G(T|I) = \frac{ p(T,I) }{ p(I) } \\
  \propto \sum_{ \textbf{w} } p(I|T,\textbf{w}) p(\textbf{w}|T) p(T)
$$

While not directly applying this model to parsing, Levy (2008) performs
a psycholinguistics experiment in which he assumes a noisy environment
distorting an original utterance. A comprehender is presented a sentence
$$\textbf{w}^*$$, which is known by the researchers. However, the specific
noisy representation $$I$$ of this sentence is not known. Based on the
formula in ([levyI]), for the probability of the comprehender’s
understood sentence $$\textbf{w}$$, we have:

$$ \mathrm{P}_G(\textbf{w}|I) \propto \sum_{ \textbf{w} } p(I|T,\textbf{w}) p(\textbf{w}|T) p(T)$$

In the controlled experiment of Levy (2008), the relevant probability
distribution is $$ p(\textbf{w}|\textbf{w}^\*)$$, which is given as

$$
\begin{aligned}
  p(\textbf{w}|\textbf{w}^*) &= \int_{ I } \mathrm{P}_C(\textbf{w}|I,\textbf{w}^*) \mathrm{P}_T(I|\textbf{w}^*)  df I\end{aligned}
$$

Then, since the comprehender does not know $$\textbf{w}^*$$, it is assumed
that $$\textbf{w}^*$$ and $$\textbf{w}$$ are conditionally independent. Applying
Bayes’ rule to (2), the following formulation is proposed
($$\mathrm{P}_C$$ is the probability distribution of the comprehender):

$$
\begin{aligned}
  p(\textbf{w}|\textbf{w}^*) &= \int_{ I } \frac{ \mathrm{P}_C(I|\textbf{w}) \mathrm{P}_C(\textbf{w}) }{ \mathrm{P}_C(I) }  \mathrm{P}_T(I|\textbf{w}^*) df I \\
   &= \mathrm{P}_C(\textbf{w}) \int_{ I } \frac{ \mathrm{P}_C(I|\textbf{w}) \mathrm{P}_T(I|\textbf{w}^*) }{ \mathrm{P}_C(I) } df I \\
   &\propto \mathrm{P}_C(\textbf{w}) Q(\textbf{w}, \textbf{w}^*)\end{aligned}
$$

$$Q(\textbf{w}, \textbf{w}^*)$$ in ([levyIV]) is proportional to the integral
in (3) and given some of the experiment’s assumptions; it is a
symmetric, non-negative function of $$\textbf{w}$$ and $$\textbf{w}^*$$. In the
rest of the paper, $$Q(\textbf{w}, \textbf{w}^*)$$ is implemented as a simple
Levensthein distance measure calculated via a token-based finite-state
automaton.

One of the arguments that is presented as supporting this model comes
from a simple prediction the model makes: the prior knowledge
$$\mathrm{P}_C(\textbf{w})$$ of the comprehender can overwrite the actual
linguistic input. Hence, a sentence can be interpreted as meaning
something else than it was originally expressed to mean. This is a
necessary requirement of such a model: A human copy editor, for example,
is without a question, able to read and correct erroneous writing.
Non-noisy models of sentence processing are able to cover this issue in
cases where the sentence is ungrammatical; however, the noisy model can
also account for cases where the sentence is fully grammatical but the
comprehender can still not process the sentence. This is the case in
certain garden path sentences, as in the following example from Levy
(2008):

a. While the man hunted the deer ran into the woods.
b. While the man hunted it the deer ran into the woods.

In this case, both sentences are grammatical sentences. For the sentence
in _a._, there is a grammatical reading; however, it is
ambiguous whether _the deer_ is the object of the verb _hunted_, or the
subject of the verb _ran_. In the case that it is read as the object of
_hunted_, the _ran_ will miss a subject, and the comprehender would
re-read the sentence as it “leads nowhere”. However, experiments in
which participants are given this sentence have shown that a large
number of participants initially perceive _the deer_ as the object of
_hunted_. Non-noisy models of sentence processing would not predict
this; however, it can be explained by the noisy model that can assume an
underlying sentence such as the sentence in _b._.

Note the similarity of the final model in () to well-established
noisy-channel methods for spelling correction, such as Kernighan et al.
(1990), where a correction $$c$$ for a text $$t$$ is found by maximizing
$$p(c) p(t|c)$$.

## References

Yoeng-Jin Chu and Tseng-Hong Liu. 1965. On the shortest arborescence of
a directed graph. _Science Sinica_, 14(1396-1400):270.

Michael Collins. 2002. Discriminative training methods for hidden markov
models: Theory and experiments with perceptron algorithms. In
_Proceedings of the ACL-02 Conference on Empirical Methods in Natural
Language Processing_, volume 10, pages 1–8, Philadelphia, PA.
Association for Computational Linguistics.

Koby Crammer and Yoram Singer. 2003. Ultraconservative online algorithms
for multiclass problems. _The Journal of Machine Learning Research_,
3:951–991.

Aron Culotta and Jeffrey Sorensen. 2004. Dependency tree kernels for
relation extraction. In _Proceedings of the 42nd Annual Meeting on
Association for Computational Linguistics_, page 423. Association for
Computational Linguistics.

Jack Edmonds. 1967. Optimum branchings. _Journal of Research of the
National Bureau of Standards B_, 71:233–240.

Jason M. Eisner. 1996. Three new probabilistic models for dependency
parsing: An exploration. In _Proceedings of the 16th Conference on
Computational Linguistics_, volume 1, pages 340–345. Association for
Computational Linguistics.

Mark D. Kernighan, Kenneth W. Church, and William A. Gale. 1990. A
spelling correction program based on a noisy channel model. In
_Proceedings of the 13th Conference on Computational Linguistics_,
volume 2, pages 205–210. Association for Computational Linguistics.

Sandra Kübler, Ryan McDonald, and Joakim Nivre. 2009. _Dependency
Parsing_.volume 2. Morgan & Claypool Publishers, editions.

Matthew Lease, Eugene Charniak, Mark Johnson, and David McClosky. 2006.
A Look at Parsing and Its Applications. In _Proceedings of the National
Conference on Artificial Intelligence_, volume 21, pages 1642–1645, No. 2. Menlo Park, CA; Cambridge, MA. MIT Press.

Roger Levy. 2008. A noisy-channel model of rational human sentence
comprehension under uncertain input. In _Proceedings of the 2008
Conference on Empirical Methods in Natural Language Processing_, pages
234–243. Association for Computational Linguistics.

Christopher D. Manning and Hinrich Schütze. 1999. _Foundations of
Statistical Natural Language Processing_. MIT press, editions.

Ryan T. McDonald, Fernando Pereira, Kiril Ribarov, and Jan Hajic. 2005.
Non-Projective Dependency Parsing using Spanning Tree Algorithms. In
_Proceedings of the conference on Human Language Technology and
Empirical Methods in Natural Language Processing._ Association for
Computational Linguistics.

Frank Rosenblatt. 1958. The perceptron. _Psychological Review_,
65(6):386–408.

Claude E. Shannon. 1948. A Mathematical Theory of Communication. _The
Bell System Technical Journal_, 27:379–423, 623–656, July, October.

Libin Shen, Jinxi Xu, and Ralph Weischedel. 2008. A new
string-to-dependency machine translation algorithm with a target
dependency language model. In _Proceedings of the 46th Annual Meeting of
the Association for Computational Linguistics: Human Language
Technologies_, pages 577–585. Association for Computational Linguistics.

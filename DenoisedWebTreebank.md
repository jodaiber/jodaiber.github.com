---
layout: default
title: The Denoised Web Treebank
---

We introduce the Denoised Web Treebank: a treebank including a normalization layer and a corresponding evaluation metric for dependency parsing of noisy text, such as Tweets. This benchmark enables the evaluation of text normalization methods, including normalization as machine translation and unsupervised lexical normalization, directly on syntactic trees.

## Documentation

For more information and documentation, please see [my 2013 Master thesis](http://jodaiber.github.io/doc/msc_thesis.pdf).

## Data

Download the treebank [here](http://jodaiber.github.io/data/denoised_web_treebank.tar.gz).

## Source code

All source code used in this paper is available under Apache 2.0 license on [Github: jodaiber/ithaka](https://github.com/jodaiber/ithaka).

## License

The treebank is licensed under Creative Commons (BY-NC-SA).

## File contents

The treebank cosists of the following files:

- `dev/test.ids`: IDs of the tweets that were the source of the sentence.
- `dev/test.tokens`: The original noisy tokens.
- `dev/test.normalized`: The manually normalized tokens including the alignments.
- `dev/test.conll`: Manually annotated dependency trees for each sentence (CONLL X format).

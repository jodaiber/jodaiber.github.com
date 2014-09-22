---
layout: default
title: Multilingual entity linking
---


## Multilingual entity linking

I created an efficient and more accurate version of the multilingual entity linking system [DBpedia Spotlight](https://github.com/dbpedia-spotlight/dbpedia-spotlight).

- [Github repo](https://github.com/dbpedia-spotlight/dbpedia-spotlight)
- [Models in various languages](http://spotlight.sztaki.hu/downloads/)


## Raw data

* **[Download the raw data here](http://spotlight.sztaki.hu/downloads/raw/)**

We provide the raw data that is used to create entity extraction models in various languages. This data is the result of running pignlproc on the latest Wikipedia dumps.

If you use this data in your research, please cite the following paper:

```bibtex
@inproceedings{isem2013daiber,
  title = {Improving Efficiency and Accuracy in Multilingual Entity Extraction},
  author = {Joachim Daiber and Max Jakob and Chris Hokamp and Pablo N. Mendes},
  year = {2013},
  booktitle = {Proceedings of the 9th International Conference on Semantic Systems (I-Semantics)}
}
```

[Download here](http://spotlight.sztaki.hu/downloads/raw/)

## Data format

- URIs are encoded in DBpedia format **but** redirects are not yet resolved. To do this, you can use the class [WikipediaToDBpediaClosure](https://github.com/dbpedia-spotlight/dbpedia-spotlight/blob/master/index/src/main/scala/org/dbpedia/spotlight/db/WikipediaToDBpediaClosure.scala), as used in `CreateSpotlightModel.scala`:
```scala
  val wikipediaToDBpediaClosure = new WikipediaToDBpediaClosure(
    namespace,
    new FileInputStream(new File(rawDataFolder, "redirects.nt")),
    new FileInputStream(new File(rawDataFolder, "disambiguations.nt"))
  )
```

### UriCounts
```
DBpedia URI                             Count
--------------------------------------------------------------
http://en.dbpedia.org/resource/1        21
http://en.dbpedia.org/resource/7        7
http://en.dbpedia.org/resource/C        20
```

### SfAndTotalCounts
```
Surface form         Count annotated    Count total
--------------------------------------------------------------
Berlin               49068              105915
Berloz               2                  6
9z                   -1                 1
```

- if no total string occurrence count is available, the 3rd column may be empty or -1
- if the annotated count is `-1`, then this is not a surface form that has been observed with any DBpedia resource. Lines with an annotated count of -1 are there to output the total count of the lowercase representations of surface forms.


### PairCounts
```
Surface form     DBpedia URI                                         Count
----------------------------------------------------------------------------
Berlin           http://en.dbpedia.org/resource/Brent_Berlin         2
Berlin           http://en.dbpedia.org/resource/Trams_in_Berlin      9
Berlin           http://en.dbpedia.org/resource/Berlin_(Seedorf)     1
```

### TokenCounts

```
Wikipedia URI                   Stemmed token counts
----------------------------------------------------------------------------
http://en.wikipedia.org/wiki/!  {(renam,76),(intel,14),...,(plai,2),(auf,2)}
```

- All tokens are stemmed






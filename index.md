---
layout: default
title: Joachim Daiber
---

About me
--------

I am a PhD student at the University of Amsterdam.

Previously, I was a Master's student in the [EM LCT](http://lct-master.org) programme in Computational Linguistics at Charles University in Prague and the University of Groningen. In my Master thesis, I worked on robust dependency parsing of noisy content with [Gertjan van Noord](http://www.let.rug.nl/vannoord/) and [Dan Zeman](http://ufal.mff.cuni.cz/daniel-zeman).

During my undergraduate studies at Freie Universität Berlin, I worked in the [META-NET](http://www.meta-net.eu) project at the German Research Center for Artifical Intelligence.

My office hours are Tuesdays 2pm-3pm in room F 1.22 at the ILLC.

Research interests
-------------------------

- **Statistical machine translation** <span style="width: 0.2em; display: inline-block;" ></span> My current work focuses on linguistically-informed statistical models for Machine Translation. I also wrote large parts of a [translation memory application for movie subtitles](https://github.com/runn1ng/FilmTit) (Scala).
- **Dependency parsing** <span style="width: 0.2em; display: inline-block;" ></span> I am interested in robust models of parsing, with a focus on dependency parsing.
- **Multilingual entity linking** <span style="width: 0.2em; display: inline-block;" ></span> I am interested in fast and accurate multilingual models for entity linking. See code, data and software [here](entity-linking).

Teaching
--------

- Fall 2015: Natural Language Processing 1 (Prof Ivan Titov)
- Spring 2015: Natural Language Processing 2 (Prof Khalil Sima'an)
- Fall 2014: [Natural Language Processing 1 (Prof Ivan Titov)](http://ivan-titov.org/teaching/nlp1-14/index.html)
- Spring 2014: [Natural Language Processing 2 (Prof Khalil Sima'an)](https://staff.fnwi.uva.nl/k.simaan/D-Courses2013/D-SSNLP2013/StatisticalStructureinNLP.html)



Connect
-------

-   [GitHub](http://github.com/jodaiber), [LinkedIn](https://www.linkedin.com/pub/joachim-daiber/84/279/93a), [Facebook](https://facebook.com/jodaiber)
-   Email: daiber.joachim [at] gmail.com.

<!--
Code & Data
-----------

-   I created an efficient and more accurate version of the multilingual entity linking system [DBpedia Spotlight](https://github.com/dbpedia-spotlight/dbpedia-spotlight) [Scala]
-   I wrote large parts of a [translation memory for movie subtitles](https://github.com/runn1ng/FilmTit) [Scala]

-->

Selected publications
---------------------
-  **Daiber, J.** and Sima'a, K. **Machine Translation with Source-Predicted Target Morphology.** Proceedings of MT Summit XV. 2015. Miami, USA. *(to appear)*
-   **Daiber, J.** and Jakob, M. and Hokamp, C. and Mendes, P.N. [Improving Efficiency and Accuracy in Multilingual Entity Extraction.](http://jodaiber.de/doc/entity.pdf) Proceedings of the 9th International Conference on Semantic Systems. 2013. Graz, Austria.
-   Mendes, P.N., **Daiber, J.**, Rajapakse, R., Sasaki, F., Bizer, C. [Evaluating the Impact of Phrase Recognition on Concept Tagging.](papers/LREC2012.pdf) Proceedings of the International Conference on Language Resources and Evaluation, LREC 2012. 21-27 May 2012. Istanbul, Turkey.
- [More on Google Scholar...](http://scholar.google.nl/citations?user=sApPUZUAAAAJ&hl=nl)

	{% for post in site.posts %}

{% if forloop.first %}

Blog Posts
----------

<ul class="posts">

{% endif %}

    {% if post.external_url %}
    	<li><span>{{ post.date | date_to_string }}</span> <span class="seperator">~</span> {{ post.category }}: <a href="{{ post.external_url }}">{{ post.title }}</a></li>
    {% else %}
    	<li><span>{{ post.date | date_to_string }}</span> <span class="seperator">~</span> {{ post.category }}: <a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}

 
{% if forloop.last %}

</ul>

{% endif %}

{% endfor %}


Personal
--------

<div id="instafeed"></div>

<script src="/js/instafeed.min.js"></script>
<script type="text/javascript">
    var feed = new Instafeed({
		get: 'user',
		userId: 601088313,
	    accessToken: '601088313.ab103e5.1b3ebae1bcc44eec9c0d207dceedfeb1',
		link: 'true',
		clientId: '',
		limit: '10'
    });
    feed.run();
</script>

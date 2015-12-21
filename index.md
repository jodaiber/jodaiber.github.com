---
layout: default
title: Joachim Daiber
---

About me
--------

I am a PhD student in the [Statistical Language Processing and Learning Lab](https://staff.fnwi.uva.nl/k.simaan/research_all.html) at the [ILLC, University of Amsterdam](https://www.illc.uva.nl/), where I work with [Prof. Khalil Sima'an](https://staff.fnwi.uva.nl/k.simaan/).

Previously, I was a Master's student in the [EM LCT](http://lct-master.org) programme in Computational Linguistics at Charles University in Prague and the University of Groningen. In my Master thesis, I worked on robust dependency parsing of noisy content with [Gertjan van Noord](http://www.let.rug.nl/vannoord/) and [Dan Zeman](http://ufal.mff.cuni.cz/daniel-zeman).

During my undergraduate studies at Freie Universität Berlin, I worked in the [META-NET](http://www.meta-net.eu) project at the German Research Center for Artifical Intelligence.

Connect at [GitHub](http://github.com/jodaiber), [LinkedIn](https://www.linkedin.com/pub/joachim-daiber/84/279/93a),  [Facebook](https://facebook.com/jodaiber) or write an email to daiber.joachim [at] gmail.com.

Research interests
-------------------------

- **Statistical machine translation** <span style="width: 0.2em; display: inline-block;" ></span> My current work focuses on linguistically-informed statistical models for MT. I also wrote large parts of a [translation memory application for movie subtitles](https://github.com/runn1ng/FilmTit) (Scala).
- **Dependency parsing** <span style="width: 0.2em; display: inline-block;" ></span> I am also interested in robust models of parsing, with a focus on dependency parsing.
- **Multilingual entity linking** <span style="width: 0.2em; display: inline-block;" ></span> I have worked on fast and accurate multilingual models for entity linking. See code, data and software [here](entity-linking).


Selected publications
---------------------
-  **Daiber, J.** and Sima'an, K. [Machine Translation with Source-Predicted Target Morphology.](doc/mtsummit2015.pdf) Proceedings of MT Summit XV. 2015. Miami, USA. [[Poster](doc/mtsummit2015_poster.pdf), [Slides](doc/clin2015_slides.pdf)]
-   **Daiber, J.**, Quiroz, L., Wechsler, R. and Frank, S. [Splitting Compounds by Semantic Analogy.](doc/compound_analogy.pdf) Proceedings of the first Deep Machine Translation Workshop. 2015. Prague, Czech Republic. [[Slides](doc/compound_analogy_slides.pdf)]
-   **Daiber, J.** and Sima'an, K. [Delimiting Morphosyntactic Search Space with Source-Side Reordering Models.](doc/preordering_spaces.pdf) Proceedings of the first Deep Machine Translation Workshop. 2015. Prague, Czech Republic. [[Slides](doc/preordering_spaces_slides.pdf)]
-   **Daiber, J.** and Jakob, M. and Hokamp, C. and Mendes, P.N. [Improving Efficiency and Accuracy in Multilingual Entity Extraction.](doc/entity.pdf) Proceedings of the 9th International Conference on Semantic Systems. 2013. Graz, Austria.
-   Mendes, P.N., **Daiber, J.**, Rajapakse, R., Sasaki, F., Bizer, C. [Evaluating the Impact of Phrase Recognition on Concept Tagging.](doc/LREC2012.pdf) Proceedings of the International Conference on Language Resources and Evaluation, LREC 2012. 21-27 May 2012. Istanbul, Turkey.
- [More on Google Scholar...](http://scholar.google.nl/citations?user=sApPUZUAAAAJ&hl=nl)

Resources
---------

- [Semantic analogy-based compound splitter](https://github.com/jodaiber/semantic_compound_splitting): An unsupervised compound splitter based on the regularities in the vector space of word embeddings.
- [The Denoised Web Treebank](DenoisedWebTreebank): Dependency treebank for evaluation of parser robustness.
- [FilmTit](https://github.com/runn1ng/FilmTit): Translation memory application for movie subtitles.
- [DBpedia Spotlight](http://spotlight.dbpedia.org/): I created an efficient and more accurate version of the multilingual entity linking system DBpedia Spotlight.
- [Raw Spotlight data](entity-linking): Raw counts for entity linking in many languages.



Teaching
--------

- Fall 2015: Natural Language Processing 1 (Prof Ivan Titov)
- Summer 2015: Profile Project AI-NLP (with Dr. Stella Frank)
- Spring 2015: Natural Language Processing 2 (Prof Khalil Sima'an)
- Fall 2014: Natural Language Processing 1 (Prof Ivan Titov)
- Spring 2014: Natural Language Processing 2 (Prof Khalil Sima'an)


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

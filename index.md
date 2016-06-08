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



## Research Interests

Within the area of Natural Language Processing, my research interests are 
in Machine Translation, Entity Linking and Dependency Parsing.

- [My publications](publications)
- [All publications on Google Scholar](http://scholar.google.nl/citations?user=sApPUZUAAAAJ)

## Software and data

- [Semantic analogy-based compound splitter](https://github.com/jodaiber/semantic_compound_splitting): An unsupervised compound splitter based on the regularities in the vector space of word embeddings.
- [The Denoised Web Treebank](DenoisedWebTreebank): Dependency treebank for evaluation of parser robustness.
- [FilmTit](https://github.com/runn1ng/FilmTit): Translation memory application for movie subtitles.
- [DBpedia Spotlight](http://spotlight.dbpedia.org/): I created an efficient and more accurate version of the multilingual entity linking system DBpedia Spotlight.
- [Raw Spotlight data](entity-linking): Raw counts for entity linking in many languages.


## Professional activities

### Teaching:
- Natural Language Processing 1  
  Prof Ivan Titov. Fall 2015, Fall 2014.
- Natural Language Processing 2  
  Prof Khalil Sima'an. Spring 2016, Spring 2015, Spring 2014.
- Summer 2015: Profile Project AI-NLP  
  with Dr. Stella Frank

### Reviewing:
- International Journal of Cooperative Information Systems (IJCIS)
- NAACL 2016 Workshop on Discontinuous Structures in NLP

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

---
layout: default
title: Joachim Daiber
---

About me
--------

I am an applied scientist focused on natural language processing and machine learning. I recently started something new at [Objective, Inc.](https://www.objective.inc).
Previously, I was a Staff Machine Learning Engineer at Apple in California.

I received my PhD at the [University of Amsterdam](https://www.illc.uva.nl/), where I worked with [Prof. Khalil Sima'an](https://staff.fnwi.uva.nl/k.simaan/) on machine translation. From 2011 until 2013, I was a Master's student in the [EM LCT](http://lct-master.org) programme in Computational Linguistics at Charles University in Prague and the University of Groningen. In my Master thesis, I worked on robust dependency parsing of noisy content with [Gertjan van Noord](http://www.let.rug.nl/vannoord/) and [Dan Zeman](http://ufal.mff.cuni.cz/daniel-zeman). During my undergraduate studies at Freie Universität Berlin, I worked at the German Research Center for Artifical Intelligence.

See my full CV [here](/doc/CV.pdf) or connect at [GitHub](http://github.com/jodaiber), [LinkedIn](https://www.linkedin.com/pub/joachim-daiber/84/279/93a) or write an email to daiber.joachim [at] gmail.com.



## Research Interests

Within the area of Natural Language Processing, my research interests are 
in applications and evaluation of large language and vision models, machine translation, entity linking and dependency parsing.

- [See my publications on Google Scholar](http://scholar.google.nl/citations?user=sApPUZUAAAAJ)


## Software and data

- [Semantic analogy-based compound splitter](https://github.com/jodaiber/semantic_compound_splitting): An unsupervised compound splitter based on the regularities in the vector space of word embeddings.
- [The Denoised Web Treebank](DenoisedWebTreebank): Dependency treebank for evaluation of parser robustness.
- [FilmTit](https://github.com/runn1ng/FilmTit): Translation memory application for movie subtitles.
- [DBpedia Spotlight](http://spotlight.dbpedia.org/): I created an efficient and more accurate version of the multilingual entity linking system DBpedia Spotlight.
- [Raw Spotlight data](entity-linking): Raw counts for entity linking in many languages.


<!--## Professional activities

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

-->

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
<div id="frontpage">
  <div id="instafeed"></div>
</div>

[More photos...](photography)

<script src="/js/instafeed.min.js"></script>
<script type="text/javascript">
    var feed = new Instafeed({
		get: 'user',
		userId: 601088313,
    accessToken: '601088313.1677ed0.df46ed351a5f44bab606823c253be9ff',
		link: 'true',
		limit: '16'
    });
    feed.run();
</script>

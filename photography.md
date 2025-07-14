---
layout: photos
title: Photography
---

<div id="instafeed"></div>

<script src="{{ '/js/instafeed.js' | relative_url }}"></script>

{% raw %}

<script type="text/javascript">
    var feed = new Instafeed({
		get: 'user',
		userId: 601088313,
        accessToken: '601088313.1677ed0.df46ed351a5f44bab606823c253be9ff',
		link: 'true',
		limit: '64',
        resolution: 'standard_resolution',
        template: '<div class="photo"><a class="image" href="{{link}}"><img src="{{image}}" /></a><div class="caption">{{caption}}</div></div>'
    });
    feed.run();
</script>

{% endraw %}

---
layout: default
permalink: /tags/
title: Tags
---
<h2>Tags</h2>

<div class="home">
	<p class="post-meta" style="text-align: justify;">
	{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
	{% assign tags = site_tags | split:',' | sort %}
	{% include tagcloud.html %}
	</p>
</div>


<h2 class="page-heading">Posts with #tag</h2>
{% for tag in site.tags %}
  <div class="archive-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
		<a name="{{ tag_name | slugize }}"></a>
    <div id="#{{ tag_name | slugize }}"></div>
    <h3 class="tag-head">#{{ tag_name }} ({{ site.tags[tag_name].size }})</h3>
    {% for post in site.tags[tag_name] %}
    <article class="archive-item">
      <p><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></p>
    </article>
    {% endfor %}
  </div>
{% endfor %}

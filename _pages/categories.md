---
layout: default
permalink: /categories/
title: Categories
---
<h2>Categories</h2>

<div class="home">
	<p class="post-meta" style="text-align: justify;">
	{% capture site_categories %}{% for category in site.categories %}{{ category | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
	{% assign categories = site_categories | split:',' | sort %}
	{% include categorycloud.html %}
	</p>
</div>

<hr size=20>

<h2 class="page-heading">Posts with Category</h2>
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
		<a name="{{ category_name | slugize }}"></a>
    <div id="#{{ category_name | slugize }}"></div>
    <h3 class="category-head">{{ category_name }} ({{ site.categories[category_name].size }})</h3>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <p><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></p>
    </article>
    {% endfor %}
  </div>
{% endfor %}

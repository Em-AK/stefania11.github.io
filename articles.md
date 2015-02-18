---
layout: post
permalink: /articles/index.html
title: "Letters from a curious mind"
tags: [blog, graphic design]
image:
feature: "typewriter_bw.png"
---
{% for post in site.posts %}
<li>
  <div class="deets" itemscope itemtype="http://schema.org/BlogPosting" itemprop="blogPost">
      <h1><a href="{{ site.url }}{{ post.url }}">{{ post.title }}</a></h1>
      <p class="date"><time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></p>
      <p class="">{% if post.description %}{{ post.description  | strip_html | strip_newlines | truncate: 120 }}{% else %}{{ post.content | strip_html | strip_newlines | truncate: 120 }}{% endif %}</p>
  </div>
</li>
{% endfor %}

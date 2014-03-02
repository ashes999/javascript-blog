---
layout: page
title: Ashes999's Javascript Blog
tagline: Writing Javascript code all the time
---
{% include JB/setup %}

<p>Interested in Javascript? Me, too. Below are some of my posts on various topics related to JS development.</p>

<p><strong>Posts:</strong></p>

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


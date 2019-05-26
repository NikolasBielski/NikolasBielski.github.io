---
title: "Tags"
permalink: /tags/
comments: true
---

{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}

{% assign tag_words = site_tags | split:',' | sort %}

{% for item in (0..site.tags.size) %}{% unless forloop.last %} {% capture this_word %}{{ tag_words[item] | strip_newlines }}{% endcapture %}
{{ this_word }} {{ site.tags[this_word].size }}
{% endunless %}{% endfor %}

{% for item in (0..site.tags.size) %}{% unless forloop.last %} {% capture this_word %}{{ tag_words[item] | strip_newlines }}{% endcapture %}
{{ this_word }}

{% for post in site.tags[this_word] %}{% if post.title != null %}
{{ post.date | date: "%B %d, %Y" }} » {{ post.title }}
{% endif %}{% endfor %}

{% endunless %}{% endfor %} 

---
title: "Blog"
permalink: /blog/
author_profile: true
comments: true
---

{% include base_path %}
{% include group-by-array collection=site.posts field=t"tags" %}

{% for tag in group_names %}
    {% assign posts=group_items[forloop.index0] %}
    <h2 id="{{ tag | slugify }}" class="archive__substitute">{{ tag }}</h2>
    {% for post in posts %}
        {% include archive-single.html %}
    {% endfor %}
{% endfor %}

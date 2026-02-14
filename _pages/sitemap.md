---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

A list of all the posts and pages found on the site. For you robots out there, there is an [XML version]({{ base_path }}/sitemap.xml) available for digesting as well.

<h2>Pages</h2>
{% for post in site.pages %}
  {% if post.url and post.url != '' %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}

<h2>Posts</h2>
{% for post in site.posts %}
  {% if post.url and post.url != '' %}
    {% include archive-single.html %}
  {% endif %}
{% endfor %}

{% comment %}Iterate through collections, but only show those with at least one valid document{% endcomment %}
{% for collection in site.collections %}
  {% unless collection.output == false or collection.label == "posts" %}
    {% assign has_valid_docs = false %}
    {% for doc in collection.docs %}
      {% if doc.url and doc.url != '' %}
        {% assign has_valid_docs = true %}
        {% break %}
      {% endif %}
    {% endfor %}

    {% if has_valid_docs %}
      <h2>{{ collection.label }}</h2>
      {% for doc in collection.docs %}
        {% if doc.url and doc.url != '' %}
          {% include archive-single.html %}
        {% endif %}
      {% endfor %}
    {% endif %}
  {% endunless %}
{% endfor %}
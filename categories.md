---
bg: "tag.jpg"
layout: page
permalink: /categories/
title: "Categories"
crawlertitle: "Categories wise all articles"
summary: "This page contains all articles accourding to their specified categories."
active: categories
---

{% for cat in site.categories %}
  {% assign t = cat | first %}
  {% assign posts = cat | last %}

  <h2 class="category-key" id="{{ t | downcase }}">{{ t | capitalize }}</h2>

  <ul class="year">
    {% for post in posts reversed%}
      {% if post.categories contains t %}
        <li>
          {% if post.lastmod %}
            <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
            <span class="date">{{ post.lastmod | date: "%d-%m-%Y"  }}</span>
          {% else %}
            <a href="{{ post.url | relative_url}}">{{ post.title }}</a>
            <span class="date">{{ post.date | date: "%d-%m-%Y"  }}</span>
          {% endif %}
        </li>
      {% endif %}
    {% endfor %}
  </ul>

{% endfor %}

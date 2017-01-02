---
layout: home
title: BeyondClick Blog
---
<h1>{{ page.title }}</h1>

<ul class="posts">
  {% for post in site.posts %}
    <li class="post" itemscope itemtype="http://schema.org/Article">
      <h1 itemprop="name"><a href="{{ post.url }}" class="anchor">{{ post.title }}</a></h1>
      <p>
        <span itemprop="datePublished" content="{{ post.date | date: "%Y-%m-%d"}}">{{ post.date | date_to_string }}</span> |
        <a href="{{ site.url }}{{ post.url }}#disqus_thread"></a>
      </p>
      <p itemprop="headline">
        {{ post.excerpt }}
      </p>
      <p class="tags" itemprop="keywords">
        {{ post.tags | array_to_sentence_string }}
      </p>
    </li>
  {% endfor %}
</ul>

{% include comments_providers/disqus module="count" %}

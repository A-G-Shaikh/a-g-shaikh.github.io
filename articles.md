---
layout: default
title: Articles
permalink: /articles/
---

<div class="page-content">
  <h1 class="page-title">Articles</h1>
  
  <p class="lead">Browse all articles</p>
  
  <div class="articles-list">
    {% assign sorted_posts = site.posts | sort: 'date' | reverse %}
    {% for post in sorted_posts %}
      <article class="article-item">
        <!-- div class="article-metadata">
          <span class="article-date">{{ post.date | date: site.date_format }}</span>
          {% if post.categories.size > 0 %}
            <span class="article-categories">
              {% for category in post.categories %}
                <a href="{{ '/categories/#' | append: category | slugify | relative_url }}" class="article-category">{{ category }}</a>{% unless forloop.last %},{% endunless %}
              {% endfor %}
            </span>
          {% endif %}
        </div -->
        
        <h2 class="article-title">
          <a class="article-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h2>
        
        {%- if post.image -%}
          <div class="card-image">
            <img 
              src="{{ '/assets/images/' | append: post.image | relative_url }}" 
              alt="{{ post.title }}" 
              width="400" 
              height="125" 
            />
          </div>
        {% else %}
          <!-- Generate CSS featured image for posts without specified images -->
          <div class="post-featured-image css-featured-image" 
               data-pattern="{{ page.title | size | modulo: 6 }}" 
               data-title="{{ page.title | slice: 0 | upcase }}">
            <div class="css-image-title">{{ page.title | slice: 0 | upcase }}</div>
          </div>
        {%- endif -%}
        

        
        {% if post.description %}
          <p class="article-excerpt">{{ post.description }}</p>
        {% elsif post.excerpt %}
          <p class="article-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
        {% endif %}
        
        
        <a href="{{ post.url | relative_url }}" class="read-more">Read more →</a>
      </article>
    {% endfor %}
  </div>
</div>

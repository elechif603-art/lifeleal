---
layout: default
---

<section class="hero">
    <div class="wrapper">
        <h1>Welcome to LifeLeal</h1>
        <p>Your Comprehensive Guide to Postal Codes & Regional Data</p>
    </div>
</section>

<div class="container">
    <section class="posts-list">
        <h2 style="text-align: center; margin-bottom: 40px; font-size: 2.2em; color: #2c3e50;">Latest Articles</h2>
        
        {% for post in site.posts limit:10 %}
            <article class="post-preview">
                <h2 class="post-title"><a href="{{ post.url | relative_url }}">{{ post.title | default: "Untitled Post" }}</a></h2>
                <div class="post-meta">
                    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
                    {% if post.author %}
                        <span class="post-author">By {{ post.author }}</span>
                    {% endif %}
                </div>

                {% assign summary = post.excerpt | default: post.content %}
                <p class="post-excerpt">{{ summary | strip_html | truncatewords: 30 }}</p>

                <a href="{{ post.url | relative_url }}" class="read-more">Read Full Article →</a>
            </article>
        {% endfor %}
    </section>

    <div style="text-align: center; margin-top: 50px;">
        <p style="color: #666; font-size: 1.1em;">Explore {{ site.posts | size }} comprehensive articles on postal codes and regional data</p>
    </div>
</div>

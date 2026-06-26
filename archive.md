---
layout: default
title: Archive
permalink: /archive/
---

<div class="archive-page">
    <h1>Blog Archive</h1>
    <p class="archive-intro">Browse all {{ site.posts.size }} posts from LifeLeal.</p>

    <div class="archive-container">
        {% capture currentYear %}{{ 'now' | date: '%Y' }}{% endcapture %}
        {% capture currentMonth %}{% endcapture %}
        {% capture currentYearDisplay %}{% endcapture %}

        {% for post in site.posts %}
            {% capture postYear %}{{ post.date | date: '%Y' }}{% endcapture %}
            {% capture postMonth %}{{ post.date | date: '%B' }}{% endcapture %}

            {% if postYear != currentYearDisplay %}
                {% if currentYearDisplay != empty %}</ul>{% endif %}
                <h2 class="archive-year">{{ postYear }}</h2>
                <ul class="archive-list">
                {% capture currentYearDisplay %}{{ postYear }}{% endcapture %}
            {% endif %}

            <li class="archive-item">
                <span class="archive-date">{{ post.date | date: "%B %d, %Y" }}</span>
                <a href="{{ post.url | relative_url }}" class="archive-link">{{ post.title }}</a>
                {% if post.categories %}
                    <span class="archive-category">
                        {% for category in post.categories limit:1 %}
                            <a href="{{ '/category/' | append: category | downcase | replace: ' ', '-' | append: '/' | relative_url }}">{{ category }}</a>
                        {% endfor %}
                    </span>
                {% endif %}
            </li>
        {% endfor %}
        </ul>
    </div>
</div>

<style>
.archive-page {
    max-width: 800px;
    margin: 2rem auto;
    padding: 0 1rem;
}

.archive-intro {
    font-size: 1.1rem;
    color: #666;
    margin-bottom: 2rem;
}

.archive-year {
    font-size: 1.8rem;
    margin-top: 2rem;
    margin-bottom: 1rem;
    color: #333;
    border-bottom: 2px solid #007bff;
    padding-bottom: 0.5rem;
}

.archive-list {
    list-style: none;
    padding: 0;
}

.archive-item {
    display: flex;
    align-items: center;
    gap: 1.5rem;
    padding: 0.75rem 0;
    border-bottom: 1px solid #eee;
}

.archive-item:last-child {
    border-bottom: none;
}

.archive-date {
    min-width: 140px;
    color: #999;
    font-size: 0.9rem;
}

.archive-link {
    flex: 1;
    color: #007bff;
    text-decoration: none;
    font-weight: 500;
}

.archive-link:hover {
    text-decoration: underline;
    color: #0056b3;
}

.archive-category {
    background-color: #f0f0f0;
    padding: 0.25rem 0.75rem;
    border-radius: 20px;
    font-size: 0.85rem;
}

.archive-category a {
    color: #666;
    text-decoration: none;
}

.archive-category a:hover {
    color: #007bff;
}

@media (max-width: 768px) {
    .archive-item {
        flex-direction: column;
        align-items: flex-start;
        gap: 0.5rem;
    }
    
    .archive-date {
        min-width: auto;
    }
}
</style>

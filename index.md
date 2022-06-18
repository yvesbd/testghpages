---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
<!--
site: {{ site.posts | inspect }}
<br>
paginate: {{ paginate.posts | inspect }}
<br>
paginator: {{ paginator.posts | inspect }}
<br>
-->
{% assign posts_count = paginate.posts | size %}
{% if posts_count > 0 %}
<h1>recent articles</h1>
  <div class="post-links">
    
      {% for post in paginate.posts %}
        <div class="post-link-wrapper">
          <a href="{{ post.url | relative_url }}" class="post-link">{{ post.title }}</a>
          <div class="post-meta">

            {% if site.plugins contains "jekyll/tagging" %}
            <div class="post-tags">
                {% for tag in post.tags %}
                <a class="tag" href="{{ tag | tag_url }}">{{ tag }}</a>
                {% endfor %}
            </div>
            {% endif %}
            {% if site.dash.date_format %}
              {{ post.date | date: site.dash.date_format }}
            {% else %}
              {{ post.date | date: "%b %-d, %Y" }}
            {% endif %}
            {% if site.show_excerpts == true %}
              <div class="post-excerpt">
                {{ post.content | strip_html | truncatewords: 50 }}
              </div>
            {% endif %}
          </div>
        </div>
      {% endfor %}
  </div>
  {% include pagination.html %}
  {% include tagcloud.html %}
{% else %}
<h2>no posts yet.</h2>
{% endif %}
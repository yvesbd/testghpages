---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
Testing modification from remote / git push
<br>
{% assign posts_count = paginator.posts | size %}
{% if posts_count > 0 %}
<h1>recent articles</h1>
    <div class="post-links">
      {% for post in paginator.posts %}
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



<!--
## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/yvesbd/testghpages/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/yvesbd/testghpages/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
-->

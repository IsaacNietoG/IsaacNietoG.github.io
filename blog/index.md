---
layout: default
---
# All my posts
<ul>
            {% for post in site.posts limit:3 %}
                <li>
                    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
                    <p>{{ post.excerpt }}</p>
                    <p><small>{{ post.date | date: "%d %B, %Y" }}</small></p>
                </li>
            {% endfor %}
        </ul>


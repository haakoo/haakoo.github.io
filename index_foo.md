---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

---

This will be my new _home_ for my blog. Just have to finish migrating old posts.

# Latest Post
{% for post in site.posts limit:1 %}
... Show the first post all big ...
{% endfor %}

# Recent Posts
{% for post in site.posts offset:1 limit:2 %}
... Show the next two posts ...
{% endfor %}

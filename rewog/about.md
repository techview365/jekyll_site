---
title: About
description: About Gnoppix Linux
layout: about
---

{% assign posts = site.posts | sort: "date" | sort: "updated" | reverse %}

{% for post in posts %}
    {% include posts-listing.html post=post %}
{% endfor %}
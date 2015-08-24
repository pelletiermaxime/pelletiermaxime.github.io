---
layout: post
title: Creating, documenting and testing an API in PHP [1/4]
---

# {{ page.title }}

{% include API-toc.markdown %}

In this series of post I will create a REST API to create/read/update/delete (CRUD) Users. On the way I will show off a few tools to help design, document, test and, of course, code the API because we do want to create and ship something! To do this, i'm going to use the API Blueprint specs, a few tools and use that standard and a Laravel package called Dingo API.

There's sereval ways to start doing this. We could write the urls of all our api endpoints, we could draw a diagram, we could create our routes file and the controller methods or we could write the documentation.
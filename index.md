---
layout: default
---


{% for post in site.posts limit:10 %}
  <h2 class="post-title">
    <a href="{{post.url | prepend:site.baseurl | prepend:site.url}}">
      {{ post.title }}
    </a>
  </h2>

  <div class="post-descr">
      Description: {{ post.description }}
  </div>

  <ul id="tags">
    {% for tag in post.tags %}
    <!--<li><a href="{{site.baseurl | prepend:site.url}}/tag/{{ tag }}">{{ tag }}</a>|</li> -->
    <li >{{ tag }} | </li>
    {% endfor %}
  </ul>

  <div class="post-meta">
  <div class="post-time">
    <i class="fa fa-calendar"></i>
    <time datetime='{{ post.date | date: "%Y-%m-%d" }}'>{{ post.date | date_to_string }}</time>
    <br><br>
  </div>

</div>


  {% endfor %}


<!--<div class="post-footer">
  <div class="column-full">
    <h3><a href="{{ '/archive.html' | prepend: site.baseurl | prepend: site.url }}">Blog archive</a></h3>
  </div>
</div>-->

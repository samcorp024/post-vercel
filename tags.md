---
layout: default
permalink: /tags/
---

<!-- <h1>Tags</h1> -->

<div class="tags-container">
  {% for tag in site.tags %}
    <div class="tag-card">
      <a href="{{ site.baseurl }}/tags/?tag={{ tag[0] | slugify }}" class="tag-link">{{ tag[0] }}</a>
    </div>
  {% endfor %}
</div>

<h2 id="tag-title"></h2>
<div style="margin-top:20px; margin-bottom:20px" class="posts-container">
  {% for post in site.posts %}
    <div class="post-card" data-tags="{{ post.tags | join: ',' }}">
      {% if post.image %}
        <img src="{{ post.image | absolute_url }}" alt="{{ post.title }}">
      {% endif %}
      <h2><a href="{{ post.url | absolute_url }}">{{ post.title }}</a></h2>
      <p class="discription">{{ post.excerpt | strip_html | truncate: 150 }}</p>
      <a href="{{ post.url | absolute_url }}" class="read-more">Read More</a>
    </div>
  {% endfor %}
</div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const urlParams = new URLSearchParams(window.location.search);
    const tag = urlParams.get('tag');

    if (tag) {
      // Set tag title
      document.getElementById('tag-title').textContent = 'Posts tagged with "' + tag + '"';

      // Highlight the active tag-card
      const tagCards = document.querySelectorAll('.tag-card');
      tagCards.forEach(function(card) {
        if (card.textContent.trim().toLowerCase() === tag.toLowerCase()) {
          card.classList.add('active');
        }
      });

      // Filter posts by tag
      const posts = document.querySelectorAll('.post-card');
      posts.forEach(function(post) {
        if (post.getAttribute('data-tags').includes(tag)) {
          post.style.display = 'block';
        } else {
          post.style.display = 'none';
        }
      });
    } else {
      // If no tag is selected, hide the posts section
      document.getElementById('tag-title').style.display = 'none';
    }
  });
</script>



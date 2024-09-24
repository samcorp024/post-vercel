---
layout: default
title: Blockchain
permalink: /categories/blockchain-game-development/
description: "Posts related to Casino game development."
---
<style>
  /* Existing styles */
  .posts-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: start;
    gap: 15px;
  }

  .post-card {
    background-color: #f9f9f9;
    border-radius: 8px;
    position:relative;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    width: calc(100% / 3 - 20px);
    max-width: 290px;
    transition: transform 0.3s ease;
    padding: 6px;
  }

  .post-card img {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  .post-card h2 {
    font-size: 1.5em;
    margin: 16px;
    color: #333;
  }

  .post-card p {
    margin: 0 16px 16px;
    color: #666;
  }

  .read-more {
    display: block;
    text-align: center;
    padding: 10px;
    margin-top: auto;
    position:absolute;
    bottom:5px;
    width:90%;
    background-color: #0073e6;
    color: white;
    text-decoration: none;
    border-radius: 0 0 8px 8px;
    font-weight: bold;
  }

  .read-more:hover {
    background-color: #005bb5;
  }

  .post-card:hover {
    transform: translateY(-5px);
  }

  /* Responsive */
  @media (max-width: 768px) {
    .post-card {
      width: calc(100% / 2 - 20px);
    }
  }

  @media (max-width: 480px) {
    .post-card {
      width: 100%;
    }
  }

  /* Pagination styles */
  .pagination {
    text-align: center;
    margin-top: 20px;
  }
  #page-numbers{
    width:50px !important;
    border-radius  :50px !important;
  }
  .page-number{
    width:50px !important;
    border-radius  :50px !important;

  }
  .active {
    width:50px !important;
    border-radius  :50px !important;
    background-color: #54a0ef !important;
    color:black !important;

  }
  .pagination button {
    background-color: #0073e6;
    color: white;
    border: none;
    padding: 10px 20px;
    margin: 20px 5px;
    border-radius: 5px;
    cursor: pointer;
    width:100px
    
  }

  .pagination button.disabled {
    background-color: #cccccc;
    cursor: not-allowed;
  }
</style>

<h1>Casino Posts</h1>

<div class="posts-container">
  {% assign category = 'casino' %}
  {% for post in site.posts %}
    {% if post.categories contains category %}
      <div class="post-card">
        {% if post.image %}
          <img src="{{ post.image | absolute_url }}" alt="{{ post.title }}">
        {% endif %}
        <h2><a href="{{ post.url | absolute_url }}">{{ post.title }}</a></h2>
        <p class="discription">{{ post.excerpt | strip_html | truncate: 150 }}</p>
        <a href="{{ post.url | absolute_url }}" class="read-more">Read More</a>
      </div>
    {% endif %}
  {% endfor %}
</div>

<div class="pagination">
  <button id="prev-page">Previous</button>
  <span id="page-numbers"></span>
  <button id="next-page">Next</button>
</div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const postsPerPage = 6;
    const posts = Array.from(document.querySelectorAll('.post-card'));
    let currentPage = 1;
    const totalPages = Math.ceil(posts.length / postsPerPage);

    function showPage(page) {
      const startIndex = (page - 1) * postsPerPage;
      const endIndex = startIndex + postsPerPage;

      posts.forEach((post, index) => {
        post.style.display = (index >= startIndex && index < endIndex) ? 'block' : 'none';
      });

      updatePageNumbers(page);
      document.getElementById('prev-page').classList.toggle('disabled', page === 1);
      document.getElementById('next-page').classList.toggle('disabled', page === totalPages);
    }

    function updatePageNumbers(page) {
      const pageNumbers = document.getElementById('page-numbers');
      pageNumbers.innerHTML = '';

      for (let i = Math.max(1, page - 3); i <= Math.min(totalPages, page + 3); i++) {
        const pageNumber = document.createElement('button');
        pageNumber.textContent = i;
        pageNumber.className = 'page-number';
        if (i === page) {
          pageNumber.classList.add('active');
        }
        pageNumber.addEventListener('click', function() {
          currentPage = i;
          showPage(currentPage);
        });
        pageNumbers.appendChild(pageNumber);
      }
    }

    document.getElementById('prev-page').addEventListener('click', function() {
      if (currentPage > 1) {
        currentPage--;
        showPage(currentPage);
      }
    });

    document.getElementById('next-page').addEventListener('click', function() {
      if (currentPage < totalPages) {
        currentPage++;
        showPage(currentPage);
      }
    });

    // Initial display
    showPage(currentPage);
  });
</script>

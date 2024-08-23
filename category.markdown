---
layout: page
title: Categorys
permalink: /category/
---
<style>
  .posts-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: start;
    gap: 15px;
  }

  .post-card {
    background-color: #f9f9f9;
    border-radius: 8px;
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
    background-color: #0073e6;
    color: white;
    text-decoration: none;
    border-radius: 0 0 8px 8px;
    font-weight: bold;
  }
  .read-more:hover {
    display: block;
    text-align: center;
    padding: 10px;
    margin-top: auto;
    background-color: #0073e6;
    color: black;
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
</style>
<h1>Categories</h1>
<ul>
  <li><a href="/categories/casino/">Casino</a></li>
  <li><a href="/categories/game-development/">Game Development</a></li>
</ul>

---
layout: page
permalink: /code/
title: code
nav: true
nav_order: 3
---

<style>
.repo-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1em;
  justify-content: space-between;
}
.repo-card {
  flex: 1 1 calc(50% - 1em);
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 1em;
  box-shadow: 2px 2px 5px rgba(0,0,0,0.05);
  background-color: #fdfdfd;
  text-align: center;
  box-sizing: border-box;
  max-width: calc(50% - 1em);
}
.repo-card img {
  max-width: 100%;
  max-height: 150px;
  object-fit: contain;
  margin-bottom: 0.5em;
}
.repo-card h3 {
  margin: 0.5em 0;
  font-size: 1.1em;
}
</style>

<div class="repo-grid">

  <div class="repo-card">
    <h3>
      <a class="publink" href="https://github.com/borjanG/2025-transformers-frank-wolfe">
        are Transformers Frank-Wolfe in disguise?
      </a>
    </h3>
    <img src="{{ '/assets/img/cells.png' | relative_url }}" alt="transformers frank-wolfe preview">
  </div>

  <div class="repo-card">
    <h3>
      <a class="publink" href="https://github.com/KimiSun18/2024-gauss-kde-attention">
        number of modes of Gaussian KDEs
      </a>
    </h3>
    <img src="{{ '/assets/img/5.gif' | relative_url }}" alt="gaussian KDE preview">
  </div>

  <div class="repo-card">
    <h3>
      <a class="publink" href="https://github.com/HugoKoubbi/2024-transformers-dotm">
        dynamic metastability in the self-attention model
      </a>
    </h3>
    <img src="{{ '/assets/img/in-rainbows.png' | relative_url }}" alt="transformers metastability preview">
  </div>

  <div class="repo-card">
    <h3>
      <a class="publink" href="https://github.com/borjanG/2023-transformers-rotf">
        a mathematical perspective on Transformers
      </a>
    </h3>
    <img src="{{ '/assets/img/1.gif' | relative_url }}" alt="transformers ROTF preview">
  </div>

  <div class="repo-card">
    <h3>
      <a class="publink" href="https://github.com/borjanG/2023-transformers">
        emergence of clusters in self-attention dynamics
      </a>
    </h3>
    <img src="{{ '/assets/img/2.gif' | relative_url }}" alt="self-attention clusters preview">
  </div>

  <div class="repo-card">
    <h3>
      <a class="publink" href="https://github.com/borjanG/leia">
        neural ODEs
      </a>
    </h3>
    <img src="{{ '/assets/img/4.gif' | relative_url }}" alt="neural ODEs preview">
  </div>

  <div class="repo-card">
    <h3>
      <a class="publink" href="https://github.com/borjanG/2022-stefan-control">
        control of the Stefan problem
      </a>
    </h3>
    <img src="{{ '/assets/img/3.gif' |relative_url }}" alt="Stefan problem preview">
  </div>

</div>

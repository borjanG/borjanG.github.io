---
layout: page
permalink: /code/
title: code
nav: true
nav_order: 3
---

<style>
:root {
  --link-hover-color: #0070c9;  /* Replace with your real .publink hover color if different */
}

.repo-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1em;
  justify-content: space-between;
}

.repo-card {
  flex: 1 1 calc(50% - 1em);
  border: 1px solid #bbb;
  border-radius: 0;
  padding: 0.5em 1em;
  height: 220px;
  background-color: #fdfdfd;
  text-align: center;
  box-sizing: border-box;
  max-width: calc(50% - 1em);
  overflow: hidden;
  transition: border-color 0.2s ease-in-out;
}

.repo-card:hover {
  border-color: var(--link-hover-color);
}

.repo-card img {
  max-width: 100%;
  max-height: 130px;
  object-fit: contain;
  margin-bottom: 0.5em;
  border-radius: 0;
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
        coming soon. -B
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

  <div class="repo-card">
    <h3>
      <a class="publink" href="https://github.com/borjanG/2021-optimal-controller/">
        optimal actuators via Brunovsky's normal form
      </a>
    </h3>
    <img src="{{ '/assets/img/controller.png' |relative_url }}" alt="brunovsky">
  </div>

</div>

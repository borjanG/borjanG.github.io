---
layout: page
permalink: /projects/
title: projects
nav: true
nav_order: 3
---

<div id="repo-grid" style="display: flex; flex-wrap: wrap; gap: 1em; justify-content: space-between;"></div>

<script>
async function fetchReadmeSnippet(owner, repo) {
  try {
    const response = await fetch(`https://api.github.com/repos/${owner}/${repo}/readme`);
    const data = await response.json();
    const decoded = atob(data.content || "");
    const snippet = decoded.split('\n').slice(0, 8).join('\n'); // First 8 lines
    return snippet;
  } catch (error) {
    return "(Could not load README)";
  }
}

async function addRepoCard(owner, repo) {
  const snippet = await fetchReadmeSnippet(owner, repo);
  const container = document.getElementById('repo-grid');

  const card = document.createElement('div');
  card.style.flex = '1 1 calc(50% - 1em)';
  card.style.border = '1px solid #ccc';
  card.style.padding = '1em';
  card.style.borderRadius = '8px';
  card.style.backgroundColor = '#fdfdfd';
  card.style.boxShadow = '2px 2px 5px rgba(0,0,0,0.05)';
  card.style.whiteSpace = 'pre-wrap';

  card.innerHTML = `
    <h3><a href="https://github.com/${owner}/${repo}" target="_blank">${repo}</a></h3>
    <pre style="font-size: 0.9em; font-family: monospace;">${snippet}</pre>
  `;

  container.appendChild(card);
}

const repos = [
  ['borjanG', '2023-transformers-rotf'],
  ['borjanG', '2023-transformers'],
  ['borjanG', '2022-stefan-control'],
  ['borjanG', '2022-turnpike-pde-resnets'],
  ['borjanG', 'optimal.controller'],
  ['borjanG', 'dynamical.systems'],
  ['HugoKoubbi', '2024-transformers-dotm'],
  ['KimiSun18', '2024-gauss-kde-attention'],
];

repos.forEach(([owner, repo]) => addRepoCard(owner, repo));
</script>

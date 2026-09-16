---
layout: page
permalink: /jobs/
title: jobs
nav: true
nav_order: 4
_styles: |
  .jobs-photos {
    display: grid;
    grid-template-columns: minmax(0, 9fr) minmax(0, 16fr);
    gap: 1rem;
  }

  .jobs-photos figure {
    margin: 0;
  }

  .jobs-photos img {
    display: block;
    width: 100%;
    height: auto;
  }
---

currently i'm supervising the phd thesis of the amazing [Hugo Koubbi](https://hugokoubbi.github.io/). feel free to reach out if you want to join us!

<div class="jobs-photos">
  {%
    include figure.liquid path="assets/img/jobs-office.jpeg" alt="Discussion in a mathematics office"
    width=960 height=1280 sizes="(min-width: 800px) 272px, 36vw" loading="eager"
  %}
  {%
    include figure.liquid path="assets/img/jobs-blackboard.jpeg" alt="Writing mathematics on a blackboard"
    width=1280 height=960 sizes="(min-width: 800px) 484px, 64vw" loading="eager"
  %}
</div>

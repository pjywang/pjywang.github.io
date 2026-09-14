---
layout: single
permalink: /latte/
title: "Meet Latte"
author_profile: true
---

## Meet Latte

My dog Latte, and a few moments from our walks together.

<style>
/* Preserve the collage and portrait proportions, with a comfortable reading width. */
.latte-gallery { max-width: 680px; margin: 1.5em 0 2em; }
.latte-gallery figure { display: block; margin: 0; }
.latte-gallery a { display: block; }
.latte-gallery img { display: block; width: 100%; height: auto; border-radius: 6px; }
.latte-gallery figcaption { margin: 0.65em 0 0; text-align: left; }
.latte-portraits { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 1em; margin-top: 1.5em; }
@media (max-width: 480px) {
  .latte-portraits { grid-template-columns: 1fr; }
}
</style>

<div class="latte-gallery">
  <figure>
    <a href="{{ '/assets/images/Latte1.jpg' | relative_url }}">
      <img src="{{ '/assets/images/Latte1.jpg' | relative_url }}" alt="A collage of Junyoung and Latte in a park, Latte walking beside fallen petals, and Latte sitting on the grass" width="1200" height="1200">
    </a>
  </figure>
  <div class="latte-portraits">
    <figure>
      <a href="{{ '/assets/images/Latte2.jpg' | relative_url }}">
        <img src="{{ '/assets/images/Latte2.jpg' | relative_url }}" alt="Latte sitting on the grass and looking up at Junyoung" width="1080" height="1440" loading="lazy">
      </a>
    </figure>
    <figure>
      <a href="{{ '/assets/images/Latte3.jpg' | relative_url }}">
        <img src="{{ '/assets/images/Latte3.jpg' | relative_url }}" alt="Latte offering a paw to Junyoung while sitting on the grass" width="1080" height="1440" loading="lazy">
      </a>
      <figcaption>Fun fact: he can give you his left or right paw on command!</figcaption>
    </figure>
  </div>
</div>

[Back to my homepage]({{ '/' | relative_url }})

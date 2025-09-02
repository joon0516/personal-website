---
layout: page
title: others
permalink: /others/
description: Math books, niche stories, and visual side projects.
nav: true
nav_order: 4
display_categories: []
horizontal: false
---

<!-- pages/others.md -->
<div class="projects">
  <!-- Math Books Section -->
  <a id="books" href=".#books">
    <h2 class="category">Math Books & Stories</h2>
  </a>
  <p>I like theory. I have been collecting physical copies of math books since 2024 and have been self-studying many topics as a hobby, and sometimes for classes. (I’m planning to add a picture of my bookshelf here soon 📚)</p>

  
  <div class="row">
    <div class="col-sm-12">
      <h5>Books I own</h5>
      <ul>
        <li><strong>Principles of Mathematical Analysis</strong> by Walter Rudin (1976)</li>
        <li><strong>Understanding Analysis</strong> by Stephen Abbott (2015)</li>
        <li><strong>Elementary Analysis: The Theory of Calculus</strong> by Kenneth A. Ross (1980)</li>
        <li><strong>Measure, Integration & Real Analysis</strong> by Sheldon Axler (2020)</li>
        <li><strong>Measure and Integral</strong> by John L. Kelley and T.P. Srinivasan (1988)</li>
        <li><strong>Probability</strong> by A. N. Shiryaev (1996)</li>
        <li><strong>Basic Topology</strong> by M. A. Armstrong (1983)</li>
        <li><strong>Abstract Algebra</strong> by Dan Saracino (2008)</li>
        <li><strong>Undergraduate Algebra</strong> by Serge Lang (1990)</li>
        <li><strong>Linear Algebra</strong> by Serge Lang (1987)</li>
        <li><strong>Book of Proof</strong> by Richard Hammack (2013)</li>
        <li><strong>The Mathematics of Nonlinear Programming</strong> by A. L. Peressini, F. E. Sullivan, and J. J. Uhl (1988) </li>
        <li><strong>Methods of Mathematical Economics</strong> by Joel Franklin (1980)</li>
        <li><strong>Introduction to the Theory of Computation</strong> by Michael Sipser (2012)</li>
      </ul>
    </div>
  </div>
  <p>Here’s a niche fact about me: I live in Whyburn House at the University of Virginia. This dorm is named after <a href="https://en.wikipedia.org/wiki/Gordon_Whyburn">Gordon Whyburn</a>, a UVA math professor known for his work in topology. One of his PhD students at UVA, <a href="https://en.wikipedia.org/wiki/John_L._Kelley">John L. Kelley</a>, later chaired the math department at UC Berkeley and is well-known for his classic <em>General Topology</em>. I own a copy of the last book he wrote, <em>Measure and Integral</em>.</p>

  <div class="row">
    <div class="col-sm-8">
      <p>Another fun fact: I once had dinner with <a href="https://www.middlebury.edu/college/people/stephen-abbott">Stephen Abbott</a>, author of <em>Understanding Analysis</em>, one of the most widely used undergraduate real analysis textbooks. He got his PhD in math at UVA and is now a professor at Middlebury College. In 2025, he attended UVA's math majors' annual dinner, and I was lucky to sit right next to him. Here's a picture of my signed copy of <em>Understanding Analysis</em>.</p>

      <p>One last fun fact: I took my real analysis course at UVA with <a href="https://uva.theopenscholar.com/nick-kuhn/">Nick Kuhn</a>, the son of <a href="https://en.wikipedia.org/wiki/Harold_W._Kuhn">Harold Kuhn</a>, one of the Ks in the <a href="https://en.wikipedia.org/wiki/Karush%E2%80%93Kuhn%E2%80%93Tucker_conditions">KKT conditions</a>. It was his final semester teaching at UVA before retiring.</p>
    </div>
    <div class="col-sm-4">
      {% include figure.liquid path="assets/img/abbott_signed.jpg" title="Signed copy of Understanding Analysis by Stephen Abbott" class="img-fluid rounded z-depth-1" %}
    </div>
  </div>

  <!-- Visual Projects Section -->
  <a id="fun" href=".#fun">
    <h2 class="category">Visual Projects</h2>
  </a>
  <p>Lastly, here are some cool visual projects that are not related to my research.</p>
  {% assign visual_projects = site.projects | where: "category", "fun" %}
  {% assign sorted_visual_projects = visual_projects | sort: "importance" %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_visual_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
</div> 
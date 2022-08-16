---
layout: default
title: Publications
subtitle: test
---

<div class="content">

  <div id="description">
    {% include me.html %}
  </div>
</div>

<div id="accordion">
  
  <h1 id="pubs" class="panel">Publications</h1>
  <div class="panel-content">
    {% include loop_publications.html %}
  </div>


  <h1 id="funding" class="panel">Funding</h1>
  <div class="panel-content">
    <a href="https://aaaaaa">
      <img class="center" alt="Funded by aaaaaaa"
      src="https://aaaaaa"></a>
  </div>
  <!-- <h1 id="code" class="panel">Code</h1>
  <div class="panel-content">
    {% capture code %}{% include code.md %}{% endcapture %}
    {{ code | markdownify }}
  </div> -->
  <h1 id="cv" class="panel">CV</h1>
  <div class="panel-content">
    {% include cv.html %}
  </div>
---
layout: page
title: 16 Bit-Serial Computer
description: 16 bit Little Computer 3 processor built with SystemVerilog
img: assets/img/SpartanFPGA.jpeg
importance: 2
category: academic
giscus_comments: false
---

For more information on the SLC3 Computer, check out the source code below:

{% if site.data.repositories.github_repos %}
<div class="repositories d-flex justify-content-center" style="width: 100%;">
  {% for repo in site.data.repositories.github_repos %}
    {% if repo == "PNatarajan123/SLC3_Computer" %}
      {% include repository/repo.liquid repository=repo %}
      {% break %}
    {% endif %}
  {% endfor %}
</div>
{% endif %}


Also, check out the <a href="/assets/pdf/SLC3_Computer_Lab_Report.pdf" target="_blank">computer report</a>.
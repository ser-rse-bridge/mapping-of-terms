---
title: Mapping of Terms Between Software Engineering Research (SER) and Research Software Engineering (RSE)
layout: single
---
{% assign first = site.terms | sort | first %}
[Browse by term]({{ first.url | relative_url }})

---

{% for term in site.terms sort %}
<section style="margin-top:1em;width:100%">
<table style="width:100%">
    <tr>
        <th style="width:50%">SE Fundamental</th><th style="width:50%">RSE Equivalent</th>
    </tr>
    <tr>
        <td>{% include array_to_ul.html array=term.se_fundamental %}</td><td>{% include array_to_ul.html array=term.rse_equivalent %}</td>
    </tr>
</table>

<p align="center">
<a class="btn btn--primary btn--small" href="{{ term.url | relative_url }}">Details »</a>
</p>

{% unless forloop.last %}
  <hr style="width:50%; margin-left:auto; margin-right:auto; margin-top: 1em">
{% endunless %}

</section>

{% endfor %}
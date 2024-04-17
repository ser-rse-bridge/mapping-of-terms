---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
# Mapping of Terms Between Software Engineering Research (SER) and Research Software Engineering (RSE)

{% assign first = site.terms | sort | first %}
[Browse by term]({{ first.url | relative_url }})

---

{% for term in site.terms sort %}
<section style="margin-top:1em">
<table>
    <tr>
        <td><strong>SER Term</strong></td><td><strong>RSE Term</strong></td>
    </tr>
    <tr>
        <td><strong>{{ term.ser-term }}</strong></td><td><strong>{{ term.rse-term }}</strong></td>
    </tr>
</table>

<nav align="center">
<a href="{{ term.url | relative_url }}">See term details</a> |
<a href="{{site.github.repository_url}}/blob/main/{{term.path}}">Edit term on GitHub</a>
</nav>

{% unless forloop.last %}
  <hr style="width:50%; margin-left:auto; margin-right:auto; margin-top: 1em">
{% endunless %}

</section>

{% endfor %}
---
title: Mapping of Terms Between Software Engineering Research (SER) and Research Software Engineering (RSE)
layout: single
toc: true
toc_sticky: true
---

## Goals

Many in the research software engineering (RSE) community have picked up their understanding of software engineering (SE) terminology, concepts, practices, and tools (which we call "SE fundamentals") via informal means, and often not from software engineering researchers (SERs).  We want to get a better handle on what RSEs know about and use from the SE community and where there might be gaps.  Gaps may stem largely from lack of awareness, or it may be that RSEs have tried the fundamental and found it less useful in the context of research software.  In the former case, there are opportunities for education and training as well as other outreach to increase awareness and adoption. In the latter case, there may be opportunities for the SER community to work with RSEs to understand why not, and if there might be adaptations that would make it more amenable to use in the research software (RS) community.

## Approach

We're developing a mapping between terminology used in the two communities.  For each term, we're trying to gauge the extent to which the RSE community is aware of these fundamentals of software engineering and uses them, along with the perceived potential for software engineering research to improve usage in RS.

To be systematic, we're starting with the [Software Engineering Body of Knowledge](https://www.computer.org/education/bodies-of-knowledge/software-engineering) (SWEBOK) as the primary source of terms and their meanings from the SE community.  Once we've covered the terms from SWEBOK, we'll open it to other sources, though we'll always prefer well-recognized sources that will help us be systematic.

## How to contribute

The page for each term includes a discussion capability.  Make comments there to suggest changes or discuss the term's entry.

{% assign first = site.terms | sort | first %}
## Summary list of terms ([browse by term]({{ first.url | relative_url }}))

{% for term in site.terms sort %}
<section style="margin-top:1em">
<h3>{{ term.title }}</h3>
<table style="display:table">
    <thead>
    <tr>
        <th style="width:50%">SE Fundamental</th>
        <th style="width:50%">RSE Equivalent</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td>{% if term.se_fundamental and term.se_fundamental != empty %}
                {% include array_to_ul.html array=term.se_fundamental %}
            {% else %}
                <em style="color:red">Not provided</em>
            {% endif %}
        </td>
        <td>{% if term.rse_equivalent and term.rse_equivalent != empty %}
                {% include array_to_ul.html array=term.rse_equivalent %}
            {% else %}
                <em style="color:red">Not provided</em>
            {% endif %}
        </td>
    </tr>
    </tbody>
</table>

<p align="center">
<a class="btn btn--primary btn--small" href="{{ term.url | relative_url }}">Details »</a>
</p>

{% unless forloop.last %}
  <hr style="width:50%; margin-left:auto; margin-right:auto; margin-top: 1em">
{% endunless %}

</section>

{% endfor %}

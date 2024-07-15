---
title: Mapping of Terms Between Software Engineering Research (SER) and Research Software Engineering (RSE)
layout: single
toc: true
toc_sticky: true
comments: true
---

## Goals

Many in the research software engineering (RSE) community have picked up their understanding of software engineering (SE) terminology, concepts, practices, and tools (which we call "SE fundamentals") via informal means, and often not from software engineering researchers (SERs).  We want to get a better handle on what RSEs know about and use from the SE community and where there might be gaps.  Gaps may stem largely from lack of awareness, or it may be that RSEs have tried the fundamental and found it less useful in the context of research software.  In the former case, there are opportunities for education and training as well as other outreach to increase awareness and adoption. In the latter case, there may be opportunities for the SER community to work with RSEs to understand why not, and if there might be adaptations that would make it more amenable to use in the research software (RS) community.

## Approach

We're developing a mapping between terminology used in the two communities.  For each term, we're trying to gauge the extent to which the RSE community is aware of these fundamentals of software engineering and uses them, along with the perceived potential for software engineering research to improve usage in RS.

To be systematic, we're starting with the [Software Engineering Body of Knowledge](https://www.computer.org/education/bodies-of-knowledge/software-engineering) (SWEBOK) as the primary source of terms and their meanings from the SE community.  Once we've covered the terms from SWEBOK, we'll open it to other sources, though we'll always prefer well-recognized sources that will help us be systematic.

Each SE fundamental has a page that lists the following:

- The SE fundamental, and synonyms or adjacent concepts which can be grouped together for mapping purposes
    - The SWEBOK section number(s) in which the terms are found
    - A brief description of the SE fundamental
- The equivalent RSE term(s), also including synonyms or adjacent concepts.
    - A brief description of the typical RSE practices associated with the term
- An estimate of the level of awareness of the SE fundamental by RSEs, along with a source for the estimate
    - Values range from 0=effectively no awareness to 3=widespread awareness
- An estimate of the level of usage of the SE fundamental by RSEs, along with a source for the estimate
    - Values range from 0=effectively no usage to 3=widespread usage
- An estimate of the potential for SE research to improve the use of the fundamental in RS, along with a source for the estimate
    - Values range from 0=effectively no opportunity to 3=significant SE research would be beneficial
- A brief description of the reasons or opportunities for SE research to facilitate improvements
- Any references or links that may be useful
- Date of last review of the term mapping record by the curators of the website
- Additional notes as may be useful

{% assign first = site.terms | sort | first %}
The table below, based on the SWEBOK table of contents, will link you to the detail pages for the available SE fundamentals, or you can browse through the collection of terms [page by page]({{ first.url | relative_url }}).

## How *you* can contribute

We want this mapping to represent the collective experience of the SER and RSE communities. The page for each SE fundamental includes a discussion capability.  Make comments there to suggest changes or discuss the term's entry.

## SWEBOK table of contents

*Note that the SWEBOK contains a great deal more than just terminology.  This table presents only those sections of the SWEBOK which are candidates for mapping.  If no link is presented, we don't yet have a page for the relevant term(s). If you'd like to help us complete the table, please reach out via [Github issues](https://github.com/ser-rse-bridge/mapping-of-terms/issues).*

*During the development of this page, we're displaying the whole SWEBOK table of contents, but marking sections that are **not** candidates for mapping in red and noting "n/a" in the **Mapping** column. Eventually, we will simply avoid displaying those entries. Also, we're currently showing the SWEBOK page numbers, as a convenience.  We may remove those in production.*

{% comment %}
  Use site.data.swebok-toc to present a "table of contents" to SWEBOK.
  Add links to the term mapping pages for toc entries, where appropriate.

  Add additional rows to the toc for terms that fall between one toc section and the next.  
  Specifically, the toc only goes to depth=3, so items at depth=4+ need to be added.
{% endcomment %}
<table style="display:table">
  <thead><tr>
    <th>Section</th><th>Heading</th><th>Page</th><th>Mapping</th>
  </tr></thead>
  {% comment %}
    Step through the rows of the table.  
    Each cell in the row has a component named per the header row of the data file.
  {% endcomment %}
  {% assign prev_section = "" %}
  {% for row in site.data.swebok-toc %}
    {% assign tdstyle = ""%}
    {% comment %}
      Chapter headings have only one component in their section numbers
    {% endcomment %}
    {% assign depth = row.section | split: "." | size %}
    {% comment %}
      Render chapter headings in bold face.
      Render those for which mapping is not applicable in red.
    {% endcomment %}
    {% if depth == 1 or row.mapping == "n/a" %}
      {% assign tdstyle = 'style="' %}
      {% if depth == 1 %}{% assign tdstyle = tdstyle | append: "font-weight:bold;" %}{% endif %}
      {% if row.mapping == "n/a" %}{% assign tdstyle = tdstyle | append: "color:red;" %}{% endif %}
      {% assign tdstyle = tdstyle | append: '"' %}
    {% endif %}
    {% comment %}
      Look for exact matches for this section in the terms collection
    {% endcomment %}
    {% assign terms = site.terms | where_exp: "t", "t.swebok_section == row.section" %}
    {% assign mappings = "" %}
    {% for t in terms %}
      {% assign turl = t.url | relative_url %}
      {% assign mappings = mappings | append: '<a href="' | append: turl| append: '">mapping</a>' %}
      {% unless forloop.last %}{% assign mappings = mappings | append: ", " %}{% endunless %}
    {% endfor %}
    {% comment %}
      Emit any terms that fall between the previous section and this section
    {% endcomment %}
    {% assign terms = site.terms | where_exp: "t", "t.swebok_section > prev_section and t.swebok_section < row.section" %}
    {% for t in terms %}
        <tr id="{{ t.swebok_section }}">
          <td>{{ t.swebok_section }}</td>
          <td>{{ t.se_fundamental[0] }}</td>
          <td>??</td>
          <td><a href="{{ t.url | relative_url }}">mapping</a></td>
        </tr>
    {% endfor %}
    {% comment %}
      Emit the actual toc row we're processing
    {% endcomment %}
    <tr id="{{ row.section }}">
      <td {{tdstyle }}>{{ row.section }}</td>
      <td {{tdstyle }}>{{ row.heading }}</td>
      <td {{tdstyle }}>{{ row.page }}</td>
      <td {{tdstyle }}>{{ row.mapping }}{{ mappings }}</td>
    </tr>
    {% assign prev_section = row.section %}
    {% endfor %}
</table>

---
layout: default
title: Associates
description: The people and businesses Far-Fetched Advisory and Consulting works alongside.
permalink: /associates/
---
{%- assign roster = site.data.associates -%}
<div class="ff-view ff-page ff-page--wide associates">
  <h1 class="ff-page__title">Associates</h1>
  <p class="ff-page__lede">Far Fetched is one senior advisor, not an agency. These are the people and businesses we work alongside: specialists, partners, and operators we trust.</p>

  {%- if roster.people.size > 0 %}
  <section class="associates__group" aria-labelledby="associates-people">
    <h2 class="associates__heading" id="associates-people">People</h2>
    {%- for person in roster.people %}
    {% include associate.html entry=person kind="person" %}
    {%- endfor %}
  </section>
  {%- endif %}

  {%- if roster.businesses.size > 0 %}
  <section class="associates__group" aria-labelledby="associates-businesses">
    <h2 class="associates__heading" id="associates-businesses">Businesses</h2>
    {%- for business in roster.businesses %}
    {% include associate.html entry=business kind="business" %}
    {%- endfor %}
  </section>
  {%- endif %}

  <div class="ff-cta-block">
    <h3>Need one of these specialists on your project?</h3>
    <a href="{{ '/contact/' | relative_url }}" class="btn-primary">Get in touch</a>
  </div>
</div>

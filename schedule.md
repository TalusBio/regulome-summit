---
layout: page
title: Schedule

# Display order and labels
order:
  - registration
  - plenary
  - nwsf
  - ai-ml
  - lunch
  - keynote
  - epigenetics
  - undruggable
  - posters

slots:
  registration: {time: "8:00 AM", label: "Registration", note: "Check in, badges, coffee"}
  plenary:      {time: "9:00 AM", label: "Welcome, plenary", note: "Opening remarks"}
  nwsf:         {time: "10:00 AM", label: "Northwest Sarcoma Foundation", note: "Patient and clinical perspectives"}
  ai-ml:        {time: "11:00 AM", label: "Session 1, AI and ML"}
  lunch:        {time: "12:00 PM", label: "Lunch"}
  keynote:      {time: "1:00 PM",  label: "Keynote"}
  epigenetics:  {time: "2:00 PM",  label: "Session 2, Epigenetics"}
  undruggable:  {time: "3:00 PM",  label: "Session 3, Drugging the Undruggable"}
  posters:      {time: "4:00 PM",  label: "Posters and happy hour", note: "Reception"}

# Optional blurb shown under NWSF details
nwsf_blurb: >
  Brief remarks on patient impact and clinical needs in sarcoma.
  Why the regulome matters for rare cancers. Update this text as needed.
---

# Event Schedule

## Monday, September 15 · University of Washington, Seattle

| Time | Session | Details |
|----:|:--|:--|
{% for key in page.order %}
{% assign slot = page.slots[key] %}
{% if key == "ai-ml" or key == "epigenetics" or key == "undruggable" %}
  {% assign chair = site.data.speakers | where: "session", key | where: "role", "chair" | first %}
  | {{ slot.time }} | {{ slot.label }} | {% if chair %}Session Chair: {{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% else %}Session chair TBA{% endif %} |
{% elsif key == "keynote" %}
  {% assign keynote = site.data.speakers | where: "role", "keynote" | first %}
  | {{ slot.time }} | {{ slot.label }} | {% if keynote %}{{ keynote.name }}{% if keynote.degrees %}, {{ keynote.degrees }}{% endif %}{% else %}Speaker TBA{% endif %} |
{% else %}
  | {{ slot.time }} | {{ slot.label }} | {{ slot.note | default: "" }} |
{% endif %}
{% endfor %}

---

## Welcome, plenary
Short orientation. Context, logistics.

---

## Northwest Sarcoma Foundation
{{ page.nwsf_blurb }}

<details><summary>Speakers</summary>
{% assign nw_list = site.data.speakers | where: "session", "nwsf" %}
{% for sp in nw_list %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}*{{ sp.talk_title }}*{% endif %}
  {% if sp.abstract %}<br>{{ sp.abstract }}{% endif %}
{% endfor %}
</details>

---

## Session 1, AI and ML
{% assign chair = site.data.speakers | where: "session", "ai-ml" | where: "role", "chair" | first %}
**Session Chair:** {% if chair %}{{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Speakers and talks</summary>
{% assign list = site.data.speakers | where: "session", "ai-ml" | where_exp: "s", "s.role == 'speaker' or s.role == 'panelist'" %}
{% for sp in list %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}*{{ sp.talk_title }}*{% endif %}
  {% if sp.abstract %}<br>{{ sp.abstract }}{% endif %}
{% endfor %}
</details>

---

## Keynote
{% assign keynote = site.data.speakers | where: "role", "keynote" | first %}
**Speaker:** {% if keynote %}{{ keynote.name }}{% if keynote.degrees %}, {{ keynote.degrees }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Abstract</summary>
{% if keynote and keynote.abstract %}{{ keynote.abstract }}{% else %}Abstract TBA{% endif %}
</details>

---

## Session 2, Epigenetics
{% assign chair = site.data.speakers | where: "session", "epigenetics" | where: "role", "chair" | first %}
**Session Chair:** {% if chair %}{{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Speakers and talks</summary>
{% assign list = site.data.speakers | where: "session", "epigenetics" | where_exp: "s", "s.role == 'speaker' or s.role == 'panelist'" %}
{% for sp in list %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}*{{ sp.talk_title }}*{% endif %}
  {% if sp.abstract %}<br>{{ sp.abstract }}{% endif %}
{% endfor %}
</details>

---

## Session 3, Drugging the Undruggable
{% assign chair = site.data.speakers | where: "session", "undruggable" | where: "role", "chair" | first %}
**Session Chair:** {% if chair %}{{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Speakers and talks</summary>
{% assign list = site.data.speakers | where: "session", "undruggable" | where_exp: "s", "s.role == 'speaker' or s.role == 'panelist'" %}
{% for sp in list %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}*{{ sp.talk_title }}*{% endif %}
  {% if sp.abstract %}<br>{{ sp.abstract }}{% endif %}
{% endfor %}
</details>

---

## Posters and happy hour
Reception and networking.

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

# Optional blurb under NWSF
nwsf_blurb: >
  Brief remarks on patient impact and clinical needs in sarcoma.
  Why the regulome matters for rare cancers. Update this text as needed.
---

# Event Schedule

## Monday, September 15 · University of Washington, Seattle

**Jump to:** [Plenary](#welcome-plenary) · [NWSF](#northwest-sarcoma-foundation) · [Session 1](#session-1-ai-and-ml) · [Keynote](#keynote) · [Session 2](#session-2-epigenetics) · [Session 3](#session-3-drugging-the-undruggable) · [Posters](#posters-and-happy-hour)

| Time | Session | Details |
|----:|:--|:--|
{% assign chairs = site.data.speakers | where: "role", "chair" %}
{% for key in page.order %}
{% assign slot = page.slots[key] %}
{% if key == "ai-ml" or key == "epigenetics" or key == "undruggable" %}
  {% assign chair_single = chairs | where: "session", key | first %}
  {% assign chair_multi  = chairs | where_exp: "p", "p.sessions and p.sessions contains key" | first %}
  {% assign chair = chair_single %}
  {% if chair == nil %}{% assign chair = chair_multi %}{% endif %}
  | {{ slot.time }} | {{ slot.label }} | {% if chair %}Session Chair: {{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% if chair.affiliation %} — {{ chair.affiliation }}{% endif %}{% else %}Session chair TBA{% endif %} |
{% elsif key == "keynote" %}
  {% assign keynote_single = site.data.speakers | where: "role", "keynote" | where: "session", key | first %}
  {% assign keynote_multi  = site.data.speakers | where: "role", "keynote" | where_exp: "p", "p.sessions and p.sessions contains key" | first %}
  {% assign keynote = keynote_single %}
  {% if keynote == nil %}{% assign keynote = keynote_multi %}{% endif %}
  | {{ slot.time }} | {{ slot.label }} | {% if keynote %}{{ keynote.name }}{% if keynote.degrees %}, {{ keynote.degrees }}{% endif %}{% if keynote.affiliation %} — {{ keynote.affiliation }}{% endif %}{% else %}Speaker TBA{% endif %} |
{% else %}
  | {{ slot.time }} | {{ slot.label }} | {{ slot.note | default: "" }} |
{% endif %}
{% endfor %}

---

## Welcome, plenary
Short orientation. Context and logistics.

---

## Northwest Sarcoma Foundation
{{ page.nwsf_blurb }}

<details><summary>Speakers</summary>
{% assign nwsf_single = site.data.speakers | where: "session", "nwsf" %}
{% assign nwsf_multi  = site.data.speakers | where_exp: "p", "p.sessions and p.sessions contains 'nwsf'" %}
{% assign nw_list = nwsf_single | concat: nwsf_multi %}
{% for sp in nw_list %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% assign t = sp.talk_title %}
  {% assign a = sp.abstract %}
  {% if t %}{% assign t_key = t['nwsf'] | default: t %}*{{ t_key }}*{% endif %}
  {% if a %}<br>{{ a['nwsf'] | default: a }}{% endif %}
{% endfor %}
</details>

---

## Session 1, AI and ML
{% assign chair_single = chairs | where: "session", "ai-ml" | first %}
{% assign chair_multi  = chairs | where_exp: "p", "p.sessions and p.sessions contains 'ai-ml'" | first %}
{% assign chair = chair_single %}{% if chair == nil %}{% assign chair = chair_multi %}{% endif %}
**Session Chair:** {% if chair %}{{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% if chair.affiliation %} — {{ chair.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Speakers and talks</summary>
{% assign s1_single = site.data.speakers | where: "session", "ai-ml" | where_exp: "p", "p.role == 'speaker' or p.role == 'panelist'" %}
{% assign s1_multi  = site.data.speakers | where_exp: "p", "(p.sessions and p.sessions contains 'ai-ml') and (p.role == 'speaker' or p.role == 'panelist')" %}
{% assign s1 = s1_single | concat: s1_multi %}
{% for sp in s1 %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% assign t = sp.talk_title %}{% if t %}{% assign t_key = t['ai-ml'] | default: t %}*{{ t_key }}*{% endif %}
  {% assign a = sp.abstract %}{% if a %}<br>{{ a['ai-ml'] | default: a }}{% endif %}
{% endfor %}
</details>

---

## Keynote
{% assign keynote_single = site.data.speakers | where: "role", "keynote" | where: "session", "keynote" | first %}
{% assign keynote_multi  = site.data.speakers | where: "role", "keynote" | where_exp: "p", "p.sessions and p.sessions contains 'keynote'" | first %}
{% assign keynote = keynote_single %}{% if keynote == nil %}{% assign keynote = keynote_multi %}{% endif %}
**Speaker:** {% if keynote %}{{ keynote.name }}{% if keynote.degrees %}, {{ keynote.degrees }}{% endif %}{% if keynote.affiliation %} — {{ keynote.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Abstract</summary>
{% if keynote and keynote.abstract %}{{ keynote.abstract['keynote'] | default: keynote.abstract }}{% else %}Abstract TBA{% endif %}
</details>

---

## Session 2, Epigenetics
{% assign chair_single = chairs | where: "session", "epigenetics" | first %}
{% assign chair_multi  = chairs | where_exp: "p", "p.sessions and p.sessions contains 'epigenetics'" | first %}
{% assign chair = chair_single %}{% if chair == nil %}{% assign chair = chair_multi %}{% endif %}
**Session Chair:** {% if chair %}{{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% if chair.affiliation %} — {{ chair.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Speakers and talks</summary>
{% assign s2_single = site.data.speakers | where: "session", "epigenetics" | where_exp: "p", "p.role == 'speaker' or p.role == 'panelist'" %}
{% assign s2_multi  = site.data.speakers | where_exp: "p", "(p.sessions and p.sessions contains 'epigenetics') and (p.role == 'speaker' or p.role == 'panelist')" %}
{% assign s2 = s2_single | concat: s2_multi %}
{% for sp in s2 %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% assign t = sp.talk_title %}{% if t %}{% assign t_key = t['epigenetics'] | default: t %}*{{ t_key }}*{% endif %}
  {% assign a = sp.abstract %}{% if a %}<br>{{ a['epigenetics'] | default: a }}{% endif %}
{% endfor %}
</details>

---

## Session 3, Drugging the Undruggable
{% assign chair_single = chairs | where: "session", "undruggable" | first %}
{% assign chair_multi  = chairs | where_exp: "p", "p.sessions and p.sessions contains 'undruggable'" | first %}
{% assign chair = chair_single %}{% if chair == nil %}{% assign chair = chair_multi %}{% endif %}
**Session Chair:** {% if chair %}{{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% if chair.affiliation %} — {{ chair.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Speakers and talks</summary>
{% assign s3_single = site.data.speakers | where: "session", "undruggable" | where_exp: "p", "p.role == 'speaker' or p.role == 'panelist'" %}
{% assign s3_multi  = site.data.speakers | where_exp: "p", "(p.sessions and p.sessions contains 'undruggable') and (p.role == 'speaker' or p.role == 'panelist')" %}
{% assign s3 = s3_single | concat: s3_multi %}
{% for sp in s3 %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% assign t = sp.talk_title %}{% if t %}{% assign t_key = t['undruggable'] | default: t %}*{{ t_key }}*{% endif %}
  {% assign a = sp.abstract %}{% if a %}<br>{{ a['undruggable'] | default: a }}{% endif %}
{% endfor %}
</details>

---

## Posters and happy hour
Reception and networking.

<details><summary>Poster details</summary>
- Setup time and location
- Poster size and format
- Presenter timing
- Best poster note if applicable
</details>

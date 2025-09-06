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
{% for key in page.order %}
{% assign slot = page.slots[key] %}
{% if key == "ai-ml" or key == "epigenetics" or key == "undruggable" %}
  {% assign chair = site.data.speakers
     | where: "role", "chair"
     | where_exp: "s", "(s.sessions and s.sessions contains key) or s.session == key"
     | first %}
  | {{ slot.time }} | {{ slot.label }} | {% if chair %}Session Chair: {{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% if chair.affiliation %} — {{ chair.affiliation }}{% endif %}{% else %}Session chair TBA{% endif %} |
{% elsif key == "keynote" %}
  {% assign keynote = site.data.speakers
     | where: "role", "keynote"
     | where_exp: "s", "(s.sessions and s.sessions contains key) or s.session == key"
     | first %}
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
{% assign nw_list = site.data.speakers
  | where_exp: "s", "(s.sessions and s.sessions contains 'nwsf') or s.session == 'nwsf'" %}
{% for sp in nw_list %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}
    {% if sp.talk_title.nwsf %}*{{ sp.talk_title.nwsf }}*{% else %}*{{ sp.talk_title }}*{% endif %}
  {% endif %}
  {% if sp.abstract %}
    {% if sp.abstract.nwsf %}<br>{{ sp.abstract.nwsf }}{% else %}<br>{{ sp.abstract }}{% endif %}
  {% endif %}
{% endfor %}
</details>


---

## Session 1, AI and ML
{% assign chair = site.data.speakers
   | where: "role", "chair"
   | where_exp: "s", "(s.sessions and s.sessions contains 'ai-ml') or s.session == 'ai-ml'"
   | first %}
**Session Chair:** {% if chair %}{{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% if chair.affiliation %} — {{ chair.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Speakers and talks</summary>
{% for sp in site.data.speakers %}
  {% if (sp.role == "speaker" or sp.role == "panelist") and ((sp.sessions and sp.sessions contains "ai-ml") or sp.session == "ai-ml") %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}
    {% if sp.talk_title["ai-ml"] %}*{{ sp.talk_title["ai-ml"] }}*{% else %}*{{ sp.talk_title }}*{% endif %}
  {% endif %}
  {% if sp.abstract %}
    {% if sp.abstract["ai-ml"] %}<br>{{ sp.abstract["ai-ml"] }}{% else %}<br>{{ sp.abstract }}{% endif %}
  {% endif %}
  {% endif %}
{% endfor %}
</details>

---

## Keynote
{% assign keynote = site.data.speakers
   | where: "role", "keynote"
   | where_exp: "s", "(s.sessions and s.sessions contains 'keynote') or s.session == 'keynote'"
   | first %}
**Speaker:** {% if keynote %}{{ keynote.name }}{% if keynote.degrees %}, {{ keynote.degrees }}{% endif %}{% if keynote.affiliation %} — {{ keynote.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Abstract</summary>
{% if keynote and keynote.abstract %}
  {% if keynote.abstract.keynote %}{{ keynote.abstract.keynote }}{% else %}{{ keynote.abstract }}{% endif %}
{% else %}
  Abstract TBA
{% endif %}
</details>

---

## Session 2, Epigenetics
{% assign chair = site.data.speakers
   | where: "role", "chair"
   | where_exp: "s", "(s.sessions and s.sessions contains 'epigenetics') or s.session == 'epigenetics'"
   | first %}
**Session Chair:** {% if chair %}{{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% if chair.affiliation %} — {{ chair.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Speakers and talks</summary>
{% for sp in site.data.speakers %}
  {% if (sp.role == "speaker" or sp.role == "panelist") and ((sp.sessions and sp.sessions contains "epigenetics") or sp.session == "epigenetics") %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}
    {% if sp.talk_title.epigenetics %}*{{ sp.talk_title.epigenetics }}*{% else %}*{{ sp.talk_title }}*{% endif %}
  {% endif %}
  {% if sp.abstract %}
    {% if sp.abstract.epigenetics %}<br>{{ sp.abstract.epigenetics }}{% else %}<br>{{ sp.abstract }}{% endif %}
  {% endif %}
  {% endif %}
{% endfor %}
</details>

---

## Session 3, Drugging the Undruggable
{% assign chair = site.data.speakers
   | where: "role", "chair"
   | where_exp: "s", "(s.sessions and s.sessions contains 'undruggable') or s.session == 'undruggable'"
   | first %}
**Session Chair:** {% if chair %}{{ chair.name }}{% if chair.degrees %}, {{ chair.degrees }}{% endif %}{% if chair.affiliation %} — {{ chair.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details><summary>Speakers and talks</summary>
{% for sp in site.data.speakers %}
  {% if (sp.role == "speaker" or sp.role == "panelist") and ((sp.sessions and sp.sessions contains "undruggable") or sp.session == "undruggable") %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} — {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}
    {% if sp.talk_title.undruggable %}*{{ sp.talk_title.undruggable }}*{% else %}*{{ sp.talk_title }}*{% endif %}
  {% endif %}
  {% if sp.abstract %}
    {% if sp.abstract.undruggable %}<br>{{ sp.abstract.undruggable }}{% else %}<br>{{ sp.abstract }}{% endif %}
  {% endif %}
  {% endif %}
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

---
layout: page
title: Schedule
---

# Event Schedule

## Monday, September 15 · University of Washington, Seattle

{% assign chair_ai_ml = nil %}
{% assign chair_epi = nil %}
{% assign chair_undr = nil %}
{% assign keynote = nil %}
{% for sp in site.data.speakers %}
  {% if sp.role == "chair" %}
    {% if sp.session == "ai-ml" %}{% assign chair_ai_ml = sp %}{% endif %}
    {% if sp.sessions and sp.sessions contains "ai-ml" %}{% assign chair_ai_ml = sp %}{% endif %}

    {% if sp.session == "epigenetics" %}{% assign chair_epi = sp %}{% endif %}
    {% if sp.sessions and sp.sessions contains "epigenetics" %}{% assign chair_epi = sp %}{% endif %}

    {% if sp.session == "undruggable" %}{% assign chair_undr = sp %}{% endif %}
    {% if sp.sessions and sp.sessions contains "undruggable" %}{% assign chair_undr = sp %}{% endif %}
  {% endif %}

  {% if sp.role == "keynote" %}
    {% if sp.session == "keynote" %}{% assign keynote = sp %}{% endif %}
    {% if sp.sessions and sp.sessions contains "keynote" %}{% assign keynote = sp %}{% endif %}
  {% endif %}
{% endfor %}

| Time    | Session                               | Details |
|-------: |---------------------------------------|---------|
| 8:00 AM | Registration                          | Check in, badges, coffee |
| 9:00 AM | Welcome, plenary                      | Opening remarks |
| 10:00 AM| Northwest Sarcoma Foundation          | Patient and clinical perspectives |
| 11:00 AM| Session 1, AI and ML                  | {% if chair_ai_ml %}Session Chair: {{ chair_ai_ml.name }}{% if chair_ai_ml.degrees %}, {{ chair_ai_ml.degrees }}{% endif %}{% if chair_ai_ml.affiliation %} · {{ chair_ai_ml.affiliation }}{% endif %}{% else %}Session chair TBA{% endif %} |
| 12:00 PM| Lunch                                 |  |
| 1:00 PM | Keynote                               | {% if keynote %}{{ keynote.name }}{% if keynote.degrees %}, {{ keynote.degrees }}{% endif %}{% if keynote.affiliation %} · {{ keynote.affiliation }}{% endif %}{% else %}Speaker TBA{% endif %} |
| 2:00 PM | Session 2, Epigenetics                | {% if chair_epi %}Session Chair: {{ chair_epi.name }}{% if chair_epi.degrees %}, {{ chair_epi.degrees }}{% endif %}{% if chair_epi.affiliation %} · {{ chair_epi.affiliation }}{% endif %}{% else %}Session chair TBA{% endif %} |
| 3:00 PM | Session 3, Drugging the Undruggable   | {% if chair_undr %}Session Chair: {{ chair_undr.name }}{% if chair_undr.degrees %}, {{ chair_undr.degrees }}{% endif %}{% if chair_undr.affiliation %} · {{ chair_undr.affiliation }}{% endif %}{% else %}Session chair TBA{% endif %} |
| 4:00 PM | Posters and happy hour                | Reception |

---

## Welcome, plenary
Short orientation. Context and logistics.

---

## Northwest Sarcoma Foundation
{{ site.data.sessions.nwsf.blurb }}{% if site.data.sessions.nwsf.link %} ([learn more]({{ site.data.sessions.nwsf.link }})){% endif %}

<details markdown="1"><summary>Speakers</summary>

{% assign session_key = "nwsf" %}
{% for sp in site.data.speakers %}
  {% assign in_session = false %}
  {% if sp.session == session_key %}{% assign in_session = true %}{% endif %}
  {% if sp.sessions and sp.sessions contains session_key %}{% assign in_session = true %}{% endif %}
  {% if in_session %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} · {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}{% if sp.talk_title[session_key] %}*{{ sp.talk_title[session_key] }}*{% else %}*{{ sp.talk_title }}*{% endif %}{% endif %}
  {% if sp.abstract %}{% if sp.abstract[session_key] %}<br>{{ sp.abstract[session_key] }}{% else %}<br>{{ sp.abstract }}{% endif %}{% endif %}
  {% endif %}
{% endfor %}

</details>

---

## Session 1, AI and ML
{{ site.data.sessions["ai-ml"].blurb }}

**Session Chair:** {% if chair_ai_ml %}{{ chair_ai_ml.name }}{% if chair_ai_ml.degrees %}, {{ chair_ai_ml.degrees }}{% endif %}{% if chair_ai_ml.affiliation %} · {{ chair_ai_ml.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details markdown="1"><summary>Speakers and talks</summary>

{% assign session_key = "ai-ml" %}
{% for sp in site.data.speakers %}
  {% if sp.role == "speaker" or sp.role == "panelist" %}
    {% assign in_session = false %}
    {% if sp.session == session_key %}{% assign in_session = true %}{% endif %}
    {% if sp.sessions and sp.sessions contains session_key %}{% assign in_session = true %}{% endif %}
    {% if in_session %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} · {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}{% if sp.talk_title[session_key] %}*{{ sp.talk_title[session_key] }}*{% else %}*{{ sp.talk_title }}*{% endif %}{% endif %}
  {% if sp.abstract %}{% if sp.abstract[session_key] %}<br>{{ sp.abstract[session_key] }}{% else %}<br>{{ sp.abstract }}{% endif %}{% endif %}
    {% endif %}
  {% endif %}
{% endfor %}

</details>

---

## Keynote
{{ site.data.sessions.keynote.blurb }}

**Speaker:** {% if keynote %}{{ keynote.name }}{% if keynote.degrees %}, {{ keynote.degrees }}{% endif %}{% if keynote.affiliation %} · {{ keynote.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details markdown="1"><summary>Abstract</summary>

{% if keynote and keynote.abstract %}
  {% if keynote.abstract.keynote %}{{ keynote.abstract.keynote }}{% else %}{{ keynote.abstract }}{% endif %}
{% else %}
  Abstract TBA
{% endif %}

</details>

---

## Session 2, Epigenetics
{{ site.data.sessions.epigenetics.blurb }}

**Session Chair:** {% if chair_epi %}{{ chair_epi.name }}{% if chair_epi.degrees %}, {{ chair_epi.degrees }}{% endif %}{% if chair_epi.affiliation %} · {{ chair_epi.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details markdown="1"><summary>Speakers and talks</summary>

{% assign session_key = "epigenetics" %}
{% for sp in site.data.speakers %}
  {% if sp.role == "speaker" or sp.role == "panelist" %}
    {% assign in_session = false %}
    {% if sp.session == session_key %}{% assign in_session = true %}{% endif %}
    {% if sp.sessions and sp.sessions contains session_key %}{% assign in_session = true %}{% endif %}
    {% if in_session %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} · {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}{% if sp.talk_title[session_key] %}*{{ sp.talk_title[session_key] }}*{% else %}*{{ sp.talk_title }}*{% endif %}{% endif %}
  {% if sp.abstract %}{% if sp.abstract[session_key] %}<br>{{ sp.abstract[session_key] }}{% else %}<br>{{ sp.abstract }}{% endif %}{% endif %}
    {% endif %}
  {% endif %}
{% endfor %}

</details>

---

## Session 3, Drugging the Undruggable
{{ site.data.sessions.undruggable.blurb }}

**Session Chair:** {% if chair_undr %}{{ chair_undr.name }}{% if chair_undr.degrees %}, {{ chair_undr.degrees }}{% endif %}{% if chair_undr.affiliation %} · {{ chair_undr.affiliation }}{% endif %}{% else %}TBA{% endif %}

<details markdown="1"><summary>Speakers and talks</summary>

{% assign session_key = "undruggable" %}
{% for sp in site.data.speakers %}
  {% if sp.role == "speaker" or sp.role == "panelist" %}
    {% assign in_session = false %}
    {% if sp.session == session_key %}{% assign in_session = true %}{% endif %}
    {% if sp.sessions and sp.sessions contains session_key %}{% assign in_session = true %}{% endif %}
    {% if in_session %}
- **{{ sp.name }}**{% if sp.degrees %}, {{ sp.degrees }}{% endif %}{% if sp.affiliation %} · {{ sp.affiliation }}{% endif %}
  {% if sp.talk_title %}{% if sp.talk_title[session_key] %}*{{ sp.talk_title[session_key] }}*{% else %}*{{ sp.talk_title }}*{% endif %}{% endif %}
  {% if sp.abstract %}{% if sp.abstract[session_key] %}<br>{{ sp.abstract[session_key] }}{% else %}<br>{{ sp.abstract }}{% endif %}{% endif %}
    {% endif %}
  {% endif %}
{% endfor %}

</details>

---

## Posters and happy hour
Reception and networking.

<details markdown="1"><summary>Poster details</summary>

- Setup time and location
- Poster size and format
- Presenter timing
- Best poster note if applicable

</details>


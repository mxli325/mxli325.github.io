---
permalink: /
title: ""
excerpt: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

# Educations
- *2023.09 - Now*, Xi’an Jiaotong University. 
- *2019.09 - 2023.06*, Northeastern University at Qinhuangdao.

# Publications

{% assign publications = site.publications | sort: "order" %}
{% for publication in publications %}
<div class='paper-box{% unless publication.image %} paper-box--text-only{% endunless %}'>
  {% if publication.image %}<div class='paper-box-image'>
    <div>
      {% if publication.venue %}<div class="badge">{{ publication.venue }}</div>{% endif %}
      {% if publication.image %}<img src='{{ publication.image }}' alt="{{ publication.title | escape }}" style="width: {{ publication.image_width | default: '100%' }};">{% endif %}
    </div>
  </div>
  {% endif %}<div class='paper-box-text'>
    {% unless publication.image %}<p class="journal-info">{{ publication.venue }}</p>{% endunless %}
    <p><a href="{{ publication.link }}">{{ publication.title }}</a></p>
    {{ publication.content | markdownify }}
    <p class="journal-info">
      <strong>Journal:</strong> {{ publication.journal }}
      · <strong>Year:</strong> {{ publication.year }}
      {% if publication.impact_factor %}· <strong>Impact Factor:</strong> {{ publication.impact_factor }}{% if publication.impact_factor_year %} ({{ publication.impact_factor_year }}){% endif %}{% endif %}
      {% if publication.quartile %}· <strong>Quartile:</strong> {{ publication.quartile }}{% endif %}
    </p>
  </div>
</div>
{% endfor %}

# Awards

{% assign awards = site.awards | sort: "order" %}

## International / National

{% for award in awards %}
  {% if award.level == "International" or award.level == "National" %}
    {% include award-box.html award=award %}
  {% endif %}
{% endfor %}

## Provincial

{% for award in awards %}
  {% if award.level == "Provincial" %}
    {% include award-box.html award=award %}
  {% endif %}
{% endfor %}

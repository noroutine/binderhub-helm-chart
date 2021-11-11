## See installation instructions for:

- [BinderHub](https://binderhub.readthedocs.io)

Jump to:
{%- for chartmap in site.data.index.entries %}
- [Development Releases: {{ chartmap[0] }}](#development-releases-{{ chartmap[0] | slugify }})
{%- endfor %}

{% for chartmap in site.data.index.entries %}
  {% if site.stableCharts contains chartmap[0] %}
### {{ chartmap[0] }}

| Version | Date | App. version |
|---------|------|---------------------|
    {%- assign sortedcharts = chartmap[1] | sort: 'created' | reverse -%}
    {%- for chart in sortedcharts -%}
      {%- unless chart.version contains "-" %}
| [{{ chart.version }}]({{ chart.urls[0] }}) | {{ chart.created | date_to_long_string }} | {{ chart.appVersion }} |
      {%- endunless -%}
    {%- endfor %}
  {%- endif %}
{% endfor %}


{% for chartmap in site.data.index.entries %}
### Development releases: {{ chartmap[0] }}

| Version | App. version | Date |
|---------|-----|---------------------|
  {%- assign sortedcharts = chartmap[1] | sort: 'created' | reverse %}
  {%- for chart in sortedcharts %}
| [{{ chart.version }}]({{ chart.urls[0] }}) | {{ chart.app_version }} | {{ chart.created | date_to_rfc822 }} |
  {%- endfor %}
{% endfor %}

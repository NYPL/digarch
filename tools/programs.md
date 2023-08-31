---
title: Programs
layout: default
nav_order: 6
parent: Software
grand_parent: Tools
has_children: False
---

# Programs:

Programs are defined as any non-internally developed out-of-the-box software used in Digital Archives workflows. Many programs used by Digital Archives staff can be installed via Homebrew or by downloading installation files from the associated website. Programs requiring more intensive installation and configuration instructions have been given dedicated pages.

{% for tool in site.data.program %}

## {{tool.name}}:
{{tool.desc}}

{% if tool.docs %}
[See Official Documentation]({{tool.docs}})
{% endif %}

{% if tool.inst%}
### Installing {{tool.name}}:
{{tool.inst}}
{% endif %}

{% if tool.conf%}
### Configuring {{tool.name}}:
{{tool.conf}}
{% endif %}

{% if tool.use%}
### Using {{tool.name}}:
{{tool.use}}
{% endif %}
{% endfor %}
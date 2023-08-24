---
title: Working Scripts
layout: default
nav_order: 7
parent: Software (Draft)
grand_parent: Tools
has_children: False
---

# Working Scripts:

Working Scripts are defined as scripts written internally and maintained by Digital Archives staff for use in our workflows.

{% for tool in site.data.working %}
### {{tool.name}}:
{{tool.desc}}

{% if tool.use%}
#### Using {{tool.name}}:
{{tool.use}}
{% endif %}

{% endfor %}

## Deprecated and Legacy Scripts:

Deprecated and Legacy Scripts are any scripts which may have been previously used in workflows but are no longer in use, were planned but not completed or replaced by a Working Script.

### ft.sh 
### metadata.sh 
### movemetadata script 
### movephotograph script 

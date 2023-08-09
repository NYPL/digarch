---
title: Software (Draft)
layout: default
nav_order: 5
parent: Tools
has_children: False
---

# Software
{: .no_toc }

Digital Archives utilizes several software throughout our workflows. This page acts as a departmental glossary for these software and includes installation, detailed use instructions and links to official documentation whenever possible. Shorter contextual instructions for these software can be found on the associated pages, consider this page our definitive guides.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Programs:

Programs are defined as any non-internally developed out-of-the-box software used in Digital Archives workflows.

{% for tool in site.data.program %}

### {{tool.name}}:
{{tool.desc}}

#### Installing {{tool.name}}:
{{tool.inst}}

#### Configuring {{tool.name}}:
{{tool.conf}}

#### Using {{tool.name}}:
{{tool.use}}

{% endfor %}

## Working Scripts:

Working Scripts are defined as scripts written internally and maintained by Digital Archives staff for use in our workflows.

### CMS metadata import 
### iterative scripts 
### kryofluxmove.sh 
### makesips script 
### moveimages script 
### report ftk extents script 
### report HDD extents script

## Deprecated and Legacy Scripts:

Deprecated and Legacy Scripts are any scripts which may have been previously used in workflows but are no longer in use, were planned but not completed or replaced by a Working Script.

### ft.sh 
### metadata.sh 
### movemetadata script 
### movephotograph script 


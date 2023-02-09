---
title: Filters and zips
layout: default
nav_order: 2
has_children: false
parent: FTK Processing Instructions
grand_parent: Processing
---

# Filters and zips
This video shows how the Actual Files filter deals with zips and files within zips. It demonstrates filters that will show files in zips that are available to import if you don’t see them in your collection. It displays what the File List looks like when a filter is active and how to toggle filters on and off.

<div class="embed-container">
  <iframe
      src="https://www.youtube.com/embed/rAtmTcIiRuM"
      width="700"
      height="480"
      frameborder="0"
      allowfullscreen="true">
  </iframe>
</div>

FTK can display files within Zip containers. But using Actual Files filter hides files in Zips.
![FTK File List with Zip and contents displayed](FTK-Introduction/media/zipfilelist.png)
Click Filter Manger.

![Filter Manager window with reduce system files filter highlighted](FTK-Introduction/media/reducesystemfiles.png)
Check default and imported filters for Actual Files. Select a filter.

![Filter Manager window with reduce system files filter highlighted and cursor over Define button](FTK-Introduction/media/reducesystemfilesdefine.png)
Click Define.

![Filter Definition window](FTK-Introduction/media/filterdefinition.png)
Note Operators: Matches, Criteria: Actual Files. This filter only displays actual files.

![File List with Actual Files filter on](FTK-Introduction/media/filelistactualfiles.png)
File List displays yellow when a filter is on. Note Zip is displayed not .doc files within.

![File List with Actual Files filter toggled off](FTK-Introduction/media/filelistfilteroff.png)
Click funnel in upper left corner to toggle filter off.

![FTK File List with Zip and contents displayed](FTK-Introduction/media/zipfilelist.png)
With the filter off File List displays .doc files within Zip container.  
Click Filter Manger.

![Filter Manager with "include zip extracted" filters displayed](FTK-Introduction/media/filtermanagerzipextracted.png)
Select a filter with “include zip extracted”. See import filter for more filters.

![Filter Definition window displaying "include zip extracted" filter](FTK-Introduction/media/filtermanagerincludezip.png)
Note Actual Files does not appear in filter Rules Criteria.

![File List with "include zip extracted" filter on](FTK-Introduction/media/filelistincludezip.png)
Files within Zip container (.doc files) appear while filter is on. Yellow File List shows filter is on.

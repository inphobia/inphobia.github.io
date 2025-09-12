---
date: {{ .Date }}
title: {{ replace .File.ContentBaseName "-" " " | title }}
params:
  eid: {{ replace .File.ContentBaseName "-" " " | title }}
---

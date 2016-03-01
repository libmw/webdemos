---
  layout: skill
  title: 问题汇总
---

## IE BUG

IE 用js插入一个img到div里，img不会自动缩放，即使设置了max-width和height为100%；除非先设置src，onload后插入。解决办法是，不要创建img标签，把img标签放到html里

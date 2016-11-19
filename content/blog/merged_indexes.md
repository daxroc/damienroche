---
author: "Damien Roche"
date: 2012-06-19
linktitle: Merged Index
title: Slow queries - Merged index
highlight: true
url: /blog/database/merged_indexes.html
---
I came accross a query recently that was very slow on our production systems but was running quite fast on development servers.

It turned out to be an index issue where the prodution mysql was deciding that an index_merge was the best available to use when in fact it wasn’t a combined index was.

It was recomended that I turn off index merge, I’m not entirely convinced this is a good idea but it seems to have had an over all improvement to performance.
```
SET GLOBAL 
    optimizer_switch='
        index_merge=off,
        index_merge_union=on,
        index_merge_sort_union=on,
        index_merge_intersection=on';
SELECT @@optimizer_switch;
```

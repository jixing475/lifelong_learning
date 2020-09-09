---
title: change blogdown syntax highlighting in blogdown
author: ZERO
date: '2020-06-02'
slug: change-blogdown-syntax-highlighting-in-blogdown
categories:
  - Tools
tags:
  - vis
subtitle: ''
summary: ''
authors: []
lastmod: '2020-06-02T09:27:13+08:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

## how

```
 [markup.highlight]
    codeFences = true
    hl_Lines = ""
    lineNoStart = 1
    lineNos = false
    lineNumbersInTable = true
    noClasses = true
    style = "solarized-dark"
    tabWidth = 4
```
> the config.toml file contains this section which is the bit that actually parametrises the highlighting.

## syntax highlighting



```r
# how to create a bar plot with ggplot2
library(ggthemes)
```

```
## Warning: package 'ggthemes' was built under R version 3.5.2
```

```r
library(ggplot2)
library(dplyr)
```

```
## Warning: package 'dplyr' was built under R version 3.5.2
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
library(tidyverse)
```

```
## Warning: package 'tidyverse' was built under R version 3.5.2
```

```
## Warning: package 'tidyr' was built under R version 3.5.2
```

```
## Warning: package 'purrr' was built under R version 3.5.2
```

```
## Warning: package 'stringr' was built under R version 3.5.2
```

```
## Warning: package 'forcats' was built under R version 3.5.2
```

```r
#how to create a barplot with label using ggplot2 package
iris %>%
  group_by(Species) %>%
  summarise(counts = n()) %>%
  mutate(Species = fct_reorder(Species, counts)) %>%
  ggplot(aes(x = Species, y = counts, fill = Species)) +
  geom_bar(stat = "identity") +
  geom_text(aes(label = counts), hjust = 1.6, color = "white", size = 5) +
  coord_flip() +
  theme_minimal()+ scale_color_tableau() + scale_fill_tableau()+
  labs(caption = "figure 01") +
  theme(axis.text.x = element_text(angle = 0, hjust = 1),
        legend.position = "bottom",
        plot.caption=element_text(size=12,family = "Arial",face = "bold",
                                  hjust=0, margin=margin(t=15)))
```

<img src="/post/2020-06-02-change-blogdown-syntax-highlighting-in-blogdown_files/figure-html/unnamed-chunk-1-1.png" width="672" />

## why

> Creating Websites with R Markdown book which outlines the differences between the Rmd and Rmarkdownformats.


> Turns out that each format is rendered to HTML through different converters. Rmarkdown uses something called Blackfriday and Rmd uses Pandoc. As I understanding then Rmd is rendered by R and Rmarkdown is rendered by Hugo and so posts need to be rendered by Hugo in order for all the configs in the .toml file to apply.

简单说就是 rmd 和 Rmarkdown 的编译方式是不同的

## links

 [Syntax Highlighting in Blogdown; a very specific solution | A stats website](https://venciso.netlify.app/2020/05/syntax-highlighting-blogdown/)

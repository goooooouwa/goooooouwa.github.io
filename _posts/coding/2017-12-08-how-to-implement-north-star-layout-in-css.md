---
date: 2017-12-08
title: How to implement north star layout in css
layout: post
category: coding
tags: css
---

![Desired Style]({{site.baseurl}}/assets/images/K5AXNzB.png)

## Design Requirements

tab text centering in navigation tab, a red dot relatively positioned at the upper right of tab text (text content might vary).

### Constraints:

navigation tab has `display` set as `flex`, so `float`, `clear` and `vertical-align` will have no effect on children (flex items).

### Box model

![Box model]({{site.baseurl}}/assets/images/4uKCNvQ.png)

## Solution

1. wrap the tab text and red dot inside a `div` or `span`
2. set `align-items: center` on the wrapper in preparation for text centering (note: by now the tab text are not center aligned since the red dot taking up some space of the wrapper)
3. set `position: relative` to override the default `static` position on the wrapper, so that it's children can position relatively to it (reference: [CSS position Property](https://www.w3schools.com/cssref/pr_class_position.asp))
4. set `position: absolute` to the red dot, so that it can position relatively to it's parent element: the wrapper. And notice, since the red dot has absolute position, it will float out of the document flow, by now the only child of the wrapper will be the tab text, which will take up the whole space. Since the wrapper is centered in navigation tab, so is the text. Since the text is the only child of the wrapper, position relatively to the wrapper has the same effect as position relatively to the text itself.
5. adjust `top` and `left` to set the right distance from the wrapper for the red dot.

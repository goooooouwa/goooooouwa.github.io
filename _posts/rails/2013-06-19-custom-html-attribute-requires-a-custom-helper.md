---
date: 2013-06-19
title: Custom HTML attribute requires a custom helper
category: rails
---
# Custom HTML attribute requires a custom helper

if I wanna add attribute 'data-submit_clear=1' to an text_field in rails, do this:

`<%= f.text_field :somename,:data =>{:submit_clear =>'1'} %>`

 

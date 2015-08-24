---
layout: post
title: Digging into Scopes in Rails
---
Scopes are nothing but macros in ruby. 

 * default_scope
 * scope
 * unscoped

###### Default Scope
<blockquote> default_scope { ... } </blockquote>

###### Scope 
<blockquote> scope :name, { ... } </blockquote>


Should explain difference between 
where(:end_date >= Date.today)
where('end_date=>?', Date.today)


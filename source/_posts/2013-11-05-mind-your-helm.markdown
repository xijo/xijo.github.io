---
layout: post
title: "Mind your helm"
date: 2013-11-05 08:35
comments: true
categories:
author: Johannes Opper
---
I really like the abstraction for menus that twitter bootstrap makes: take an `ul`, spice with some classes and wrap your links in `li` elements.

In order to build more and larger menus I wanted to have a small helper for the most common cases. Therefore an entry should be:

  1. Visible or invisible based on a condition
  1. Disabled and show a tooltip based on a condition
  1. Able to have a submenu
  1. Find out if it should be highlighted

So I wrote a little gem called `helmsman` and you can find out how it works on the [github page](https://github.com/xijo/helmsman).

For [betterplace](http://betterplace.org) we made some nice menus and submenus and I want to share how we did that with you.

For a project manager it should be possible to enter translations in all supported locales, so we wanted to have a submenu to select and highlight which locale the manager wants to edit.

```ruby
# Stolen from projects/_admin_sidebar.html.slim
- helm :translations, url: project_translations_url(project) do |entry|
  - if entry.current?
    ul
      - AppConfig.locales.each do |locale|
        = helm :"translation_#{locale}", url: (...), current: is_current_locale?
```

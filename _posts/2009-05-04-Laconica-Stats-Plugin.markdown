---
layout: post
title: Stats plugin for laconica
---

# {{ page.title }}

I installed laconica on my localhost the day it was opened to the public, but I never wrote any code for it for many reasons 
(but I won't go into this). When I saw that the latest laconica had support for plugins and hooks to help create them, I 
started to look at how to do something cool for my laconica server at <a href="http://symphoni.ca">symphoni.ca</a>. I came 
across <a href="http://www.macno.org/denticator.php">denticator</a> and had the idea to do a (very) simple plugin to show some 
stats for my instance.

You can get the code at <a href="http://symphoni.ca/plugin/StatsPlugin.txt">http://symphoni.ca/plugin/StatsPlugin.txt</a>. It 
basically adds a "stats" tab to the public navigation menu and then uses the google chart api and a sql query to display the global stats for each day of the week. I hope it can 
help to ceate (better) plugins for laconica.


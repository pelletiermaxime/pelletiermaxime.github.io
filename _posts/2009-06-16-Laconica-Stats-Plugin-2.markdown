---
layout: post
title: Stats plugin for laconica version 0.2
---

# {{ page.title }}

Someone (Gaurav Wasan) asked in the comments of my first blog post about this plugin if it was possible to modify it to show 
stats for a specific user. Took me a while, but i'm now posting to say I did it and I updated the sources.

You can get the code at <a href="http://symphoni.ca/plugin/StatsPlugin.txt">http://symphoni.ca/plugin/StatsPlugin.txt</a>. It 
basically adds a "stats" tab to the public navigation menu and to the personal navigation menu and 
then uses the google chart api and a few sql queries to display the global stats for each day of the week and to display the 
same stats for an user.

If it's not working for you, try adding the line

	Event::handle('EndPersonalGroupNav', array($this));

at the end of /lib/personalgroupnav.php (right before "$this->out->elementEnd('ul');").

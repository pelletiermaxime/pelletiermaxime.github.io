---
layout: post
title: Installing laconi.ca on nginx
---

# {{ page.title }}

A few weeks ago I wanted to install Laconi.ca and start my own microblogging instance. Of course by now you know that I use and 
really like nginx, so I looked for instructions on how to install it on this http server. All I found was tutorials for apache 
and nginx wasn't mentionned a single time, so I started doing it myself.
Here is my config :

	server {
                listen 80;
                server_name     symphoni.ca;
                root /path/to/my/htdocs;
                index index.php;
                location ~ \.php$ {
                        include /etc/nginx/fastcgi_params;
                        fastcgi_pass  127.0.0.1:1026;
                        fastcgi_index index.php;
                }
                location / {
                        try_files $uri $uri/ @laconica;
                }
                location @laconica {
                        rewrite ^(.+)$ /index.php?p=$1 last;
                }
        }

This config was tested only on nginx > 0.7.30. It should work on >= 0.6.36 because it now has try_files support, but I haven't 
tried it.

I also suggest using laconica >= 0.7.3 because it fixes some bugs in the redirects. Also, this config works **only** if you put 
the config
	$config['site']['fancy'] = true;
in the config.php. I couldn't get the not fancy urls to work, but I guess this isn't a problem :p.
If you need help just post a comment or contact me on identi.ca/symphoni.ca.

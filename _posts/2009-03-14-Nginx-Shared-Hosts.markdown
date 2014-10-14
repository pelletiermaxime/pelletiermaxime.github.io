---
layout: post
title: Configuring Nginx to do shared hosting or virtual hosts
---

# {{ page.title }}

I host multiple websites on the same server and I was tired to do server sections in my nginx config,
so I created a config that catches all domains and point to a directory. Heres my config and I will
explain it after.

	server {
                if ($host ~* www\.(.*)) {
                        set $host_without_www $1;
                        rewrite ^(.*)$ http://$host_without_www$1/ permanent;
                }
                server_name_in_redirect off; #or folders like /awstats will redirect to _
                listen 80;
                server_name _;
                access_log      /var/log/nginx/$host.access_log main;
                error_log      /var/log/nginx/$host.access_log info;
                root /var/www/$host/htdocs;
                location ~ \.php$ {
                        include /etc/nginx/fastcgi_params;
                        fastcgi_pass  127.0.0.1:1026;
                        fastcgi_index index.php;
                }
		#For WP
                if (!-e $request_filename) {
                        rewrite ^(.+)$ /index.php?q=$1 last;
                }
        }


Here is a detailed explanation of the config, as best as I can describe it.

	if ($host ~* www\.(.*)) {
        	set $host_without_www $1;
                rewrite ^(.*)$ http://$host_without_www$1/ permanent;
        }

Assign the variable host_without_www and then rewrite to stip all the www. Without those lines, www.domain.com and domain.com 
would be considered 2 different domains.

	server_name_in_redirect off; #or folders like /awstats will redirect to _

Like my comment says, without this line, domain.com/directory would redirect to _ (the server name).

	listen 80;
        server_name _;
        access_log      /var/log/nginx/$host.access_log main;
        error_log      /var/log/nginx/$host.access_log info;
        root /var/www/$host/htdocs;

The key part of this config is the server_name. _ is a catch all that catches every domain name. Then, the variable $host 
contain the actual domain name. For exemple, for this site the access log would be 
/var/log/nginx/pelletiermaxime.info.access_log. The root line tells nginx to use /var/www/pelletiermaxime.info/htdocs as the 
server root.

	location ~ \.php$ {
        	include /etc/nginx/fastcgi_params;
                fastcgi_pass  127.0.0.1:1026;
                fastcgi_index index.php;
        }
	#For WP
        if (!-e $request_filename) {
        	rewrite ^(.+)$ /index.php?q=$1 last;
        }

This is the standard config to pass requests to the php cgi and to rewrite urls for my wordpress blog. 

If you have questions or suggestions of how to do this better or comments, just ask.

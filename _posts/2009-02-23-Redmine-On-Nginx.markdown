---
layout: post
title: Installing Redmine on Nginx
---

# {{ page.title }}

At work we were looking for something to manage our projects, our bugs and that had a wiki, svn/git integration and some time 
tracking features. Trac what my first choice, but it needed lots of plugins to have the features we wanted. I then looked at 
<a href="http://www.indefero.net/">InDefero</a>. This would have been perfect because it's in php, but the project lacks a lot 
of features we wanted and just isn't mature enough yet. Then I remembered Redmine. The only problem is that I had to learn how 
to install rails, mongrel and how to configure nginx to make it work. It took me hours and that's why I wanted to blog about 
it.

The first step is to get Redmine working using WEBrick. I'm using gentoo so installing rails was as simple as running emerge 
rails:2.1 (i'm using Redmine 0.8 which works only with rails 2.1.x). Then I followed the steps on the install wiki of redmine 
at <a href="http://www.redmine.org/wiki/redmine/RedmineInstall">http://www.redmine.org/wiki/redmine/RedmineInstall</a>. One 
step I forgot at the beginning was making sure that my database is really set to UTF-8. Redmine seemed to work in ISO-8859-1, 
but I couldn't import the data from our old Mantis installation until I set everything to UTF-8. After all this, Redmine worked 
perfectly at http://localhost:3000.

Next is configuring mongrel and nginx. I'm sure setting up mongrel is different on every distro, but here are the commands I 
did on Gentoo :

	- emerge mongrel_cluster
	- mkdir /etc/mongrel_cluster
	- ln -s /server/root/redmine/config/mongrel_cluster.yml /etc/mongrel_cluster/redmine.yml
	- cp /usr/lib/ruby/gems/1.8/gems/mongrel_cluster-1.0.5/resources/mongrel_cluster /etc/init.d
	- chmod +x /etc/init.d/mongrel_cluster
	- modified /etc/mongrel_cluster/redmine.yml

Then, the hard part : configuring nginx. This took me hours to figure out. The problem is that redmine doesn't like to be in a 
subdirectory. For exemple, http://trima.ca/redmine won't work. What I learned just before writing this is that theres solutions 
around this problem :
- Starting mongrel with --prefix=/redmine
- Add this "ActionController::AbstractRequest.relative_url_root = "/redmine"" at the end of config/environment.rb
Keep in mind that I haven't tried those solutions. What I ended up doing is using "redmine.trima.ca". Here's my nginx config :


	upstream mongrel {
		server 127.0.0.1:9000;
	        server 127.0.0.1:9001;
	}
	server {
		listen          80;
	        server_name     redmine.trima.ca;

        	root /path/to/root/redmine/public;

	        location / {
        		proxy_set_header  X-Real-IP  $remote_addr;
                	proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
	                proxy_set_header  Host $http_host;
        	        proxy_redirect false;
                	proxy_read_timeout 300;

	                if (-f $request_filename/index.html) {
        	        	rewrite (.*) $1/index.html break;
                	}

	                if (-f $request_filename.html) {
        	        	rewrite (.*) $1.html break;
                	}

	                if (-f $request_filename.txt) {
        	        	rewrite (.*) $1.txt break;
                	}

	                proxy_pass http://mongrel/;
	        }
	}
I also had to add redmine.trima.ca to the dns, but that was really easy using the control panel of Linode.
Hope that helped you.


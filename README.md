## Configure NGINX for Ubuntu

Configure Nginx for static website (Beginner’s Guide)

# What is NGINX?
  
  NGINX is open source software for web serving, reverse proxying, caching, load balancing, media streaming, and more. It started out as a web server designed for maximum performance and stability. In addition to its HTTP server capabilities, NGINX can also function as a proxy server for email (IMAP, POP3, and SMTP) and a reverse proxy and load balancer for HTTP, TCP, and UDP servers.

# NGINX as a Web Server?

  It started out as a web server designed for maximum performance and stability. NGINX is a powerful web server software used by several hosting companies. Therefore, it offers faster loading times and better performance than most other web servers.Additionally, NGINX uses fewer resources and hardware than other server software.The main purpose of the master process is to read and evaluate configuration files, as well as maintain the worker processes.The worker processes do the actual processing of requests. The number of worker processes is defined by the worker processes directive in the <code>nginx.conf</code> configuration file and can either be set to a fixed number or configured to adjust automatically to the number of available CPU cores.

# Starting the NGINX
  
  To install you need to open your terminal and type:
  
  <code>sudo apt update</code>

  <code>sudo apt install -y nginx</code>

  After installing it,you alredy have every thing you need. The next step is to point your browser to yoour server IP adddress and you should see this page:

  * If you see this page, you have successfully installed Nginx on your web server.

  <picutre>
    <img src="https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/original/2X/7/7504d83a9fe8c09d861b2f7c49e144ac773f0c0d.png">
  </picutre>

* Create your website and get it ready for hosting
  The path where the default html document is located is in

  <code>/var/www/html</code>

  and of course your can read it as it will do for you

  <code>cat /var/www/html/index.html</code>

  And it will look like this:

      <!DOCTYPE html>
      <html>
      <head>
      <title>Welcome to nginx!</title>
      <style>
        body {
            width: 35em;
            margin: 0 auto;
            font-family: Tahoma, Verdana, Arial, sans-serif;
          }
      </style>
      </head>
      <body>
        <h1>Welcome to nginx!</h1>
        <p>If you see this page, the nginx web server is successfully installed and
            working. Further configuration is required.</p>

        <p>For online documentation and support please refer to
        <a href="http://nginx.org/">nginx.org</a>.<br/>
        Commercial support is available at
        <a href="http://nginx.com/">nginx.com</a>.</p>

        <p><em>Thank you for using nginx.</em></p>
      </body>
      </html>

  
* Position yourself in the location listed above this text and create a directory with the name that suits you best.

  <code>cd /var/www </code>

* Create your directory:

  <code>mkdir myFirstWebsite</code>
* After creating the repositories, you need to place your main index.html in your newly created directory. For a display example we can use the following:

      <!doctype html>
      <html>
      <head>
      <meta charset="utf-8">
      <title>Hello, Nginx!</title>
      </head>
      <body>
          <h1>Hello, Nginx!</h1>
          <p>We have just configured our Nginx web server on Ubuntu Server!</p>
      </body>
      </html>
  
# Setting up NGINX virtual host

* To setit up we need to go to file in <code> /etc/nginx/sites-available/</code> and it should look like this:

      ##
      # You should look at the following URL's in order to grasp a solid understanding
      # of Nginx configuration files in order to fully unleash the power of Nginx.
      # https://www.nginx.com/resources/wiki/start/
      # https://www.nginx.com/resources/wiki/start/topics/tutorials/config_pitfalls/
      # https://wiki.debian.org/Nginx/DirectoryStructure
      #
      # In most cases, administrators will remove this file from sites-enabled/ and
      # leave it as reference inside of sites-available where it will continue to be
      # updated by the nginx packaging team.
      #
      # This file will automatically load configuration files provided by other
      # applications, such as Drupal or Wordpress. These applications will be made
      # available underneath a path with that package name, such as /drupal8.
      #
      # Please see /usr/share/doc/nginx-doc/examples/ for more detailed examples.
      ##

      # Default server configuration
      #
      server {
	  listen 80 default_server;
       	  listen [::]:80 default_server;

      # SSL configuration
      #
      # listen 443 ssl default_server;
      # listen [::]:443 ssl default_server;
      #
      # Note: You should disable gzip for SSL traffic.
      # See: https://bugs.debian.org/773332
      #
      # Read up on ssl_ciphers to ensure a secure configuration.
      # See: https://bugs.debian.org/765782
      #
      # Self signed certs generated by the ssl-cert package
      # Don't use them in a production server!
      #
      # include snippets/snakeoil.conf;

      root /var/www/html;

      # Add index.php to the list if you are using PHP
      index index.html index.htm index.nginx-debian.html;

      server_name _;

      location / {
		# First attempt to serve request as file, then
		# as directory, then fall back to displaying a 404.
		try_files $uri $uri/ =404;
	      }

      # pass PHP scripts to FastCGI server
      #
      # location ~ \.php$ {
      #	include snippets/fastcgi-php.conf;
      #
      ## With php-fpm (or other unix sockets):
      #	fastcgi_pass unix:/run/php/php7.4-fpm.sock;
      ## With php-cgi (or other tcp sockets):
      #	fastcgi_pass 127.0.0.1:9000;
      # }

      # deny access to .htaccess files, if Apache's document root
      # concurs with nginx's one
      #
      # location ~ /\.ht {
      #	deny all;
      # }
      }


      # Virtual Host configuration for example.com
      #
      # You can move that to a different file under sites-available/ and symlink that
      # to sites-enabled/ to enable it.
      #
      # server {
      # listen 80;
      # listen [::]:80;
      #
      # server_name example.com;
      #
      # root /var/www/example.com;
      # index index.html;
      #
      # location / {
      # try_files $uri $uri/ =404;
      # }
      # }

* Do you see the problem? <code>root</code> is a where you have to placed our path of index.html file. Index is used to specify file available when visiting root directory of site. server_name can be anything you want, because you aren’t pointing it to any real domain by now. In that directory we need to change the path to our new directory which is located in <code>myFirstWensite</code> . We will do it in the following way

 	<code>nano /etc/nginx/sites-available</code>

      ##
      # You should look at the following URL's in order to grasp a solid understanding
      # of Nginx configuration files in order to fully unleash the power of Nginx.
      # https://www.nginx.com/resources/wiki/start/
      # https://www.nginx.com/resources/wiki/start/topics/tutorials/config_pitfalls/
      # https://wiki.debian.org/Nginx/DirectoryStructure
      #
      # In most cases, administrators will remove this file from sites-enabled/ and
      # leave it as reference inside of sites-available where it will continue to be
      # updated by the nginx packaging team.
      #
      # This file will automatically load configuration files provided by other
      # applications, such as Drupal or Wordpress. These applications will be made
      # available underneath a path with that package name, such as /drupal8.
      #
      # Please see /usr/share/doc/nginx-doc/examples/ for more detailed examples.
      ##

      # Default server configuration
      #
      server {
	  listen 80 default_server;
       	  listen [::]:80 default_server;

      # SSL configuration
      #
      # listen 443 ssl default_server;
      # listen [::]:443 ssl default_server;
      #
      # Note: You should disable gzip for SSL traffic.
      # See: https://bugs.debian.org/773332
      #
      # Read up on ssl_ciphers to ensure a secure configuration.
      # See: https://bugs.debian.org/765782
      #
      # Self signed certs generated by the ssl-cert package
      # Don't use them in a production server!
      #
      # include snippets/snakeoil.conf;

      root /var/www/myFirstWebsite;

      # Add index.php to the list if you are using PHP
      index index.html index.htm index.nginx-debian.html;

      server_name _;

      location / {
		# First attempt to serve request as file, then
		# as directory, then fall back to displaying a 404.
		try_files $uri $uri/ =404;
	      }

      # pass PHP scripts to FastCGI server
      #
      # location ~ \.php$ {
      #	include snippets/fastcgi-php.conf;
      #
      ## With php-fpm (or other unix sockets):
      #	fastcgi_pass unix:/run/php/php7.4-fpm.sock;
      ## With php-cgi (or other tcp sockets):
      #	fastcgi_pass 127.0.0.1:9000;
      # }

      # deny access to .htaccess files, if Apache's document root
      # concurs with nginx's one
      #
      # location ~ /\.ht {
      #	deny all;
      # }
      }


      # Virtual Host configuration for example.com
      #
      # You can move that to a different file under sites-available/ and symlink that
      # to sites-enabled/ to enable it.
      #
      # server {
      # listen 80;
      # listen [::]:80;
      #
      # server_name example.com;
      #
      # root /var/www/example.com;
      # index index.html;
      #
      # location / {
      # try_files $uri $uri/ =404;
      # }
      # }

# Activating and testing results
* Last but not the last step to make our site working, simply restart Nginx service.
  
  <code> sudo systemctl restart nginx</code>

Let’s check if everything works as it should. Open our newly created site in web browser. Remember that we used :80 port.

  <img src="https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/original/2X/c/c541cea4fdab6269a04523060021728a0965e93e.png">
If you see this page the moment you ping the IP address of your server in your browser.Congratulations! Everything works as it should. We have just configured Nginx web server.

# Load Balancer Configuration

* Create or modify the NGINX configuration file to serve as a load balancer. Here's a simple example:
	
		http {
		    upstream backend {
		        server backend1.example.com;
		        server backend2.example.com;
		        # Add more servers as needed
		    }
		
		    server {
		        listen 80;
		        server_name loadbalancer.example.com;
		
		        location / {
		            proxy_pass http://backend;
		            proxy_set_header Host $host;
		            proxy_set_header X-Real-IP $remote_addr;
		            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		            proxy_set_header X-Forwarded-Proto $scheme;
		        }
		    }
		}

 Here, <code>upstream backend</code> defines a group of backend servers, and <code>proxy_pass</code> forwards requests to the defined backend servers.
 
 * Check the syntax of the configuration and restart NGINX: 
 
		sudo nginx -t
		sudo service nginx restart
  
 * Test the load balancer by sending HTTP requests to its address. See how NGINX evenly distributes requests among backend servers.
 * Customize the configuration according to the specific needs of your system. Consider adjusting health check options, server weights, session settings, and other options that suit your requirements.

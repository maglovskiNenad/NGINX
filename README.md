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

  

# Configure NGINX for Ubuntu

Configure Nginx for static website (Beginner’s Guide)

* What is NGINX?
  
    NGINX is open source software for web serving, reverse proxying, caching, load balancing, media streaming, and more. It started out as a web server designed for maximum performance and stability. In addition to its HTTP server capabilities, NGINX can also function as a proxy server for email (IMAP, POP3, and SMTP) and a reverse proxy and load balancer for HTTP, TCP, and UDP servers.

* NGINX as a Web Server?

  It started out as a web server designed for maximum performance and stability.GINX is a powerful web server software used by several hosting companies. Therefore, it offers faster loading times and better performance than most other web servers.Additionally, NGINX uses fewer resources and hardware than other server software.The main purpose of the master process is to read and evaluate configuration files,   as well as maintain the worker processes.The worker processes do the actual processing of requests. NGINX relies on OS-dependent mechanisms to efficiently distribute requests among worker processes. The number of worker processes is defined by the worker processes directive in the nginx.conf configuration file and can either be set to a fixed number or configured to adjust automatically to the number of      available CPU cores.

* Starting the NGINX
  
  To install you need to open your terminal and type:
  
    <code>sudo apt update</code>

    <code>sudo apt install -y nginx</code>

  After installing it,you alredy have every thing you need. The next step is to point your browser to yoour server IP adddress and you should see this page:

  * If you see this page, you have successfully installed Nginx on your web server.

  <picutre>
    <img src="https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/original/2X/7/7504d83a9fe8c09d861b2f7c49e144ac773f0c0d.png">
  </picutre>

# Grav-PHP-Nginx

## A modern approach for a lightweight yet efficient CMS

### At a glance

This aproach for a lightweight Content Management System stack includes four main parts:

+ **Grav** as the lightweight _flat-file_ Content Management System.
+ **Nginx** as a fast and eficient webserver.
+ **PHP-FPM** as the FastCGI engine.
+ **Pushion** as the minimal linux container for this stack.

The idea behind this solution is to have a very light and small footprint CMS that can run efficiently in a flexible environment.

### How to use it

Its very important to note this container expose 3 volumes and 2 ports.
You should properly map the ports when you run the container.

1. Run the container:

   **docker run -d -i -p 80:80 -p 2222:22 ahumaro/grav-php-nginx**
    
   The previous command run the container. If the container it not already in your system, it downloads the image from the Docker Hub.
   
   Two ports are mapped. In the example above, we are mapping port 80 in the host to the port 80 in the container. Also port 2222 in the host to port 22 in the container (This port can be used to access the container via SSH).

2. Test Grav site

   Just point your browser to **`http://your_server/`** and you are done.

You can inspect your new running container to find out the location of the 3 volumes the container is exposing:
+ Volume **/usr/share/nginx/html/**

  Here you can find the Grav home folder where you can add and manage your content.

+ Volume **/etc/nginx/**

  (Optional) Here you can tweak Nginx configuration and sites 

+ Volume **/root/.ssh/**

  (Optional) Here you can put your **public** key so you can access container via SSH. After that, open a SSH connection to root@your_server:2222 specifying your **private** key.
  
### Components

**Grav** is a very fast and simple solution for a CMS. It use flat files to store content. Installation is very simple and is much more easy and light than other CMS's like Drupal or Joomla.
Also is worth to mention that is a very well documented piece of software. 

**Nginx** is a webserver very light and efficient that is strong focused in a small memory footprint and high concurrency and performance.
Also it can be configured as a reverse proxy to handle and solve many scenarios and, in conjunction with **PHP-FPM**, is the way to go to handle and enhance this CMS solution.

**Pushion** base Docker container is a minimal Ubuntu base image modified and minified to be a lightweight Docker compatible container. 
The container is enhanced with key features like the ability to handle SSH access to the container and the ability to add additional daemons that run at the startup time of the container.
 
### Container philosophy

In theory, the use of Docker and containers encourage the one process per container approach but, from the point of view of software as a service, this new container is focused in the one service per container philosophy.

### Dockerfile

The definition for this new **Grav-PHP-Nginx** container perfirm several tasks at build time:

+ Define the base image as **phusion/baseimage:0.9.19**, an excelent minified Ubuntu 16.04 LTS Docker container.
+ Install and update the core components for this new container like Nginx, PHP-FPM, etc.
+ Get Grav up-to-date files from its GIT repository.
+ Run Grav install scripts.
+ Setup Nginx and Grav configuration site.
+ Setup PHP-FPM, Nginx and SSH services.
+ Expose Volumes and ports.

This Docker container is ready and preconfigured. Just download and use it.

### Enjoy this container!
## Ahumaro Mendoza

ahumaro@ahumaro.com

www.ahumaro.com

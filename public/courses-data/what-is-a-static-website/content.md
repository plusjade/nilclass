# What is a Static Website?
{
  "diagramStep" : "internet"
}

Static websites are popular because they are super efficient, extremely fast and usually free to host. Blogs, resumes, marketing websites, landing pages, and documentation are all good candidates for static websites.

Follow along as we visually walk-through the differences and benefits between a static vs dynamic website.


# Static websites serve content directly from the web-server's file-system exactly as stored.
{
  "diagramStep" : "internet",
  "focus" : "HTML",
  "focusPath" : ["User", "Laptop", "Internet", "Server", "Web Server", "Filesystem", "HTML"]
}


# Dynamic websites generate content live per each request
{
  "diagramStep" : "wordpress",
  "focusPath" : ["User", "Laptop", "Internet", "Server", "Web Server", "WordPress"],
  "disable" : ["Filesystem", "HTML", "Image", "Video"]
}

The request is delegated to a running web-application that builds the content.



# WordPress is a popular dynamic web-application framework written in PHP
{
  "diagramStep" : "wordpress-database",
  "focus" : ["WordPress","Database"],
  "focusPaths" : [
    ["User", "Laptop", "Internet", "Server", "Web Server", "WordPress"]
  ]
}


WordPress is installed on your website's hosting server and needs PHP and a MySQL database to run.


# WordPress sends web requests to templates responsible for generating web pages on demand
{
  "diagramStep" : "wordpress-templates",
  "focus" : "Templates",
  "focusPaths" : [
    ["WordPress", "Templates"]
  ]
}

The templates may be coded in PHP and/or other <a href="http://en.wikipedia.org/wiki/Comparison_of_web_template_engines" target="_blank">templating languages</a>.


# Templates execute conditional logic, access other files, and make database queries to generate the final page content
{
  "diagramStep" : "wordpress-full",
  "focus" : "Templates",
  "focusPaths" : [
    ["WordPress", "Templates", "Filesystem"],
    ["Templates", "Database"]
  ]
}

The more code, files, and database queries required the more expensive it is for your server.


# WordPress can be sped up using the WP Super Cache plugin
{
  "diagramStep" : "super-cache",
  "focusPath" : ["User", "Laptop", "Internet", "Server", "Web Server", "Super Cache"],
  "disable" : ["WordPress", "Templates", "Database"]
}

The <strong><a href="https://wordpress.org/plugins/wp-super-cache/" target="_blank">WP Super Cache</a></strong> plugin works with the web-server to completely bypass the WordPress application environment.
Requests are much faster because PHP is no longer executed nor is the database queried.


# WP Super Cache works by using WordPress to pre-build every page of your website
{
  "diagramStep" : "super-cache-full",
  "focus" : ["WordPress", "cached-website"],
  "focusPath" : ["WordPress", "Filesystem", "cached-website"]
}

Instead of WordPress serving the dynamic content, WP Super Cache stores the result as a static HTML file.

# WP Super Cache instructs the web-server to look first in the cached-website folder and serve _that_ page directly
{
  "diagramStep" : "super-cache-full",
  "focus" : "Static Page",
  "focusPath" : ["User", "Laptop", "Internet", "Server", "Web Server", "Super Cache", "Filesystem", "cached-website", "Posts", "Static Page"],
  "disable" : ["WordPress", "Templates", "Database"]
}

The entire WordPress application is completely bypassed!


# The web application is no longer relied upon for expensive conditional logic or database transactions
{
  "diagramStep" : "super-cache-full",
  "crossOut" : ["WordPress", "Database", "Templates"]
}

The cached version of the website is a **static website** because the web-server serves the cached page files to the user directly from the file-system.


# Serving a static website only requires the website's pages be pre-built and stored on the server's filesystem
{
  "diagramStep" : "super-cache-full",
  "focusPath" : ["User", "Laptop", "Internet", "Server", "Web Server", "Filesystem", "cached-website", "Posts", "Static Page"],
  "disable" : ["WordPress", "Templates", "Database", "Super Cache"]
}

The web-server can then serve these files directly.


# Does the entire application even need to be on the server?
{
  "diagramStep" : "super-cache-full",
  "focus" : ["WordPress", "Templates", "Database"],
  "crossOut" : ["WordPress", "Templates", "Database"]
}

WP Super Cache runs WordPress _on the server_ to pre-generate the website pages.
But that means your server needs to run PHP and a MySQL database which is more costly and resource intensive than a static file server.


# Web page files can be generated  _anywhere_, then uploaded to the server
{
  "diagramStep" : "static-site-generator",
  "focus" : "Static Site Generator",
  "focusPath" : ["Static Site Generator", "ssg-Templates", "ssg-Filesystem"]
}

A static website generator is a program that generates static websites in a completely standalone way. There are many <a href="http://staticsitegenerators.net/" target="_blank">static website generator's</a> made in a variety of programming languages.


# Your personal computer can run Static website generators
{
  "diagramStep" : "static-site-generator-full",
  "focus" : "Static Site Generator",
  "focusPaths" : [
    ["You", "Your Laptop", "Static Site Generator", "ssg-Templates", "ssg-Filesystem"]
  ]
}

But this implies your computer must be setup to run a programming language like PHP, Ruby, Javascript, and maybe even a database. This might not always be possible, especially for non-technical users.


# Static Website Generation as a Service
{
  "diagramStep" : "site-generator-service",
  "focus" : "Service",
  "crossOut" : "Static Site Generator",
  "focusPaths" : [
    ["You", "Your Laptop", "ssg-Templates", "ssg-Filesystem"],
    ["You", "Your Laptop", "Internet", "Service", "ssg-Service"]
  ]
}

A static website generator service allows you to upload templates via their website which they process _for you_.
You can use your own text-editor or web browser interface to edit and upload your templates to the service. 

# The website generation service publishes your site by uploading the generated files to a static file server for hosting
{
  "diagramStep" : "push-published-site",
  "focusPath" : ["Service", "Published Site"]
}


# Static File Servers are extremely fast, can handle tons of traffic, and fail much less often
{
  "diagramStep" : "published-site",
  "focus" : "Published Site",
  "focusPath" : ["User", "Laptop", "Internet", "Published Site", "published-web-server", "published-filesystem", "published-html"]
}


# Recap: Dynamic websites execute templates live on the server
{
  "diagramStep" : "recap",
  "focus" : "recap-application",
  "focusPath" : ["User", "Laptop", "Internet", "Server", "Web Server", "recap-application"]
}

This makes sense if your content _needs to be live_, or manage users, user sessions, access level controls, admin-panels, e-commerce, and so on.



# Static websites get a huge performance boost from pre-generating the templates _off-server_
{
  "diagramStep" : "recap",
  "focus" : "Static Site Generator",
  "focusPaths" : [
    ["Your Laptop", "Static Site Generator", "ssg-Templates", "ssg-Filesystem"]
  ]

}


# The End
{
  "diagramStep" : "recap"
}

I hope you learned more about the benefits of static websites. This course is still in development so check back frequently!
Please provide feedback or ask questions about the material by tweeting  <a href="http://twitter.com/plusjade" target="_blanks">@plusjade</a> or emailing <a href="mailto:plusjade@gmail.com">plusjade@gmail.com</a> - Thanks for learning!

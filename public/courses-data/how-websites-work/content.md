# How Websites Work.
{
    "diagramStep" : "start",
    "focus" : "You"
}

We all love browsing web sites because they are super useful and fun!
But where does a web-page come from? How does it get created?

Follow along as we go behind the scenes and visually explore how web sites work from personal blogs to massive sites like <a href="http://www.amazon.com/">Amazon.com</a>.


# Web pages are viewed using a software-progam called a web-browser.
{
    "diagramStep" : "web-browser",
    "focus" : "Web Browser",
    "focusPath" : ["You", "Web Browser"]
}


# Web browsers run on your laptop or smartphone just like Excel or Photoshop.
{
    "diagramStep" : "web-browser-platforms",
    "focus" : ["Laptop", "Phone", "Tablet"],
    "focusPath" : ["You", "Web Browser", "Laptop"]
}


# The web browser downloads Content over the Internet.

{
    "diagramStep" : "internet",
    "focus" : "Internet",
    "focusPath" : ["You", "Laptop", "Internet"]
}

It can download and stream media like text, images, pdfs, movies, and music.

# This content is stored on other computers called servers
{
    "diagramStep" : "server",
    "focus" : "Server"
}

A server is just a computer. It contains files in its filesystem just like the files and folders on your personal computer.


# Servers that accept Internet requests are called Web Servers
{
    "diagramStep" : "static-server",
    "focus" : "Web Server",
    "focusPath" : ["You", "Laptop", "Internet", "Server", "Web Server"]
}

In order to accept requests coming in over the Internet, the server runs a software program called a <strong>web-server</strong>.

# The web-server software dictates which files and programs are OK to be accessed from the Internet.
{
    "diagramStep" : "security-gate",
    "focusPaths" : [
        ["You", "Laptop", "Internet", "Server", "Web Server", "Filesystem"],
        ["Filesystem", "HTML"],
        ["Filesystem", "Image"],
        ["Filesystem", "Video"]
    ],
    "disable" : ["Passwords", "Secrets"]
}

Servers have private files you need to deny outside access to, so when web requests come in they are handled <em>only</em> by the web-server which acts as a kind of security gate.


# Web pages are just media like videos, images, and text.
{
    "diagramStep" : "security-gate",
    "focus" : ["Filesystem", "HTML", "Video", "Image"],
    "focusPath" : ["You", "Laptop", "Internet", "Server", "Web Server", "Filesystem"]
}

When a request comes in, the server processes the request and sends back content that will make up the web-page you see.
Youtube sends videos, Instagram sends images, and Spotify streams audio files.

The simplest way to send this content to the user is for the web-server to retrieve it from its own <strong>filesystem</strong>.


# Does that mean Amazon.com has millions of product pages stored as files?
{
    "diagramStep" : "static-server-amazon",
    "focus" : ["product-1","product-2","product-3","product-4"]
}

<a href="http://www.amazon.com/">Amazon.com</a> has web pages for millions of products. 
But creating millions of product page files would take forever and be hard to maintain.
Updating the product page layout would require changing every single file!


# A web application can create pages on demand.
{
    "diagramStep" : "web-application",
    "focus" : ["Application", "Templates"],
    "focusPath" : ["Application", "Templates"]
}

A web application is a software program. It can do work <em>on demand</em> like read from a template file and build a custom page <em>dynamically</em>.
This means web pages don't actually have to exist, an application can create them as needed.


# The web-server routes requests to the _Web Application_
{
    "diagramStep" : "web-application",
    "focus" : "Application",
    "focusPath" : ["You", "Laptop", "Internet", "Server", "Web Server", "Application"]
}

Instead of serving files directly, the web-server is configured to route web-requests to the web application running live on your server.


# A web application can interact with a database.
{
    "diagramStep" : "database",
    "focus" : "Database",
    "focusPath" : ["Application", "Templates", "Database"]
}

A database is a software program installed on the server that helps with efficiently storing and accessing data.

We can use a database to store Amazon's millions of products as data: `description, price, sizes, images`.


# The web application queries the database to populate its templates.
{
    "diagramStep" : "database",
    "focus" : "Templates",
    "focusPath" : ["Application", "Templates", "Database", "Product 1"]
}

The app makes a query to the database for product data then uses the data to populate a page template that has placeholder values like {price}, {description}, etc.
Now if you want change the product template, you only have to change one file. =)


# A Dedicated Database Server can Handle More Requests
{
    "diagramStep" : "dedicated-database",
    "focus" : "Database Server"
}

So far all our software programs have been running on <em>one</em> physical server. But each server has physical limits in how many requests it can handle.
To handle more requests, or <em>scale</em> your application, you can move your database software to its own dedicated database server.

# Dedicated App Servers and Database Servers
{
    "diagramStep" : "dedicated-database",
    "focus" : ["Server", "Database Server"]
}

Now your app server can concentrate on serving web-requests, while your database-server gets more computing power to manage the database.


# One lonely server may be a bottleneck
{
    "diagramStep" : "dedicated-database",
    "focus" : "Server",
    "focusPaths" : [
        ["Anna", "Phone Web Browser", "Phone", "Internet", "Server"],
        ["You", "Web Browser", "Laptop", "Internet", "Server"],
        ["Pinky", "Tablet Web Browser", "Tablet", "Internet", "Server"]
    ]
}

The application server is no longer handling the database load, but it is still solely responsible for **ALL** requests =/.

# Use Multiple Application Servers to Distribute The Request Load
{
    "diagramStep" : "multi-app-architecture",
    "focusPaths" : [
        ["Anna", "Phone Web Browser", "Phone", "Internet", "Server (clone 2)"],
        ["You", "Web Browser", "Laptop", "Internet", "Server (clone 1)"],
        ["Pinky", "Tablet Web Browser", "Tablet", "Internet", "Server"]
    ]
}

All computers ultimately have physical limits so we should help this poor server out by adding more of his friends to share the load.
But how do we send requests to the new servers?


# A reverse-proxy server delegates or <em>proxies</em> requests across multiple application servers.
{
    "diagramStep" : "reverse-proxy",
    "focus" : "Reverse Proxy",
    "focusPaths" : [
        ["Anna", "Phone Web Browser", "Phone", "Internet", "Reverse Proxy"],
        ["You", "Web Browser", "Laptop", "Internet", "Reverse Proxy"],
        ["Pinky", "Tablet Web Browser", "Tablet", "Internet", "Reverse Proxy"]
    ]
}


The reverse-proxy is inserted <em>before</em> our app-servers so requests go directly to the reverse-proxy.

# The web server on the reverse proxy server routes requests to other servers
{
    "diagramStep" : "reverse-proxy-web-server",
    "focus" : "Reverse Proxy",
    "focusPaths" : [
        ["Anna", "Phone Web Browser", "Phone", "Internet", "Reverse Proxy", "reverse-proxy-web-server", "Server"],
        ["You", "Web Browser", "Laptop", "Internet", "Reverse Proxy", "reverse-proxy-web-server", "Server (clone 1)"],
        ["Pinky", "Tablet Web Browser", "Tablet", "Internet", "Reverse Proxy", "reverse-proxy-web-server", "Server (clone 2)"]
    ]
}

Instead of serving a specific web-application software program, a web-server can be configured to route requests to <em>other servers</em>.
Find out more here: <a href="http://stackoverflow.com/a/366212/101940">http://stackoverflow.com/a/366212/101940</a>.


# Scaling horizontally: Using Many small application servers
{
    "diagramStep" : "reverse-proxy-web-server",
    "focus" : ["Server", "Server (clone 1)", "Server (clone 2)"],
    "focusPaths" : [
        ["Anna", "Phone Web Browser", "Phone", "Internet", "Reverse Proxy", "reverse-proxy-web-server", "Server"],
        ["You", "Web Browser", "Laptop", "Internet", "Reverse Proxy", "reverse-proxy-web-server", "Server (clone 1)"],
        ["Pinky", "Tablet Web Browser", "Tablet", "Internet", "Reverse Proxy", "reverse-proxy-web-server", "Server (clone 2)"]
    ]
}

Scaling horizontally is usually very cost effective because it's cheaper to buy many commodity servers than a few powerful servers.

# Scaling horizontally mitigates risk
{
    "diagramStep" : "reverse-proxy-web-server",
    "focusPaths" : [
        ["Anna", "Phone Web Browser", "Phone", "Internet", "Reverse Proxy", "reverse-proxy-web-server", "Server (clone 1)"],
        ["You", "Web Browser", "Laptop", "Internet", "Reverse Proxy", "reverse-proxy-web-server", "Server (clone 1)"],
        ["Pinky", "Tablet Web Browser", "Tablet", "Internet", "Reverse Proxy", "reverse-proxy-web-server", "Server (clone 2)"]
    ]
    ,
    "crossOut" : ["Server"],
    "disable" : ["Web Server", "Application", "Templates", "Filesystem"]
}

If you only have one powerful server and it fails, your site goes down. Many servers means some can fail and the others will pick up the load.


# A centralized database server maintains data integrity across application servers
{
    "diagramStep" : "reverse-proxy-web-server",
    "focus" : ["Database Server"],
    "focusPaths" : [
        ["Server", "Web Server", "Application", "Database Server"],
        ["Server (clone 1)", "Web Server clone 1", "App clone 1", "Database Server"],
        ["Server (clone 2)", "Web Server clone 2", "App clone 2", "Database Server"]
    ]
}

This solves the case where a user's request will be handled by app1 first, then another request by the same user is handled by app2. 
The data should be the same across both request scenarios.


# The end
{
    "diagramStep" : "reverse-proxy-web-server",
    "focus" : ["You"]
}

This is a basic walkthrough, but it is indeed how modern web applications generally work!
I'll try to add more concepts over time and feel free to provide feedback or ask questions about the material by tweeting  <a href="http://twitter.com/plusjade" target="_blanks">@plusjade</a> or emailing <a href="mailto:plusjade@gmail.com">plusjade@gmail.com</a> - Thanks!

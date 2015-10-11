## ExpressJS Overview
#### Learning Objectives
* [Introduction](#)
* [Installing Dependencies](#installing-dependencies)
* [Configure applications with package.json](#)
* [Synchronous routing](#)
* [JavaScript MVC](#)
* [Dynamic templating](#)
* [Asynchronous routing](#)
* [Debugging http requests](#)
* [Resources](#resources)

#### Introduction
>Fast, unopinionated, minimalist web framework for Node.js  
>-expressjs.com

The goal of this project is to provide a step by step, introduction to Node, Express and eventually MongoDB and Angular. My intention is to initially present each of these technologies with as few dependencies (libraries, frameworks, modules, etc) as possible in order to increase your understanding of their innerworkings, that said, once we've done things the hard way we'll circle back and play some with some cool tech.

This approach is meant to clarify some of the magic that goes on behind the scenes. I find value in building a web app from the ground up without a scaffold, hopefully you do too. The first project will be a bit trivial, but will become more involved and hopefully interesting as it grows.

#### Installing Dependencies
>“There are two questions a man must ask himself: The first is 'Where am I going?' and the second is 'Who will go with me?' 

>If you ever get these questions in the wrong order you are in trouble.” 

>― Sam Keen, Fire in the Belly: On Being a Man

##### Node.js
The first and most integral dependency is Node, it grants the flexibility to:

* create web servers
* integrate modules (libraries)
* quickly create scalable applications

**Download** the pre built Node installer here: https://nodejs.org/en/download/
Check that your install has completed successfully:

```
node -v
# v0.12.7
```

Now that Node is installed we have access to 'npm.' It would make sense to assume that npm stands for Node Package Manager, but the reality is that it is not an acronym. npm helps us manage the dependencies for our application, including module installation through command line.
##### Configuring your first ExpressJS Application
Create a new directory for the application, and navigate inside of it.

```
mkdir expressGrandma
cd expressGrandma
```

Now we need to create a 'package.json' file for our application. There are several rules about what information is required within package.json, all of which are covered in the npm docs (https://docs.npmjs.com/files/package.json). Luckily, npm will help us set up our package.json file via command line:

```
npm init
# This utility will walk you through creating a package.json file.
# It only covers the most common items, and tries to guess sensible defaults.

# See `npm help json` for definitive documentation on these fields
# and exactly what they do.

# Use `npm install <pkg> --save` afterwards to install a package and
# save it as a dependency in the package.json file.

# Press ^C at any time to quit.
# name: (expressGrandma) 
```

For the time being we will use all of the default settings npm presents us with, simply press 'return' until you are presented with:


```
# Is this ok? (yes)
```

Enter: **yes**

Now if you list the files in the directory you should see a package.json file.

```
ls
# package.json
```

Finally, let's install the express module using npm, and save the dependency to our package.json file. This can be accomplished using the '--save' option. In order to install a module we use the 'install' term with npm followed by the package name. We want to save the dependency, so we will append the '--save' option as well.

```
npm install express --save

# npm WARN package.json tester@1.0.0 No README data
# express@4.13.3 node_modules/express
# ├── escape-html@1.0.2
# ├── merge-descriptors@1.0.0
# ├── array-flatten@1.1.1
# ├── utils-merge@1.0.0
# ├── methods@1.1.1
# ├── fresh@0.3.0
# ├── cookie-signature@1.0.6
# ├── range-parser@1.0.2
# ├── cookie@0.1.3
# ├── vary@1.0.1
# ├── path-to-regexp@0.1.7
# ├── content-type@1.0.1
# ├── etag@1.7.0
# ├── parseurl@1.3.0
# ├── content-disposition@0.5.0
# ├── serve-static@1.10.0
# ├── depd@1.0.1
# ├── qs@4.0.0
# ├── on-finished@2.3.0 (ee-first@1.1.1)
# ├── finalhandler@0.4.0 (unpipe@1.0.0)
# ├── debug@2.2.0 (ms@0.7.1)
# ├── proxy-addr@1.0.8 (forwarded@0.1.0, ipaddr.js@1.0.1)
# ├── send@0.13.0 (destroy@1.0.3, statuses@1.2.1, ms@0.7.1, # mime@1.3.4, http-errors@1.3.1)
# ├── type-is@1.6.9 (media-typer@0.3.0, mime-types@2.1.7)
# └── accepts@1.2.13 (negotiator@0.5.3, mime-types@2.1.7)
```

Don't worry about that `npm WARN package.json tester@1.0.0 No README data`, all that is telling you is that you haven't added README data to the package.json file, we may or may not do that later, but for now it won't get in our way. The rest of the text is the list of express dependencies that were added to the project.

If you run the list program you will see that there is a new directory in your project.

```
ls
# node_modules    package.json
```

Looking inside of node_modules you'll find express, and looking inside of express you find a node_modules directory (that's where all of those express dependencies went when we installed it)!

```
ls node_modules/
# express

ls node_modules/express/
# History.md  Readme.md lib   package.json
# LICENSE   index.js  node_modules

ls node_modules/express/node_modules/
# accepts     methods
# array-flatten   on-finished
# content-disposition parseurl
# content-type    path-to-regexp
# cookie      proxy-addr
# cookie-signature  qs
# debug     range-parser
# depd      send
# escape-html   serve-static
# etag      type-is
# finalhandler    utils-merge
# fresh     vary
# merge-descriptors
```

#### Our First Express Route

Now that we have express installed and our package.json file configured, let's stick with convention and deploy `Hello World!` to a real live web browser! Let's start super simple.

The first step is to create a javascript file to hold our routes and server configuration: `touch app.js`

Let's walk step by step through the code as we add it. Declare a variable 'express' to include the express module we installed with npm. This will give us access to all of expresses sub-modules. Then declare an 'app' variable and set it equal to the 'express()' top level function. This is convention and will give us access to the main application.

```javascript
// app.js
var express = require('express');
var app = express();
```

Next let's configure our server (localhost) so that we can run our app and make sure everything is going as planned. The simplest form ths could take is:

```javascript
// app.js
app.listen(3000, function() {
  console.log("expressGrandma is listening on port 3000!");
});
```

The official express have us make this a little bit more maleable, and have us store our server configuration as a variable, ultimately using a formatted string to print out the port specifications we've assigned.

```javascript
// app.js
var server = app.listen(3000, function() {
  var host = server.address().address;
  var port = server.address().port;

  console.log('expressGrandma listening at http://%s:%s', host, port);
});
```

This is better code, more abstract/reusable, and unnecessary for our current purposes. I just wanted to make you aware that this is how this looks in the "getting started" documentation.

Now we can use node to have our server start listening:

```
node app.js
```

Opening a browser and navigating to 'localhost:3000' we see...

![Image of Cannot GET /](/imgs/cannot_get.png)

...that was pretty anti-climactic. We still haven't added any routes, so the browser isn't served any content by our server when we navigate to port 3000. Let's set up a route to serve the browser "Hello World!".

In 'app.js' let's build a 'GET' route to serve data to the client. Routes in Express follow the `app.METHOD(PATH,HANDLER)` convention. 'app' is an instance of express, METHOD is the http request method, PATH is a path on our server, and the HANDLER is a function that will execute when the route is called. The 'GET' method is used to request/serve data, since we want to serve "Hello World!" that's the one we'll be using. Following the `app.METHOD(PATH, HANDLER)` convention our route will look something like this:

```javascript
// app.js
app.get('/', function(request, response) {

});
```

Here we are using the 'GET' http method, the path is '/' which is the root of our application, and we are passing our anonumous handler function to parameters, request (being the information sent to the server) and response (the data we will send back to the client). NOTE: these are typically written with the shorthand (req, res).

Now we have a route, but we aren't responding with any data. Let's see if anything has changed when we navigate to 'localhost:3000':

![Image of no response](/imgs/get_no_send.png)

Hmmm, not quite what we were looking for. Our browser seems hung up waiting for a response, which makes sense, because we aren't sending one. Let's change that. 

The '.send()' can be called on the response parameter and passed a String, Buffer Object, Object, or Array. All we want to do is have "Hello World!" display on the client, so lets try just sending that as a String. Modify the GET route like so:

```javascript
// app.js
app.get('/', function(req, res) {
  res.send("Hello World!");
});
```

Refresh the browser and...

![Image of Hello World](/imgs/hello_world.png)


#### Resources  
  * [Node Docs](https://nodejs.org/en/docs/)
  * [Express Docs](http://expressjs.com/4x/api.html)
  * [npm Docs](https://www.npmjs.com/)
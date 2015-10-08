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

#### Installing Dependencies
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

Now that Node is installed we have access to Node Package Manager ('npm'). npm helps us manage the dependencies for our application, including module installation through command line.
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

Enter: yes

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





#### Resources  
  * [Node Docs](https://nodejs.org/en/docs/)
  * [Express Docs](http://expressjs.com/4x/api.html)
  * [npm Docs](https://www.npmjs.com/)
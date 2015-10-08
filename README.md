## ExpressJS Overview
#### Learning Objectives
* <a href="#dependencies">Express and Node dependencies</a>
* <a href="#package">Configure applications with package.json</a>
* <a href="#sync">Synchronous routing</a>
* <a href="#mvc">JavaScript MVC</a>
* <a href="#templating">Dynamic templating</a>
* <a href="#async">Asynchronous routing</a>
* <a href="#debug">Debugging http requests</a>

#### What is Express?
>Fast, unopinionated, minimalist web framework for Node.js  
>-expressjs.com
#### <a name="dependencies">Installing Dependencies</a>
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

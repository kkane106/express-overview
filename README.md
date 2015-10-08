<h2>ExpressJS Overview</h2>
  <h4>Learning Objectives</h4>
    <ul>
      <li><a href="#dependencies">Express and Node dependencies</a></li>
      <li><a href="#package">Configure applications with package.json</a></li>
      <li><a href="#sync">Synchronous routing</a></li>
      <li><a href="#mvc">JavaScript MVC</a></li>
      <li><a href="#templating">Dynamic templating</a></li>
      <li><a href="#async">Asynchronous routing</a></li>
      <li><a href="#debug">Debugging http requests</a></li>
    </ul>
<hr>
  <h4>What is Express?</h4>
    <blockquote>Fast, unopinionated, minimalist web framework for Node.js -expressjs.com</blockquote>
  <h4><a name="dependencies">Installing Dependencies</a></h4>
     <h5>Node.js</h5>
       <p>The first and most integral dependency is Node, it grants the flexibility to:</p>
       <ul>
         <li>create web servers</li>
         <li>integrate modules (libraries)</li>
         <li>quickly create scalable applications</li>
       </ul>
       <p><strong>Download</strong> the pre built Node installer here: https://nodejs.org/en/download/</p>
       <p>Check that your install has completed successfully:</p>
```bash
node -v
# v0.12.7
```
       <p>Now that Node is installed we have access to Node Package Manager ('npm'). npm helps us manage the dependencies for our application, including module installation through command line.</p>
    <h5>Configuring your first ExpressJS Application</h5>
      <p>Create a new directory for the application, and navigate inside of it.</p>
```bash
mkdir expressGrandma
cd expressGrandma
```
      <p>Now we need to create a 'package.json' file for our application. There are several rules about what information is required within package.json, all of which are covered in the npm docs (https://docs.npmjs.com/files/package.json). Luckily, npm will help us set up our package.json file via command line:</p>
```bash
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

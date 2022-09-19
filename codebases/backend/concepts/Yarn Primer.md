### Yarn v1: Alternative to the node package manager (`npm`)

`yarn` is a package manager for `node`. It provides more functionality over `npm` and is better at resolving dependencies, which is why most developers use it.  `node` is a JavaScript runtime for your operating system which comes with `npm` as the default package manager. `node` is special because it takes the JavaScript from the browser and allows it to run on your computer. It has some OS specific functionality as well - reading files, spawning child processes, bootstrapping servers, crypto etc. Adding this functionality would not have been possible within the confines of a browser runtime. 

The backend project contains a  `package.json` file. This file lists all dependencies and developer dependencies. Also contains some project metadata. It was generated using `yarn init`.  

TLDR for `yarn` commands:

- `yarn add <package_name>` : Install a package. Packages can be found on https://www.npmjs.com. This will generate (or update) a `yarn.lock` file. Do not touch this file. The `package.json`  dependancy list will be updated as well, with the newly installed package. 

- `yarn upgrade-interactive --latest`: Interactive GUI to update dependencies

- `yarn add -D <package_name>` : Install a developer dependency. These dependencies are not very important to the business and are stripped out of the production codebase. These usually include packages which help the developers setup the project environment and automate certain tasks. Stuff like the `typescript` compiler will go here.  The `package.json`  and `yarn.lock`  will be updated. 

- `yarn`: Install all the dependencies listed in `package.json`. A `node_modules` folder will be created as well, but this should not concern the developer and can be ignored. Do not mess around with this folder. 

We can add custom `yarn` scripts as well which can be called from time to time to execute certain tasks. These are defined in the `package.json` file as well under the `scripts` property.

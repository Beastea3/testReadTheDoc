# Node.Js with C++ Add-ons

## CommonJS module standard
1. `require` is a function which represent it is a module;
2. Module Context: each object in module.exports will be exported to the outside;
3. Located by absolute path or relative path, and should not be with `.js` extentions;


## Node.JS categories of modules
1. Node.JS core modules, like `fs`, `net`;
2. 3-rd party modules, like the modules installed by npm, `express`, `koa` are both 3-rd party modules;
3. Project modules, the project files which you integrated them into your infrastructure;

## Construction of npm packages
1. `package.json` in the root directory of the package;
2. Binary file should be in the `/bin` directory;
3. JavaScript source code should be in `/lib`;
4. Documents should be in `/doc`;
5. Unit test file should be put in `/test`;

## NPM 2 Vs NPM 3+
NPM was used by Node.JS only in the beginning, but after the usage among frontend spread, NPM change its package construction into flat design. But the author thinks it is not good to Node.JS developers, because the scenarios when u want to hack some basic modules, in flattened design, change will impact all modules depended on the module you hacked.

## How the C++ Add-on works

Actually, when requires a C++ Add-on is to require a dynamic link library when node program executed.
When requires a node module

 - Check if the module has loaded in the cache
 - Check if the module is a non internal module
 - Use `new Module()`
 
Hence, once a module has been loaded, Node will reload it from cache when require again.

## Memory Mechanism

- Chrome V8 is to explain and execute JavaScript
- libuv is to realize the Event Loop in Node.js

There are several stack memory in Chrome V8:

- New Generation Memory area
 - small but refresh fast
 - some object will hoist to old generation area
  1. Live through a new generation refresh 
  2. 25 percent of to space has been used
- Old Generation pointer area
 - slow but huge
 - hybrid Mark-Sweep, Mark-Compact and Lazy clean up
- Old Generation data area
- Big Object area
- code area
- cell area, property area and map area.

### Handle

*Why handle instead of pointer?*

The Objects in V8 are usually moving around, so pointer will become a wild pointer which point to something unexpected. A handle will be updated when the object is moved, so the handle is more reliable in this scenario.



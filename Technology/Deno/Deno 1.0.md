# Deno 1.0 Summary

 [Deno 1.0](https://deno.land/v1)

 ## Why dynamic language?

 * Allows develpers complete a complex system rapidly w/o worring about the low-level details like GC or memory management;
 * Although Go and Rust have made it easier to produce native machine code, scripting is still a powerful and invaluable util to solve a wider range of problems, JS is far not reach the the limit of itself;
 * Javascript is most widely-used, it can almost run on any devices and any environments.
 * ECMA international supports the rule of syntax of JS, which ensure the continuous and stable increasement of JS;
 
## Why not Node.js?

 * Node.js was designed in 2009, and in that time, JS was much different, Node.js is not go well with today's JS.
 * Some other design mistakes[Design Mistakes in Node](https://www.youtube.com/watch?v=M3BM9TB-8yA), refer to the comment from Anton Rich:


    The goal of Node was event driven HTTP servers.

    1 Regret: Not sticking with Promises.
    * I added promises to Node in June 2009 but foolishly removed them in February 2010.
    * Promises are the necessary abstraction for async/await.
    * It's possible unified usage of promises in Node would have sped the delivery of the eventual standartization and async/await.
    * Today Node's many async APIs are aging baldly due to this.

    6:02
    2 Regret: Security
    * V8 by itself is a very good security sandbox
    * Had I put more thought into how that could be maintained for certain applications, Node colud have had some nice security guarantees not available in any other language.
    * Example: Your linter shouldn't get complete access to your computer and network.

    7:01
    3 Regret: The Build System (GYP)
    * Build systems are very difficult and very important.
    * V8 (via Chrome) started using GYP and I switched Node over in tow.
    * Later Chrome dropped GYP for GN. Leaving Node the sole GYP user.
    * GYP is not an ugly internal interface either - it is exposed to anyone who's trying to bind to V8.
    * It's an awful experience for users. It's this non-JSON, Python adaptation of JSON.
    * The continued usage of GYP is the probably largest failure of Node core.
    * Instead of guiding users to write C++ bindings to V8, I should have provided a core foreign function interface (FFI)
    * Many people, early on, suggested moving to an FFI (namely Cantrill) and regrettably I ignored them.
    * (And I am extremely displeased that libuv adopted autotools.)

    9:52
    4 Regret: package.json
    * Isaac, in NPM, invented package.json (for the most part)
    * But I sanctioned it by allowing Nod's require() to inspect package.json files for "main"
    * Ultimately I included NPM in the Node distribution, which much made it the defacto standard.
    * It's unfortunate that there is centralized (privately controlled even) repository for modules.
    * Allowing package.json gave rise to the concept of a "module" as a directory of files.
    * This is no a strictly necessary abstraction - and one that doesn't exist on the web.
    * package.json now includes all sorts of unnecessary information. License? Repository? Description? It's boilerplate noise.
    * If only relative files and URLs were used when importing, the path defines the version. There is no need to list dependencies.

    12:35
    5 Regret: node_modules
    * It massively complicates the module resolution algorithm.
    * vendored-by-default has good intentions, but in practice just using $NODE_PATH wouldn't have precluded that.
    * Deviates greatly from browser semantics
    * It's my fault and I'm very sorry.
    * Unfortunately it's impossible to undo now.

    14:00
    6 Regret: require("module") without the extension ".js"
    * Needlessly less explicit.
    * Not how browser javascript works. You cannot omit the ".js" in a script tag src attribute.
    * The module loader has to query the file system at multiple locations trying to guess what the user intended.

    14:40
    7 Regret: index.js
    * I thought it was cute, because there was index.html
    * It needlessly complicated the module loading system.
    * It became especially unnecessary after require supported package.json

    15:28 Talks about Deno.


## How about Deno?

### Decentralized Dependency

Unlike the NPM, deno can use scripts all around the web.

```js
import { serve } from "https://deno.land/std@0.50.0/http/server.ts";

for await (const req of serve({ port: 8000 })) {
  req.respond({ body: "Hello World\n" });
}
```

This is a code segment which start a http server.

### Security

In Deno, all scripts are executed in a sandbox by default, and have no access to the resources of the device. So we need to add a parameter `--alow-net` to alow the server above get the access to the network.

## Strong Type Restriction - TS

All Deno's standart modules are written in TS, which means deno is originally type sensitive.


## Optimized Promises

Node.js's Promise need to add `pause()` to prevent flooding, which results in 
considerable tail latency. In Deno, the event will only receive data after users explicidly `read()`. Which means less code and more effecient.

## RUST APIs

Deno use RUST crate in its low-level, `rusty-v8` is a zero-cost binding to the C++ v8.

*Limitaions*
## HTTP Server Performance

Simple Hello World Serevr, Deno vs Node

Deno: 26k qps with 1.3 ms latency,
Node: 34k qps with 2 - 300 ms latency.

## Plugins and Extensions

Due to the nascent plugin system, the interface is still under development and marked as unstable.

## TSC Bottleneck

The TypeScript compiler is very slow in deno in this time, the optimization is on the way.





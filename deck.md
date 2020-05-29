---
theme: uncover
---
<style>
  section {
    background: #282828;
    font-family: helvetica;
    color: #fbf1c7;
  }

  section a {
    color: #458588;
  }
  
  pre {
    background:  #d5c4a1;
    box-shadow: none;
    border: 1px solid #fbf1c7;
    color: #282828;
  }

  code {
    background: #d5c4a1;
    color: #282828;
  }
</style>

# Deno
![width:500px](https://deno.land/favicon.svg)

---

![](./images/deno-circle-24fps.gif)

---

Deno is a simple, modern and secure runtime for JavaScript and TypeScript.

It's built on V8, Rust, and Tokio.

---

# Why deno?

Node.js is stable, widely used, and works (mostly) fine.

---

![](./images/modern.jpg)

---

# Philosophy

Deno aims to be a productive and secure scripting environment for the modern
programmer.

---

# Philosophy

Deno will always be distributed as a single executable. Given a URL to a Deno program, it is runnable with nothing more than the ~15 megabyte zipped executable. Deno explicitly takes on the role of both runtime and package manager. It uses a standard browser-compatible protocol for loading modules: URLs.

---

# Major Highlights

- Secure by default. No file, network, or environment access, unless explicitly
  enabled.
- Supports TypeScript out of the box.
- Ships only a single executable file.

---

# Major Highlights

- Has built-in utilities like a dependency inspector (deno info) and a code
  formatter (deno fmt).
- Has a set of reviewed (audited) standard modules that are guaranteed to work
  with Deno: [deno.land/std](deno.land/std)

---

# Comparison to Node.js

- Deno does not use `npm` or a `package.json`
- All async actions in Deno return a promise.
- Deno requires explicit permissions for file, network, and environment access.
- Deno always dies on uncaught errors.

--- 

# Installation

Deno ships as a single executable with no dependencies.

```
curl -fsSL https://deno.land/x/install/install.sh | sh

iwr https://deno.land/x/install/install.ps1 -useb | iex

brew install deno

cargo install deno
```

---

# Environment Setup

### Shell Autocomplete

You can generate completion script for your shell using the `deno completions <shell>` command. 

---

# Environment Setup

### Editors

Because Deno requires the use of file extensions for module imports and allows http imports, and most editors and language servers do not natively support this at the moment, many editors will throw errors about being unable to find files or imports having unnecessary file extensions.

---

# Permissions *

Deno is secure by default. Therefore, unless you specifically enable it, a deno module has no file, network, or environment access for example. 

Access to security sensitive areas or functions requires the use of permissions to be granted to a deno process on the command line.

---

# Permissions

- -A, --allow-all Allow all permissions. This disables all security.

- --allow-net=\<allow-net> Allow network access. You can specify an optional, comma separated list of domains to provide a whitelist of allowed domains.

- --allow-read=\<allow-read> Allow file system read access. You can specify an optional, comma separated list of directories or files to provide a whitelist of allowed file system access.

---

# External Code *

We saw Deno could execute scripts from URLs. Like browser JavaScript, Deno can import libraries directly from URLs. This example uses a URL to import an assertion library:

```
import { assertEquals } from 
  "https://deno.land/std/testing/asserts.ts";

assertEquals("hello", "hello");
assertEquals("world", "world");

console.log("Asserted! 🎉");
```

--- 

# External Code

Deno caches remote imports in a special directory specified by the $DENO_DIR environment variable.

---

# Other cool features *


```
deno install

deno install --allow-net --allow-read https://deno.land/std/http/file_server.ts
```

---

To define a test you need to call Deno.test with a name and function to be tested:

```
Deno.test("hello world", () => {
  const x = 1 + 2;
  if (x !== 3) {
    throw Error("x should be equal to 3");
  }
});
```

---

It is possible to debug Deno programs using Chrome Devtools or other clients that support the protocol (eg. VSCode).

To activate debugging capabilities run Deno with `--inspect` or `--inspect-brk` flag.

`--inspect` flag allows to attach debugger at any point in time, while `--inspect-brk` will wait for debugger being attached and pause execution on the first line of code.

---

`deno fmt`

---

`deno bundle [URL]` will output a single JavaScript file, which includes all dependencies of the specified input. For example:

```
> deno bundle https://deno.land/std/examples/colors.ts colors.bundle.js
Bundling "colors.bundle.js"
Emitting bundle to "colors.bundle.js"
9.2 kB emitted.
```

---

`deno info [URL]`

---

```
deno info https://deno.land/std@0.52.0/http/file_server.ts
Download https://deno.land/std@0.52.0/http/file_server.ts
...
local: /Users/deno/Library/Caches/deno/deps/https/deno.land/5bd138988e9d20db1a436666628ffb3f7586934e0a2a9fe2a7b7bf4fb7f70b98
type: TypeScript
compiled: /Users/deno/Library/Caches/deno/gen/https/deno.land/std@0.52.0/http/file_server.ts.js
map: /Users/deno/Library/Caches/deno/gen/https/deno.land/std@0.52.0/http/file_server.ts.js.map
deps:
https://deno.land/std@0.52.0/http/file_server.ts
```

---

# Resources

[Deno.land](https://deno.land/)
[Introduction](https://deno.land/manual/introduction)
[std lib](https://deno.land/std/)

---

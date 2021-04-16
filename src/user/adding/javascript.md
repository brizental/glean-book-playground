# Adding Glean to your Javascript project

A Javascript implementation of Glean is provided by the [Glean.js]() project.

Currently, Glean.js has support only for web extensions. Support for websites, Node.js and
other Javascript environments is planned, but not currently available.

## Setting up the dependency

The Glean.js package is distributed as an npm package [`@mozilla/glean`](https://www.npmjs.com/package/@mozilla/glean).

Install Glean.js in your Javascript project, by running:

```bash
npm install @mozilla/glean
```

Then import Glean into your project like so:

```js
// Glean.js for webextensions
//
// esm
import Glean from "@mozilla/glean/webext";
// cjs
const { default: Glean } = require("@mozilla/glean/webext");
```

{{#include ../../../assets/info.html}}

### Common import errors

> #### "Cannot find module '@mozilla/glean'"
>
> Glean.js does not have a [`main`](https://nodejs.org/api/packages.> html#packages_main_entry_point_export)
> package entry point. Instead it relies on a series of entry points depending on the platform you > are
> targeting.
> 
> In order to import Glean use `import Glean from '@mozilla/glean/<your-platform>`.
> 
> #### "Module not found: Error: Can't resolve '@mozilla/glean/webext' in '...'"
> 
> Glean.js relies on Node.js' [subpath exports](https://nodejs.org/api/packages.> html#packages_subpath_exports)
> feature to define multiple package entry points.
> 
> Please make sure that you are using a supported Node.js runtime (>= v12.7.0) and also make sure
> the tools you are using support this Node.js feature.

## Setting up metrics and pings code generation

In Javascript, the metrics and pings definitions must be parsed at build time. The `@mozilla/glean`
package exposes [glean_parser]() through the `glean` script.

To parse your Glean YAML files using this script, define a new script in your `package.json` file:

```json
{
  ...
  "scripts": {
    ...
    "build:glean": "glean translate path/to/metrics.yaml path/to/pings.yaml -f javascript -o path/to/generated",
    // Or, if you are building for a Typescript project
    "build:glean": "glean translate path/to/metrics.yaml path/to/pings.yaml -f typescript -o path/to/generated"
  }
}
```

Then run this script by calling:

```
npm run build:glean
```

## Automation steps

### Documentation

One of the commands provided by glean_parser let's users generate Markdown documentation based
on the contents of their metrics and pings YAML files. To perform that translation, use the
[`translate`]() command with a different output format.

In your `package.json`, define the following script:

```json
{
  ...
  "scripts": {
    ...
    "docs:glean": "glean translate path/to/metrics.yaml path/to/pings.yaml -f markdown -o path/to/docs",
  }
}
```

Then run this script by calling:

```
npm run docs:glean
```

### YAML files linting

Glean includes a "linter" for `metrics.yaml` and `pings.yaml` files called the `glinter` that
catches a number of common mistakes in these files. To run the linter use the `glinter` command.

In your `package.json`, define the following script:

```json
{
  ...
  "scripts": {
    ...
    "lint:glean": "glean glinter path/to/metrics.yaml path/to/pings.yaml",
  }
}
```

Then run this script by calling:

```
npm run lint:glean
```

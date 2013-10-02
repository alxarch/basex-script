# basex-script [![Build Status](https://secure.travis-ci.org/alxarch/basex-script.png?branch=master)](http://travis-ci.org/alxarch/basex-script)

BaseX command scripts for nodejs

## Getting Started
Install the module with: `npm install basex-script`

```javascript
var basex-script = require('basex-script');
basex-script.awesome(); // "awesome"
```

## Documentation

A convenience object that generates `BaseX` [Command Scripts](http://docs.basex.org/wiki/Commands#Command_Scripts).

All `BaseXScript` methods except `BaseXScript.render()` are chainable.


### `script.command(name, input, params), script.command(name, params)`

`name`: the tagname of the command (`drop-db`)

Appends a command to the script.

All command name, input, and params are validated 
and relevant errors are thrown.

### `script.requires(module1, module2, ..., moduleN)`

Adds a `REPO INSTALL <file>` command for each argument.

### `script.bind(key, value), job.bind(bindings)`

Binds parameters for XQuery external variables.

These bindings are collected and *prepended* to the command script 
before all other commands upon rendering.

### `script.execute(command)`

Appends an `EXECUTE` command. 
If `command` can be a `BaseXScript` instance.

### `script.xquery(xquery)`

Appends an `XQUERY` command.

### `script.import(files, path, options), job.import(files), job.import(files, options)`

Imports files.

In order to specify parsing options for the files without affecting
global options, it appends an `EXECUTE` command that executes 
a child Command Script. Options that can be set are:

#### `options.db`

Specify the database to add files to. 
If not set the currently opened database will be used.
If no db is currently open or the specified database does not exist
the script will fail upon execution.

#### `options.{createfilter, addarchives, skipcorrupt, addraw, parser, parseropt, htmlopt}`

See [Parsing Options](http://docs.basex.org/wiki/Options#Parsing)

#### `options.{chop, intparse}`
See [Parsing Options](http://docs.basex.org/wiki/Options#XML_Parsing)


### `script.set(option, value), job.set(options)`

`option`: Option name to set.
`value`: Value to set the option to.

or 

`options`: Object of option/value pairs.

Appends single/multiple `SET` command.

### `script.export(path)`

Appends an `EXPORT <path>` command.

### `script.check(db)`

Appends an `CHECK <db>` command.

### `script.open(db)`

Appends an `OPEN <db>` command.

### `script.close()`

Appends a `CLOSE` command.

### `script.run(file)`

Appends a `RUN` command.

### `script.render()`

Renders the xml for this Command Script.

### `script.toString()`

Alias of `script.render()`

_(Coming soon)_

## Examples
_(Coming soon)_

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
_(Nothing yet)_

## License
Copyright (c) 2013 Alexandros Sigalas. Licensed under the MIT license.

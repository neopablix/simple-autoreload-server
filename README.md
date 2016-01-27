simple-autoreload-server [![Build Status](https://travis-ci.org/cytb/simple-autoreload-server.png?branch=master)](https://travis-ci.org/cytb/simple-autoreload-server)
========================

A simple Web server on Node.js with Live/Autoreload feature.
  - Reload statically on update the html files
  - Refresh dynamically on update the files like css, js, png, and etc.
  - No browser extensions are needed. (uses only WebSocket.)

Usage
----
  1. Install simple-autoreload-server via npm.
     (e.g. npm install simple-autoreload-server)

  2. Start autoreload-server from command line.
     (e.g. autoreload-server ./ 8080)

  3. Open server url with your browser.
     (e.g. iexplore http://localhost:8080/)

Command Line Usage
----
```sh
autoreload-server [options] [root-dir] [port]
```

Command Line Options
----

option | default | description
:--- | :--- | :---
`--root, -d <param>` | `.` | _set base directory to publish._
`--port, -p <param>` | `8080` | _set port to listen (http)._
`--list-directory, -l` | `true` | _enable directory listing._
`--browse, -b` | `false` | _open url of server by platform default program._
`--execute, -e <param>` |  | _execute command when the server has prepared._
`--stop-on-exit` | `false` | _exit when invoked process specified by '--execute' died._
`--watch, -w <param>` | `/^/` | _regex pattern for file to watch._
`--watch-delay <param>` | `1` | _delay the watch event to supress duplication (in ms)._
`--verbose, -v` | `false` | _enable verbose logging._
`--client-log` | `false` | _inform client to log._
`--recursive, -r` | `true` | _watch sub-directories recursively. (may take a while at startup)_
`--follow-symlink, -l` | `false` | _follow symbolic-link. (it affects only when the resursive option specified.)_
`--force-reload, -f <param>` |  | _regex pattern for file forced to reload the whole page._
`--broadcast-delay <param>` | `0` | _delay time before broadcasting event (in ms)._
`--no-default-script` | `false` | _disable default script injection._
`--inject-file, -I <param>` |  | _the file to be injected into content._
`--inject-method, -M <param>` | `p` | _specify the injection method [prepend or append]_
`--inject-match-text, -T <param>` |  | _specify the regex or string pattern for content where to inject_
`--inject-match-file, -F <param>` |  | _specify the regex pattern for file where to inject._
`--version, -V` |  | _show version_
`--help, -h` |  | _show help_



#### Example

```sh
autoreload-server -w "\\.(html|css|js)" ./site-files 8008
```

Module Usage (Example)
----
```
var launcher = require('simple-autoreload-server');

var server = launcher({
  port: 8008,
  root: './',
  listDirectory: true,
  watch: /\.(png|js|html|json|swf)$/i,
  forceReload: [/\.json$/i, "static.swf"]
});
```

#### Options

See 'src/lib/options.ls' for details of options.


Version
----
0.0.21-0

Installation
--------------
install this package via 'npm'.

```sh
npm install simple-autoreload-server
```

License
----
MIT

[simple-autoreload-server]:https://github.com/cytb/simple-autoreload-server


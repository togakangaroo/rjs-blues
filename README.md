I can't get the requirejs optimizer to work properly.

my web app has the following directories

* app
  * index.html - includes requirejs, main.js, then `require(['plugins'])`
  * scripts
    * main.js - bootstraps requirejs, sets baseUrl to /scripts
    * plugins.js - references and exposes modules from app-plugins. References via `../app-plugins/a.js`
  * app-plugins
    * a.js

everything works fine in the non-optimized version (run a webserver at app, open console and navigate to the index page). 

Optimizing, however, gives me an error because of the `../` in plugins.js. To see this cd to the optimization directory and run `node .\node_modules\requirejs\bin\r.js -o .\build.json`. The error will be

```
W:\temp\requireop\optimization [master]> .\Build-RequireJs.ps1

Tracing dependencies for: main

Tracing dependencies for: plugins
Error: ENOENT, no such file or directory 'W:\temp\requireop\build\app-plugins\a.js'
In module tree:
    plugins

Error: Error: ENOENT, no such file or directory 'W:\temp\requireop\build\app-plugins\a.js'
In module tree:
    plugins

    at Object.fs.openSync (fs.js:427:18)
```
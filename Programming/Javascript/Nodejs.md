# Handle error 
```
ERROR: npm v9.1.2 is known not to run on Node.js v10.19.0. You'll need to upgrade
to a newer Node.js version in order to use this version of npm. This version of
npm supports the following node versions: `^14.17.0 || ^16.13.0 || >=18.0.0`. You
can find the latest version at https://nodejs.org/.

ERROR:
/usr/local/lib/node_modules/npm/lib/utils/exit-handler.js:22
  const hasLoadedNpm = npm?.config.loaded
                           ^

SyntaxError: Unexpected token .
    at Module._compile (internal/modules/cjs/loader.js:723:23)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)
    at Module.require (internal/modules/cjs/loader.js:692:17)
    at require (internal/modules/cjs/helpers.js:25:18)
    at module.exports (/usr/local/lib/node_modules/npm/lib/cli.js:76:23)
    at Object.<anonymous> (/usr/local/lib/node_modules/npm/bin/npm-cli.js:2:25)
    at Module._compile (internal/modules/cjs/loader.js:778:30)
```

1. Install NVM
 + curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh
2. Download LTS
 + nvm install --lts
3. Use LTS 
 +  nvm use --lts


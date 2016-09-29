# Openshift Labs Node.JS

## Usage

`rhc create-app <app name> http://cartridgelabsnodejs-dzhao.itos.redhat.com/manifest/de6ed8eb3d709932b69b79816c9f9e5e89795e95`

What this cartridge provides out of the box
---
1. **node.js** ([latest LTS](https://semver.io/node/resolve/4) currently 4.6.0)
2. **npm** (latest stable currently 2.15.9)
3. **grunt**
4. **bower**

What this cartridge does out of the box
---
*Not much.*

1. Installs node.js (version specified by `$OPENSHIFT_NODEJS_VERSION` and resolved by [semver.io](https://semver.io))
2. Installs grunt, bower, and forever globally (specified by `$OPENSHIFT_NPM_GLOBALS`)
3. Allows the user to manually install required dependencies (in a `build` [action_hook](http://openshift.github.io/documentation/oo_user_guide.html#action-hooks))
4. Runs `npm start` if `package.json` is found in repo directory (log is written to `$OPENSHIFT_NODEJS_LOG_DIR`)

How can I modify the cartridge
---

##### Use a different version of node
###### (using 0.11.13 as an example)

1. Run `rhc env set OPENSHIFT_NODEJS_CUSTOM_VERSION="0.11.13" -a <app name>`
2. Run `rhc cartridge reload http://cartridgelabsnodejs-dzhao.itos.redhat.com/manifest/de6ed8eb3d709932b69b79816c9f9e5e89795e95 -a <app name>`

***Heads up!***
The cartridge defaults to installing grunt, bower, and forever globally. Bower depends on node >=0.10.0. If you wish to use an older version of node set `$OPENSHIFT_NPM_CUSTOM_GLOBALS` to not include bower.

##### Install more npm packages globally
###### (using gulp and component as an example)

1. Run `rhc env set OPENSHIFT_NPM_CUSTOM_GLOBALS="gulp component" -a <app name>`
2. Run `rhc cartridge reload http://cartridgelabsnodejs-dzhao.itos.redhat.com/manifest/de6ed8eb3d709932b69b79816c9f9e5e89795e95 -a <app name>`

Thanks!
---
These repos helped out a ton while developing this cartridge.

1. [engineersamuel/openshift-origin-cartridge-nodejs](https://github.com/engineersamuel/openshift-origin-cartridge-nodejs)
2. [wshearn/openshift-origin-cartridge-nodejs](https://github.com/wshearn/openshift-origin-cartridge-nodejs)
3. [ramr/nodejs-custom-version-openshift](https://github.com/ramr/nodejs-custom-version-openshift)
4. [heroku/heroku-buildpack-nodejs](https://github.com/heroku/heroku-buildpack-nodejs)
5. [connyay/openshift-node-diy](https://github.com/connyay/openshift-node-diy)

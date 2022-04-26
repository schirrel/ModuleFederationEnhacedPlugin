# ModuleFederationEnhacedPlugin

Utility to extend Module Federation power.

It uses inheritance so it receive the same props of ModuleFederationPlugin and call it under the hoods.

# Install

```shell script
yarn @module-federation/ModuleFederationEnhacedPlugin -D
```

# Extended

### Extended to remoteEntry:
|   Prop    |                   Description                       |
| --------- | --------------------------------------------------- |
| moduleMap | list of all available modules from a single remote. |
| remoteMap | list of all remotes available for consumption       |
| remoteUrlMap | list of all remotes URL to initilize      |

### Other

|   Prop    |                   Description                       |
| --------- | --------------------------------------------------- |
| chunkMap.json | list of all chunkNames and create a json file on dist filder. |
# Usage

```js
const ModuleFederationEnhacedPlugin = require("@module-federation/ModuleFederationEnhacedPlugin");

module.export = {
  //... rest of your config
  plugins: [
    new ModuleFederationEnhacedPlugin({
      name: "myApp",
      library: { type: "var", name: "app2" },
      filename: "remoteEntry.js",
      remotes: {
        app1: "app1@myApp1.com/remoteEntry.js",
        app2: "app2@coolAppRunningOnCLoude.com.br/remoteEntry.js",
      },
      exposes: {
        Button: "./src/Button",
        Input: "./src/Input",
        /* Auto Generated:
            moduleMap: ['Button', 'Input'],
            remoteMap: ['app1', 'app2'],
            remoteUrlMap: [{app1: 'myApp1.com/remoteEntry.js' app2: 'coolAppRunningOnCLoude.com.br/remoteEntry.js'}]
          */
      },
    }),
  ],
};
```

Usage on component:

```js
import moduleMap from "myApp/moduleMap";
import remoteMap from "myApp/remoteMap";
import remoteUrlMap from "myApp/remoteUrlMap";
```

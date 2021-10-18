# node-example-helper

Library for implementing simple node.js-based interactive command line tools that use the Particle API

## Features

### Configuration file

The example node scripts have an optional configuration file, config.js, in the application directory. This is read by the main app using require. In most cases, this configuration is optional, or only requires the default values, and can prompt for things that are not specified in the file.

The prompting for configuration, for example which product to work with, is useful when running in Stackblitz.

### Settings file

The settings file, on the other hand, is a simple JSON file that's maintained by this helper for storing state temporarily. For example, you can enable storing a temporary authorization token in the settings.json file so you don't have to type it in every time you run the script. This is usually disabled by default, but is useful if you're writing your own script that you are going to be running a number of times.

### Interactive CLI (readline) helper

There are utilities for prompting for strings, passwords, numbers, yes/no answers, and simple menus.

### Particle authentication

A single function call, `helper.authenticate()`, takes care of prompting for username (email), password, and MFA token (if enabled). This is more secure than storing the authentication token in the config.js file, though that is also supported for use cases where it makes sense to do so.

### Other useful Particle API calls

While not intended to replace particle-api-js, there are some useful functions in the helper. For example, you can retrieve the entire product device list at once, instead of paginated. This library doesn't actually use particle-api-js, it uses axios directly, however you can still use particle-api-js from your own scripts, as the device move and device provisioning sample scripts do.

## Usage 

This library is intended for use in a node.js environment (not a browser). It has one external dependency, axios, for doing Particle REST API calls. It also uses the node libraries fs, path, and readline. It requires node v12 or later.

The sample scripts like DeviceProvisioning and DeviceMove use it like this:

```
const helper = require('@particle-iot/node-example-helper');
helper
    .withRootDir(__dirname)
    .withConfig(config);
```

Using the config file is optional. config is just an object that is read using require() in the main application.



## Version History

### 0.0.1 (2021-10-18)

- Initial version

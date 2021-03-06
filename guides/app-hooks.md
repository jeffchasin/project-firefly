
# Project Firefly application tooling lifecycle event hooks

Project Firefly applications created with [our CLI](https://github.com/adobe/aio-cli) are inherently npm packages.
This means they support many of the npm conveniences node developers expect.

package.json may include the following scripts which are triggered at various times while an app is being built, deployed and/or run.

## Sample hooks configuration

For example, pre and post hooks can be defined for the `run`, `build` and `deploy` operations in the package.json file of your app as follows:

```
  "scripts": {
    "pre-app-run": "echo pre-app-run",
    "post-app-run": "echo post-app-run",
    "pre-app-build": "echo pre-app-build",
    "post-app-build": "echo post-app-build",
    "pre-app-deploy": "echo pre-app-deploy",
    "post-app-deploy": "echo post-app-deploy"
  }
  ```

## Sample hooks flow

The following diagram illustrates how your custom hooks will be executed within the application build and deploy operations which are triggered from the `aio app deploy` command:

![aio-app-deploy lifecycle](../images/aio-app-deploy.png)

# NPM script hooks

Use of Project Firefly event hooks does not interfere with use of npm scripts, however you will need to use `npm run ..` to trigger them.
The only _default_ script that Firefly tooling calls is `test`
`aio app test -> npm test`, and in turn, npm calls `pretest` and `posttest` around your actual test script.

[How npm handles the "scripts" field](https://docs.npmjs.com/misc/scripts)

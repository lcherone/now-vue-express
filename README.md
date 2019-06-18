# Express API with a Vue Static Frontend on ZEIT Now

This example shows a pre-setup project including:

- An `api` directory, containing a single endpoint that retrieves the current time with Express built with the [@now/node Builder](https://zeit.co/docs/v2/deployments/official-builders/node-js-now-node/).
- A `dist` directory, containing the static built Vue project files.
- A `src` directory, containing the Vue project source files.
- `.env` files ready.


#### Local Development

Using Now CLI, you can use the following command from your terminal to start a development environment locally which replicates the production environment on Now so you can test your new project:

```bash
now dev
```

#### Deploying

Using [Now CLI](https://zeit.co/download), you can also deploy to both [staging](https://zeit.co/docs/v2/domains-and-aliases/aliasing-a-deployment#staging) and [production](https://zeit.co/docs/v2/domains-and-aliases/aliasing-a-deployment#production) environments from your terminal.

For a staging deployment, you can use the following one-word command:

```bash
now
```

Then, for production, including automatic aliasing, you can use the following:

```bash
now --target production
```

For more information on deploying, see the [Deployment Basics documentation](https://zeit.co/docs/v2/deployments/basics#introducing-a-build-step).

## Configuration Breakdown

This example contains a `now.json` file which instructs Now how to treat this project when developing locally and deploying.

```json
{
    "version": 2,
    "name": "now-vue-express",
    "builds": [
        { "src": "api/**/*.js", "use": "@now/node" },
        { "src": "package.json", "use": "@now/static-build" }
    ],
    "routes": [
        { "src": "/service-worker.js", "headers": { "cache-control": "s-maxage=0" } },
        { "handle": "filesystem" },
        { "src": "/", "dest": "dist/index.html" }
    ]
}
```

The above instructs Now with:

- The [`version` property](https://zeit.co/docs/v2/deployments/configuration#version), specifying the latest Now 2.0 Platform version.
- The [`name` property](https://zeit.co/docs/v2/deployments/configuration#name), setting the name for the deployment.
- The [`builds` property](https://zeit.co/docs/v2/deployments/configuration#builds), allowing Now to use [the @now/node Builder](https://zeit.co/docs/v2/deployments/official-builders/node-js-now-node/) with a specific source target for the /api routes and [the @now/static-build Builder](https://zeit.co/docs/v2/deployments/official-builders/static-now-static/) to run the now-build comand in the `package.json`, which will then build the Vue project. 
- The [`routes` property](https://zeit.co/docs/v2/deployments/configuration#routes), instructing Now to route the user to the `dist/index.html` file when requesting the root path `dist` directory and API lambda's.

For more information on configuring Now, see the [Configuration documentation](https://zeit.co/docs/v2/deployments/configuration).

## Resources

Learn more about the ZEIT Now platform from [our documentation](https://zeit.co/docs), including:

- [More information on deploying Express projects](https://zeit.co/docs/v2/deployments/official-builders/node-js-now-node/) and some technical details.
- [More information on the platform itself](https://zeit.co/docs), including [domains and aliasing](https://zeit.co/docs/v2/domains-and-aliases/introduction/) and [local development](https://zeit.co/docs/v2/development/basics/).

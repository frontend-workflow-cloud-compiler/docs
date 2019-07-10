# Server

The node server provides the endpoints for compiling the data like css, js and svg.

Github: [unglue-workflow/server](https://github.com/unglue-workflow/server)

## Install

`yarn add unglue-server`

## Start

### Node package

`yarn --cwd node_modules/unglue-server/ run start`

*If you want to, you can add following code to your package.json to shorten the command to `yarn start`:*

```
"scripts": {
    "start": "yarn --cwd node_modules/unglue-server/ run start"
}
```

## Connect client to custom server

By default the client connects to the EC2 server instance.  
Use the `--server=localhost:3000` client option to connect to your custom server ([#connect-to-another-server](https://unglue-docs.readthedocs.io/en/latest/client/#connect-to-another-server)).

## API

**/compile/css:** Compiles given scss and css code and transforms the code based on the given options. By default it transforms scss to css, applies autoprefixer and minifies the code with cssnano.

**/compile/js:** Compiles ES6 to ES5 code with babel and compresses es5 code with uglifyjs. The plugins can be turned on / off in the options.

**/compile/svg-sprite:** Combines multiple svg files into one svg "sprite" to be used with symbols. See [css-tricks.com](https://css-tricks.com/svg-symbol-good-choice-icons/#article-header-id-1) for more information on how to use svg symbols.

> You can find the full API Definition on [SwaggerHub](https://app.swaggerhub.com/apis-docs/TheMaaarc/Unglue/1.1.1). Make sure to hit "Try it out" to see all the parameters and options that are available.

## Options

Some options like sourcemap or distFile options will be overwritten by the server.

**CSS**

| Plugin | Available options |
|---|---|
| autoprefixer | [autoprefixer options](https://github.com/postcss/autoprefixer#options) |
| cssnano | [cssnano presets](https://cssnano.co/guides/presets) |

> You can find an example request on [SwaggerHub](https://app.swaggerhub.com/apis-docs/TheMaaarc/Unglue/1.1.1#/API%20Calls/get_css).

**JS**

| Plugin | Available options |
|---|---|
| babel | [babel options](https://babeljs.io/docs/en/options) |
| uglifyjs | [uglifyjs options](https://github.com/mishoo/UglifyJS2#minify-options) |

> You can find an example request on [SwaggerHub](https://app.swaggerhub.com/apis-docs/TheMaaarc/Unglue/1.1.1#/API%20Calls/get_js).

**SVG-Sprite**

| Plugin | Available options |
|---|---|
| svgstore | [svgstore options](https://github.com/svgstore/svgstore#options) |

> You can find an example request on [SwaggerHub](https://app.swaggerhub.com/apis-docs/TheMaaarc/Unglue/1.1.1#/API%20Calls/get_svg_sprite).

## Run as dockerized image

Run the docker image. Map port 3000 to local port 3000.

`docker run -d -p 3000:3000 unglue/server`

You should now be able to access `https://localhost:3000`.

## Install with GIT

1. Clone the git repository.  
   `git clone https://github.com/unglue-workflow/server.git unglue-server/`

2. Install dependencies  
   `yarn install`

3. Start the server  
   `yarn start`

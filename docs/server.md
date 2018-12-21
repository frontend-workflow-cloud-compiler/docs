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

## Endpoints

### `/compile/css`

Compiles the given scss files and runs autoprefixer. Can be compressed, sourcemaps can be generated.

**Parameters:**

| Name | Type | Description |
|---|---|---|
| distFile* | string | Name of the dist file, used for generating the correct sourcemap links. |
| mainFiles* | string | Name and path of all files that shall be combined into one css string. Can include css or scss files. It's important that the given css/scss files are sent with code and the same file path as given in `files`. |
| files* | array | Array of all files `[{"file": "path/file.scss", "code": "code"}]`.
| options | object | Optional. Object with options for compilation. Default: `{"compress": true, "maps": false}` |

Example payload:

> The unglue file is in `/var/www/dist/`.  
> 
> The mainFiles will be concatenated in the order given. If enabled, sourcemaps will be generated.

```json
{
    "distFile": "main.css",
	"mainFiles": [
		"/var/www/src/css/lib.css",
		"/var/www/src/scss/main.scss"
	],
	"files": [
		{
			"file": "/var/www/src/css/lib.css",
			"relative": "../src/css/lib.css",
			"code": "..."
		},
		{
			"file": "/var/www/src/scss/main.scss",
			"relative": "../src/scss/main.scss",
			"code": "..."
		}
	]
}
```

**Result:**

Returns the following object:

```json
{
	"code": "...compiled code..."
}
```

> If enabled the sourcemap will be embeded into the code.


### `/compile/js`

Combines given js files into one file. Can be compressed, can generate sourcemaps. The task will also compile ES6 to ES5 code through the babel transpiler.

**Parameters:**

| Name | Type | Description |
|---|---|---|
| distFile* | string | Name of the dist file, used for generating the correct sourcemap links. |
| files* | array | Array of files `[{"file": "path/file.js", "code": "code"}]`.
| options | object | Optional. Object with options for compilation. Default: `{"compress": true, "maps": false}` |

**Result:**

Returns the following object:

```json
{
	"code": "...compiled code..."
}
```

> If enabled the sourcemap will be embeded into the code.

### `/compile/svg-sprite`

Combines given SVGs to a single SVG string with symbols. Can than be `use`d on the website.

> See [css-tricks.com](https://css-tricks.com/svg-use-with-external-reference-take-2/) for more informations.

**Parameters:**

| Name | Type | Description |
|---|---|---|
| files* | array | Array of files `[{"file": "path/file.svg", "code": "code"}]`.

**Result:**

Returns the following object:

```json
{
	"code": "...svg sprite with each provided svg as symbol...",
}
```

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
	`yarn start`2
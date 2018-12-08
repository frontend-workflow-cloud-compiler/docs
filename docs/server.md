# Server

The node server provides the endpoints for compiling the data like css, js and svg.

Github: [unglue-workflow/server](https://github.com/unglue-workflow/server)

## Install

### Node package

`yarn add unglue-server`

### Git

Clone the git repository and install the dependencies.

```
git clone https://github.com/unglue-workflow/server.git unglue-server/
yarn install
```

## Start

### Node package

`yarn --cwd node_modules/unglue-server/ run start`

*If you want to, you can add following code to your package.json to shorten the command to yarn start:*

```
"scripts": {
    "start": "yarn --cwd node_modules/unglue-server/ run start"
}
```

### Git

`yarn start`

## Endpoints

### `/compile/css`

Compiles the given scss files and runs autoprefixer. Can be compressed, sourcemaps can be generated.

**Parameters:**

| Name | Type | Description |
|---|---|---|
| distFile* | string | Name of the dist file, used for generating the correct sourcemap links. |
| mainFile* | string | Name and path of the main `.scss` file. Used for the sass compiler as entry point. |
| files* | array | Array of files `[{"file": "path/file.scss", "code": "code"}]`.
| options | object | Optional. Object with options for compilation. Default: `{"compress": true, "maps": false}` |

**Result:**

Returns the following object:

```json
{
	"code": "...compiled code...",
	"map": "sourcemap for code or false if options.maps false"
}
```

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
	"code": "...compiled code...",
	"map": "sourcemap for code or false if options.maps false"
}
```

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


## Build custom server

## Connect client to custom server

## Run as dockerized image
# Client

> **Please take a look at the [getting started section](start.md) for basic setup guide.**

The Unglue client is responsible for reading the `.unglue` files which defines the config, find all associated files (css, js) collect the values and transmit those informatiosn to the [Server](server.md). The response from the server will then be stored in the designated files.

## Download

The client [client binary](https://github.com/unglue-workflow/client) must be installed trough composer.

```sh
composer require --dev unglue/client
```

Afterwards the bin file is available in `vendor/bin/unglue`.

## Unglue config file

The `.unglue` files are the place where the magic happens. Depending on the file name (e.g `main.unglue`) this is what your output will look like (e.g. `main.css` and/or `main.js`). The unglue files must be stored as valid json, and currently contains the following sections:

+ css: An array with valid paths to scss files.
+ js: An array with valid paths to javascript files which should be compiled.
+ svg: An array with paths to svg which should be collected and returned as single svg sprite file.
+ options: Options for the compiling request, see the configuration option section for more details.

And example of an anglue file which will read a main.scss file and collect and compile a few javascript files. Also options like compress (uglify) and maps (source maps) are enabled:

```json
{
    "css": [
        "../../src/scss/main.scss"
    ],
    "js": [
        "js/jquery.js",
        "js/app.js",
        "js/datepicker.js"
    ],
    "options": {
        "compress" : true,
        "maps" : true
    }
}
```

## SVG-Sprites

In order to generate an svg sprite from several svg sources you can use the `svg` key inside an unglue file:

```json
{
    "svg": [
        "icon.svg",
        "another.svg",
        "johndoe.svg"
    ]
}
```

This will create an svg file with the same name as the unglue file has.

## Options

```json
    "options": {
        "compress" : true,
        "maps" : true
    }
```

|name|type|description
|----|----|-----------
|compress|boolean|compress css and js
|maps|boolean|generate maps file for css and js

## Use another Server

Run the `watch` or `compile` commands with argument `--server=localhost:3000` in order to connect to anyother server. By default you will connect to the cloud compile server of the unglue project.

## Arguments

Arguments can be added to the commands like `--server=localhost:3000` or `--timeout=20000`:

|options|description|watch|compile
|-------|-----------|-----|-------
|`--server`|Define a server to connect|☑|☑
|`--timeout`|The timeout in miliseconds between a next watch iteration is triggered.|☑|☐

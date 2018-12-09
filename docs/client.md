# Client

Please take a look at the [getting started section](start.md) for basic setup guide.

## How to install

The client [client binary](https://github.com/unglue-workflow/client) must be installed trough composer in the vendor folder.

```sh
composer require --dev unglue-workflow/client
```

## The `.unglue` file

Add the `.unglue` files, for example `main.unglue`:

```json
{
    "css" : [
        "../../src/scss/main.scss"
    ],
    "js" : [
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

## configuration option

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

## connect to another server

Run with `--server=localhost:3000`.

## Arguments

|options|description|watch|compile
|-------|-----------|-----|-------
|--server|Define a server to connect|☑|☑
|--timeout|The timeout in miliseconds between a next watch iteration is triggered.|☑|☐

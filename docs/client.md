# Client

The client https://github.com/unglue-workflow/client.

## How to install

[start.md]

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

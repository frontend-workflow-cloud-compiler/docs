# How to use

Easy as 1,2,3:

1. Add client binary to vendor `composer require --dev unglue/client`
2. Create unglue file e.g `main.unglue` with content
```json
{
    "css" : [
        "scss/app.scss"
    ],
    "js" : [
        "js/app.js"
    ]
}
```
3. Run watch command `./vendor/bin/unglue watch`

## Get started

```sh
composer require --dev unglue/client
```

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


Run inside current directory and all sub directories:

```sh
./vendor/bin/unglue watch
```

Listen inside a certain folder:

```sh
./vendor/bin/unglue watch resources/
````

Run only once

```sh
./vendor/bin/unglue compile
```

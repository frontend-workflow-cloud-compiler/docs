# How to use

Easy as 1,2,3:

1. Add client binary to vendor `composer require --dev unglue/client`
2. Create unglue file e.g `main.unglue` with content js and css definition as json.
3. Run watch command `./vendor/bin/unglue watch`

## Setup

Add the `unglue/client` to the composer.json, preferred in the `require-dev` section:

```sh
composer require --dev unglue/client
```

Create the `.unglue` files inside your project, for example `main.unglue`:

```json
{
    "css" : [
        "path/to/scss/main.scss"
    ],
    "js" : [
        "paht/to/js/app.js"
    ]
}
```

At least one definition is mandatory, whether its `js` or `css` oterhwise the unglue client will throw an exception.

## Run 

As the setup is complet, you can now run the binary file to compile the files defined in the unglue config file. In general its recommend to run the `watch` command which will compile the files on startup and watch for changes afterwards and compile again if they have changed.

```sh
./vendor/bin/unglue watch
```

If there are large projects or not all folders of the project should be watched you can add a folder as second argument, this works for `watch` and `compile` commands:

```sh
./vendor/bin/unglue watch resources/
```

Only compile all files once:

```sh
./vendor/bin/unglue compile
```

[Read more about client configurations and details](client.md)

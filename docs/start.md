# Getting started

1. Add [client](client.md) binary to vendor `composer require --dev unglue/client`
2. Create unglue file e.g `main.unglue` with content js and css definition as json.
3. Run watch command `./vendor/bin/unglue watch`

## Setup

Add the [unglue/client](https://packagist.org/packages/unglue/client) composer package to the composer.json, preferred in the `require-dev` section:

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
        "path/to/js/app.js"
    ]
}
```

At least one definition is mandatory, whether it's `js` or `css`. Oterhwise the unglue client will throw an exception.

## Run 

Run the binary file (`./vendor/bin/unglue`) to compile the files defined in the previously created unglue config files. In general it's recommend to run the `watch` command which will compile the files on startup and watch for changes afterwards.

```sh
./vendor/bin/unglue watch
```

If you use unglue in a large project, a project with unglue files in the vendor or scss files in an asset folder, you might not want to compile everything. In that case you can define the path that has to be compiled/watched as a second argument (all subdirectories will be included).

```sh
./vendor/bin/unglue watch resources/
```

Only compile all files once in the resources folder:

```sh
./vendor/bin/unglue compile resources/
```

[Read more about client configurations and details](client.md)

## Using the client with a local server

By default, the client connects to [v1.api.unglue.io](https://v1.api.unglue.io). If you have a bad internet connection or you don't want to send your files to our server (we don't record/save any data), you can setup the unglue server by following the *Install* and *Start* instructions in [the server documentation](server.md).

After successfull setup of you own server you have to run the unglue client with the parameter `--server=<domain>:<port>` where domain and port is the address of your local server instance.

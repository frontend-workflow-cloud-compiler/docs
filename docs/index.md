# Unglue

Frontend workflow done different.

## Purpose

Forget the hassle of installing Node on your local system just to compile some scss files and minify/uglify js code. A composer package which is seamless installed along with other depencies does all the job.

## Idea

An abstraction of the "collecting the data" and "process and compiling" tasks. A client binary collecting all the required content from scss, css and js files and sends everything to the server which compiles and returns the code. This allows you to either use cloud based compiling (default) or served trough local unglue server setup.

## Technology

The [client](client.md) is a composer package distributed over packagist.org, it's written in PHP with [LUYA](https://luya.io) and [Yii Framework](https://yiiframework.com). The [server](server.md) is written in node requiring extension like autoprefixer, node-sass, babeljs. The latest version of the server is used to serve the cloud compile API v1.api.unglue.io which your client will connect by default. A docker image allows you to either use the server locally trough docker or using node (distributed trough npm).

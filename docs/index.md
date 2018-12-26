# Unglue

Frontend workflow done different.

## Purpose

Forget the hassle of installing Node on your local system just to compile some code scss files and minify/uglify js code. A composer package which is seamless installed along with other depencies does all the job. 

## Idea

An abstraction of the "collecting the data" and "process and compiling" tasks. A client binary collecting all the required content from scss, css and js files and sends everything to the server which compiles and returns the code. This allows you to either use cloud based compiling (default) or served trough local server.

## Technology

Client binary is provided trough vendor folder installed via composer. Server provides an API with endpoints to compile css and js.

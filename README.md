# Heroku Buildpack for Flutter

## Introduction

Automate your deployments on Heroku easily.

It is inspired by this [buildpack](https://github.com/diezep/heroku-buildpack-flutter) by [diezep](https://github.com/diezep). Originally a fork to fix a bug, it is now a more lightweight version without relying on a forked version of `dhttpd`.

## Setup

To add this buildpack to your Flutter Web App hosted on Heroku, copy the [link](https://github.com/MMZK1526/flutter-heroku-buildpack) of this repository and paste it in buildpacks.

## Why making one more buildpack?

The original buildpack was using a forked version of `dhttpd` to serve the files. Because of that, it has been out of date for a while, and it no longer works with the latest version of Dart.

The reason for the (original) fork is to make the server look for the `$PORT` environment variable, which is provided by Heroku on deployment. It is avoided in this buildpack by using the `--port` flag of `dhttpd` and pass in the `$PORT` environment variable. In this way, it should work with future versions of `dhttpd`.

Since then, I silenced a few warnings, removed some configurations to make it more lightweight (and less versatile, but it meets my needs anyway), and added a (very simple!) check to determine if the project is indeed a Flutter Web App.

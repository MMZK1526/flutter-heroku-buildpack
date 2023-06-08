# Heroku Buildpack for Flutter

## Introduction

A Buildpack that enables the deployment of Flutter Web Apps on Heroku.

It is inspired by this [Buildpack](https://github.com/diezep/heroku-buildpack-flutter) by [diezep](https://github.com/diezep). Originally a fork to fix a bug, it is now a more lightweight version without relying on a forked version of `dhttpd`.

## Setup

To add this Buildpack to your Flutter Web App hosted on Heroku, simply copy the [link](https://github.com/MMZK1526/flutter-heroku-buildpack) of this repository and paste it in Buildpacks. Alternatively, you can enter the Buildpack URL `mmzk1526/flutter`.

## Why making one more Buildpack?

The original Buildpack was using a forked version of `dhttpd` to serve the files. Because of that, it has been out of date for a while, and it no longer works with the latest version of Dart.

The reason for the (original) fork is to make the server look for the `$PORT` environment variable, which is provided by Heroku on deployment. It is avoided in this Buildpack by using the `--port` flag of `dhttpd` and pass in the `$PORT` environment variable. In this way, it should work with future versions of `dhttpd`.

Since then, I silenced a few warnings, removed some configurations to make it more lightweight (and less versatile, but it meets my needs anyway), and added a (very simple!) check to determine if the project is indeed a Flutter Web App.

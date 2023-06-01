---
title: "WAILS"
date: 2023-05-29T18:31:10-04:00
draft: false
---

{{< lead >}}

## Overview

A tool for running cross platform applications using Go and JS

{{< /lead >}}


## Wails Features

* Native Menus, Dialogs, Theming and Translucency
* Windows, macOS and linux support
* Built in templates for Svelte, React, Preact, Vue, Lit and Vanilla JS
* Easily call Go methods from JavaScript
* Automatic Go struct to TypeScript model generation
* No CGO or external DLLs required on Windows
* Live development mode using the power of Vite
* Powerful CLI to easily Create, Build and Package applications
* A rich runtime library
* Applications built with Wails are Apple & Microsoft Store compliant

## Feature Notes

## Quick Start Templates

Wails comes with a number of pre-configured templates that allow you to get your application up and running quickly. There are templates for the following frameworks: Svelte, React, Vue, Preact, Lit and Vanilla. There are both JavaScript and TypeScript versions for each template.
Native Elements

## Lib

Wails uses a purpose built library for handling native elements such as Window, Menus, Dialogs, etc, so you can build good-looking, feature rich desktop applications.

It does not embed a browser, so it is resource efficient. Instead, it uses the native rendering engine for the platform. On Windows, this is the new Microsoft Webview2 library, built on Chromium.
Go & JavaScript Interoperability

## Go & JS Interoperability

Wails automatically makes your Go methods available to JavaScript, so you can call them by name from your frontend! It even generates TypeScript models for the structs used by your Go methods, so you can pass the same data structures between Go and JavaScript.
Runtime Library

Wails provides a runtime library, for both Go and JavaScript, that handles a lot of the things modern applications need, like Eventing, Logging, Dialogs, etc.
Live Development Experience
Automatic Rebuilds

## Dev mode
When you run your application in "dev" mode, Wails will build your application as a native desktop application, but will read your assets from disk. It will detect any changes to your Go code and automatically rebuild and relaunch your application.
Automatic Reloads

When changes to your application assets are detected, your running application will "reload", reflecting your changes almost immediately.
Develop your application in a Browser

## Debug

If you prefer to debug and develop in a browser then Wails has you covered. The running application also has a webserver that will run your application in any browser that connects to it. It will even refresh when your assets change on disk.
Production-ready Native Binaries

## Single EXE

When you're ready to do the final build of your application, the CLI will compile it down to a single executable, with all the assets bundled into it. On Windows and MacOS, it is possible to create a native package for distribution. The assets used in packaging (icon, info.plist, manifest file, etc) are part of your project and may be customised, giving you total control over how your applications are built.
Tooling

## CLI

The Wails CLI provides a hassle-free way to generate, build and bundle your applications. It will do the heavy lifting of creating icons, compiling your application with optimal settings and delivering a distributable, production ready binary. Choose from a number of starter templates to get up and running quickly!
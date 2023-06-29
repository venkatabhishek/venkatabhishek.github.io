+++
title = "A Comparison of some Frontend Tooling/Build Tools"
date = "2023-05-07"
description = "Sample article showcasing basic Markdown syntax and formatting for HTML elements."
categories = [
    "frontend",
]
+++

## Background

In the olden days of web programming and Javascript, the code base was very simple

```
<html>
    <script src="/src/index.js"></script>
</html>
```

However, as technology progressed and libraries came about, the situation multiplied:

```
<html>
    <script src="/src/index1.js"></script>
    <script src="/src/index2.js"></script>
    <script src="/src/library1.js"></script>
    <script src="/src/library2.js"></script>
    ...
</html>
```

As the code base and dependencies scaled, **module bundlers** were introduced. The role of a module bundler is to combine your code base into a single file/module that can be imported:

```
<html>
    <script src="/src/bundle.js"></script>
</html>
```

This simplified the import process as well as enabled a more clear contract for modules. Tools like **Grunt** and **Gulp** were some of the first module bundlers introduced. However, there were still some drawbacks with these tools. Mainly, they were not able to figure out dependencies between modules and relied on external libraries like **require.js** to do so.

The most recent wave of bundlers such as **Webpack** introduced smart bundling by building a dependency graph for modules involved and building a single bundle accordingly.

## Comparison

The following is a comparison of some modern build tools that include module bundlers as their core technology:

### [Parcel](https://parceljs.org/)

Parcel is a relatively new build tool that advertises zero configration for many common setups.

In my personal exploration with the tool, I encountered a few hickups but otherwise encountered no major issues when trying to setup a new Express + React app and was able to do so in minutes. I also greatly appreciated that while no configuration is necessary, you can always choose to override/eject specific configs at any time (for example custom tsconfig, eslint, etc.)

In terms of performance, I found that the actual build time of an entire project was quite slow ranging up to 1-2 minutes for even a very small project. However, the live-reload/hot-module-replacement provided by the dev server was extremely quick and happened in the matter of seconds. (NOTE: I had to use `CHOKIDAR_USEPOLLING=true` in order to enable live reloading of the app given my environment on WSL Ubuntu)

### [Vite](https://vitejs.dev/)

Vite is not quite as new, but offers impressive performance in the dev experience, utilizing esbuild for module bundling. In production, it uses the more robust Rollup module bundler. In terms of conveniance, Vite also provides a number of template presets to bootstrap projects in react, vue, etc. Vite targets both slow start and slow updates to deal with bundling thousands of modules in large scale projects

### [Webpack](https://webpack.js.org/)

Webpack is quite an old tool at this point, but still solves many existing problems with older module bundlers with its smart dependency graph. Compared to modern equivalents, webpack lacks in performance. Webpack is quite a mature project and offers many features now, but is most likely not the choice for build tool moving forward.

A few helpful articles I read about the subject:

- [https://www.linkedin.com/pulse/what-webpack-why-does-even-exist-2023-prasenjit-sutradhar](https://www.linkedin.com/pulse/what-webpack-why-does-even-exist-2023-prasenjit-sutradhar)
- [https://dev.to/underscorecode/javascript-bundlers-an-in-depth-comparative-is-webpack-still-the-best-bundler-in-2021-59jk](https://dev.to/underscorecode/javascript-bundlers-an-in-depth-comparative-is-webpack-still-the-best-bundler-in-2021-59jk)

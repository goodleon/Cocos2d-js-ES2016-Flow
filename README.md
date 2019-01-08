Cocos2d-js ES2016 Template(模板)
==============================

I am posting this modified HelloWorld Cocos2d-js project in hopes it saves(节约)
someone some time. Here are the modern JavaScript features I wanted to see in
my development environment:
我编撰这个修改后的HelloWorld Cocos2d-js项目，希望它能节约大家一些时间。
以下是我想在我的开发环境其中看到的现代的JavaScript特性
:

   * ES2015 Support(对ES2015的支持)
   * async/await from ES2016(异步函数async/await ES2016)
   * Optional static type analysis using FlowType(可选的 使用FlowType 静态类型分析)
   * Optional runtime type checking using FlowCheck(可选的使用FlowCheck 运行时类型检查)
   * Transpilation using Babel so that the above features will work on
     current ES5 browsers(利用babel使上述新特性得以在当前ES5的浏览器中实现)
   * Prebuilding a Cocos2d-js package with exactly the modules I needed; the
     runtime loading of individual JavaScript files is way, way too slow.
     (预构建一个Cocos2d-js包，包含我需要的模块; 单个JavaScript文件的运行时加载非常非常慢。)
   * Source map support for ease of development(支持易于开发的源映射)
   * WebPack to build a combined, obfuscated module when I am ready to release
     my game(当我准备发布时，WebPack将构建一个组合的、模糊的模块 我的游戏)

Supported Platforms(支持的平台)
--------------------------

Primarily tested on Windows under a Bash environment, but should 
work on Mac or Linux. Please let me know if any changes are needed
to support those platforms. I tried to make everything cross-platform,
but sometimes things can fall through the cracks.
主要在Windows的Bash环境下的上测试，但是应该这样做在Mac或Linux上工作。
如果需要更改，请告诉我支持这些平台。我试着让所有东西都跨平台，但有时事情会不了了之。

Set up requirements(建立需求)
---------------------

This template doesn't include the Cocos2d install itself. You'll need to download
and install Cocos2d-x from [here](http://cocos2d-x.org/download). Once it's installed,
you should run:
该模板不包括Cocos2d安装本身。您需要下载
并从[此处]安装Cocos2d-x (http://cocos2d.x.org/download)。一旦安装,你应该运行:


cocos new -d my_new_project -l js

This will create a my_new_project project folder that contains MyJSGame/frameworks. Move
the frameworks folder into the cocos2d_js_gulp_flow top level folder and delete the my_new_project
folder.
这将创建一个包含MyJSGame/frameworks的my_new_project项目文件夹。移动
将frameworks文件夹放入cocos2d_js_gulp_flow顶层文件夹中并删除my_new_project
文件夹中。


Then download the [Git LFS](https://git-lfs.github.com/) client and run (if you
haven't already):

```
git lfs install
```

Then install [NodeJS >= 4.x](https://nodejs.org/en/) for your platform. If you
already have an older version of Node and can't upgrade, then I recommend
installing a version of nvm, either the [original for Linux or Mac](https://github.com/creationix/nvm) or
[nvm-windows](https://github.com/coreybutler/nvm-windows) for Windows.

Then, clone the project. From the new project directory, run:

```
npm install -g bower gulp
npm install
bower install
```

Optionally, install [FlowType](http://flowtype.org) for your platform for static
type analysis. Available for Windows [here](https://www.ocamlpro.com/pub/ocpwin/flow-builds/).

Finally, copy the frameworks directory from a Cocos2d-x install into a "frameworks"
folder.

Building
----------

The first command you need to run is `gulp cocos2d`. This will build the
cocos2d package based on the modules you specify in src/projects.json. By default
it builds "cocos2d", which is almost everything.

After you've built cocos2d.js, just run:

```
gulp
```

...and you'll get a build in maindist. If you want to try it out, you can run:

```
gulp serve
```

...and it will create a temporary web server on localhost that you can point
your Chrome browser at. **Warning**: this won't work with Firefox, or at least
it doesn't work for me with Firefox. I'm running NoScript, which might be
causing the problem, but it seems there are XSS protections that prevent the
code from working with the WebPack dev server.

Finally, you can either run `flow check` or `gulp flow` to check your code
with FlowType static type analysis. If you're on Windows, for `gulp flow` to
work you need to set the environment variable FLOW_BIN to point to the path to 
the Windows flow binary, as described on the 
[gulp-flowtype](https://www.npmjs.com/package/gulp-flowtype) page. `flow check`
should work if you have the flow binary in your path.

About the Flow Declarations
----------------------------

I generated the Flow declarations from the Cocos2d-js documentation. I'm sure
there are still bugs in it, but it's more complete than any I found elsewhere.
It's also easy to update. Instructions on how to generate, plus all scripts,
are available
[in this branch of my fork of the Cocos2d-html repo](https://github.com/TimMensch/cocos2d-html5/tree/develop-tim).

Feedback
--------------
I hacked this repo together quickly, and would love to hear from anyone who
uses it. If you see problems with it, please submit them to the GitHub Issues.

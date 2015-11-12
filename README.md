## UMD

本项目为 JavaScript 模块正式地设计和实现了通用模块定义（Universal Module Definition, UMD）API。通用模块能用在任何地方——用在客户端，服务端或其它地方。

UMD 试图为当下最流行的模块加载器（如 RequireJS 等）提供兼容性。多数情况下它以 [AMD](https://github.com/amdjs/amdjs-api/wiki/AMD) 为基础，特别地兼容了 [CommonJS](http://wiki.commonjs.org/wiki/CommonJS)。

### 变体

#### 一般模块

* [amdWeb.js](https://github.com/umdjs/umd/blob/master/templates/amdWeb.js) -
  定义一个模块，用于 AMD 和浏览器全局变量。如果你想在使用 AMD 的同时导出一个全局变量—— 当加载的其它脚本仍需要那个全局变量时这很有用，则可以用
  [amdWebGlobal.js](https://github.com/umdjs/umd/blob/master/templates/amdWebGlobal.js)。

* [returnExports.js](https://github.com/umdjs/umd/blob/master/templates/returnExports.js) -
  定义一个模块，用于 Node、 AMD 和浏览器全局变量。如果你想在使用 AMD 的同时导出一个全局变量——当加载的其它脚本仍需要那个全局变量时这很有用，则可以用
  [returnExportsGlobal.js](https://github.com/umdjs/umd/blob/master/templates/returnExportsGlobal.js)。

* [commonjsStrict.js](https://github.com/umdjs/umd/blob/master/templates/commonjsStrict.js) -
  定义一个模块，用于 CommonJS 运行时，并且模块可以循环依赖。如果你想在使用 AMD 的同时导出一个全局变量——当加载的其它脚本仍需要那个全局变量时这很有用，则可以用
  [commonjsStrictGlobal.js](https://github.com/umdjs/umd/blob/master/templates/commonjsStrictGlobal.js)

#### jQuery 插件

* [jqueryPlugin.js](https://github.com/umdjs/umd/blob/master/templates/jqueryPlugin.js) -
  定义一个 jQuery 插件，用于 AMD 和浏览器全局变量。

#### 有简单 Node/CommonJS 适配器的 AMD

用于这种情况：模块使用 AMD 风格，但是用在 Node 中并且通过 NPM 安装，不需要其它依赖来建立 AMD API。

此方案不允许使用 [AMD 加载器插件](https://github.com/amdjs/amdjs-api/wiki/Loader-Plugins)，只支持基础的 JavaScript 模块依赖。它也不支持 AMD 的 [callback-style require](https://github.com/amdjs/amdjs-api/wiki/require)。

* [nodeAdapter.js](https://github.com/umdjs/umd/blob/master/templates/nodeAdapter.js) -
  这种情况的最好选择：使用 AMD 风格，但是想让它用在 Node 中又不必借助其它库建立 AMD。
* [commonjsAdapter.js](https://github.com/umdjs/umd/blob/master/templates/commonjsAdapter.js) -
  类似于 nodeAdapter.js，不过兼容更多的 CommonJS 运行时，并且支持循环依赖。

### 工具

#### 构建工具

* [docpad-plugin-umd](https://github.com/docpad/docpad-plugin-umd) 是一个 [DocPad](http://docpad.org) 插件，使用 UMD 模板包装 JavaScript 代码。
* [grunt-umd](https://github.com/alexlawrence/grunt-umd) 是一个 [Grunt](http://gruntjs.com) 任务，使用 UMD 模板包装 JavaScript 代码。
* [gulp-umd](https://github.com/eduardolundgren/gulp-umd) 是一个 [Gulp](http://gulpjs.com/) 任务，使用 UMD 模板包装 JavaScript 代码。
* [grunt-urequire](https://github.com/aearly/grunt-urequire) 是 [uRequire](https://github.com/anodynos/uRequire) 的 Grunt 包装，是创建 UMD 的便利工具。
* [generator-umd](https://github.com/ruyadorno/generator-umd) 是一个 Yeoman 生成器，使用 UMD 模板创建一个单模块项目。


#### 测试工具

* [用 grunt-contrib-jasmine 对 UMD 单元测试](http://stackoverflow.com/questions/16940548/grunt-test-for-umd)

### 资料

* [Browserify 和 UMD](http://dontkry.com/posts/code/browserify-and-the-universal-module-definition.html)

### 待办事项

* noConflict。尽管有 AMD 加载器和构建工具，也应当可以获取指定版本，可能显示一个有 noConflict 选项的版本。
* 变体能添加一些功能到 $ 上。尽管此时往往要依赖于 'jquery'，但是如果开发者想使用其它模块，而不是真实的 'jquery'，可以将此模块文件映射到 'jquery' 名字上。这是模块名字的一个优势，它们可以映射到不同的实现上。
* 用法示例
    * 深入说明用法
    * 我们知道的问题和调整，但是不会放进 UMD 默认的模板

### 影响来源

本项目的 UMD 的基础模式派生自 [@kriskowal](https://github.com/kriskowal) 用在 [Q promise](https://github.com/kriskowal/q) 中的方案。

也受到早期 UMD 变体的影响，从 Kit-Cambridge 的 [UMD](https://gist.github.com/1251221) 到 Addy Osmani, Thomas Davis, Ryan Florence 讨论的[模式](https://github.com/addyosmani/jquery-plugin-patterns/issues/1)，到最近 [James Burke](https://gist.github.com/1262861) 的 UMD。

### 许可

版权归 UMD 贡献者所有。

以 [MIT 许可证](https://github.com/umdjs/umd/blob/master/LICENSE.md) 发布。

[本文](https://github.com/umdjs/umd#readme) 由 [Ivan Yan](http://yanxyz.net/) 翻译，["署名-非商用-相同方式共享"](http://creativecommons.org/licenses/by-nc-sa/4.0/)，意见[反馈](https://github.com/hongfanqie/umd/issues)。

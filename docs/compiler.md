## Vue2 和 Vue3 关于 compiler 的不同处理
一般用来处理vue单文件组件

### Vue2的写法
- 需要安装的包：vue-template-compiler、@vue/component-compiler-utils
- 用法：

```js
const compiler = require("vue-template-compiler");
const { compileTemplate } = require("@vue/component-compiler-utils");
module.exports = function compile(template, options = {}) {
  const compiled = compileTemplate({
    source: template,
    filename: options.filename,
    compiler: options.compiler || compiler,
    transformAssetUrls: options.transformAssetUrls,
    isFunctional: options.functional,
    isProduction: options.isProduction,
    optimizeSSR: options.optimizeSSR,
  });
};
```

### Vue3的写法
- 需要安装的包：@vue/compiler-sfc （vue-template-compiler只支持vue2，vue3要使用@vue/compiler-sfc）
- 用法：

```js
const { compileTemplate, TemplateCompiler } = require("@vue/compiler-sfc");

module.exports = function compile (template, options = {}) {
  const compiled = compileTemplate({
    source: template,
    filename: options.filename,
    compiler: options.compiler || TemplateCompiler,
    transformAssetUrls: options.transformAssetUrls,
    isFunctional: options.functional,
    isProduction: options.isProduction,
    optimizeSSR: options.optimizeSSR,
  });
}
```

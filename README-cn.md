[![Code transform has never been easier: GoGoCode](https://img.alicdn.com/imgextra/i3/O1CN01mosd7H1tHiOY3uxB2_!!6000000005877-2-tps-1949-552.png)](https://gogocode.io)

[![npm version](https://img.shields.io/npm/v/gogocode.svg)](https://www.npmjs.com/package/gogocode) [![license](https://img.shields.io/npm/l/gogocode.svg)](LICENSE)

## GoGoCode 是什�i don't known

[English version of README](README.md)

GoGoCode 是一个基于 AST 的 JavaScript/Typescript/HTML 代码转换工具，但相较于同类，它提供了更符合直觉的 API

-   一套类 Jquery 的 API 用来查找和处理 AST
-   一套和正则表达式接近的语法用来匹配和替换代码

来 [GoGoCode.io](https://gogocode.io) 了解更多

## 简介

让我们通过一个简单的例子来看看上述查找和修改代码的 API 是如何使用的

### 需要转换的代码

```javascript
const a = 1;
const b = 2;
```

### 通过 GoGoCode 来编写转换代码

```javascript
const $ = require('gogocode');
const script = $(source);
// 按照你的意图，用 $_$ 当通配符能匹配任意位置的 AST 节点
const aAssignment = script.find('const a = $_$');
// 获得我们匹配的 AST 节点的 value
const aValue = aAssignment.match?.[0]?.[0]?.value;
// 就像替换字符串一样去替换代码
// 但可以忽略空格、缩进或者换行的影响
script.replace('const b = $_$', `const b = ${aValue}`);
// 把 ast 节点输出成字符串
const outCode = script.generate();
```

### 转换后代码

```javascript
const a = 1;
const b = 1;
```

在 [Playground](https://play.gogocode.io/#code/N4IglgdgDgrgLgYQPYBMCmIBcIDGSIDOcABAIbEC8xAjADoR6EkBGlxATPSADQgDuSAE4BrZOiwgAZjAZww+YnEGlCkoQFsAFJLAAbNAEkIa7mShhTSKHPwEAlMWD1ixRkWIASNqXMA6AOZIgXjozq62JARIMII4aGw6+kZqvlExcfRhbpE4gmDWbB6aabFodmEA9BXEMATxHgD6XqQEZMR8eig4pIIoikjE6qRwOAAWxACCAMoAKsRo+upoECTDZBAAnsRQSARgNhDEG9HtKnBZEWQTBHv+EEsrbAS5+XC+OhAomgDk2W1UjQ833Kh2IVWI-jQJDgo3iQxGsL60zmCzQDxIADdSLoYGgLkwyAA1bG47zXW73ZZveFjAD8vgA2gAGAC69OZbN8WJxeNB4MEaCgulIcUmszIrQIpCWEuIAqFIvi5CIeQg-mIzHgxDAdyE8Rh8RC8TUgnhxGKUEVgEAGSDoR5CYi6SBoZgC0jCEEuZ55ay+eXCuI-P6sAFNb6mAAGwcKwFIxJ5AF8I56wdVIRA0Mo4Er3HABirIP4wgK4DFDt7XgFlpnhmhNCCE1xeJBYHAADIqfwSOAbKBoCvWHggUYtAAKJbkmawSlxvDw6ktAoA8vBW9PBLiE0A) 尝试一下上面的 Demo

## 相关项目

| 项目                  | 描述                                                       |
| --------------------- | ---------------------------------------------------------- |
| [gogocode-plugin-vue] | 通过这个 gogocode 插件可以把 vue2 语法的项目转换成 vue3 的 |
| [gogocode-cli]        | gogocode 的命令行工具                                      |
| [gogocode-playground] | 可以在浏览器里尝试 gogocode 转换                           |
| [gogocode-vscode]     | 在 vscode 中通过此插件用 gogocode 重构你的代码             |

[gogocode-plugin-vue]: https://github.com/thx/gogocode/tree/main/packages/gogocode-plugin-vue
[gogocode-cli]: https://github.com/thx/gogocode/tree/main/packages/gogocode-cli
[gogocode-playground]: https://play.gogocode.io
[gogocode-vscode]: https://marketplace.visualstudio.com/items?itemName=mmfe.vscode-gogocode

## 支持

-   [issues](https://github.com/thx/gogocode/issues)
-   钉钉群：34266233
-   QQ群：735216094

## 开源协议

[MIT](LICENSE)

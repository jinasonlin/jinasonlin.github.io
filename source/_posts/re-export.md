---
title: re-export 模块二次导出
date: 2017-07-15 15:00:20
tags:
	- 草稿
	- javascript
	- es6
---

## 关于模块
JavasSript在ES6规范提出之前，一直没有一个统一标准的模块规范。在此之前，通行的模块规范主要有两种：`CommonJS `和`AMD `。

  
- CommonJS  
	NodeJS 采用的模块化规范  
- AMD Asynchronous Module Definition（异步模块定义）  
	RequireJS 在推广过程中对模块定义的规范化的产出  


而本次讨论的主题，是模块化中的一小部分：`re-export` 二次倒出。简单的说，就是export和import的复合用法。

<!--more-->

## export
__[export 语句 用于从给定的文件 (或模块) 中导出函数，对象或原语。](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/export)__  
类是于CommonJS的`exports`和`module.exports`。  
结合ES6的语法，我们看看几个简单的例子。

```javascript
// export.js
export const name = 'jim';
export const sex = 'man';
export const getName = () => {
  return name;
};

const city = 'shanghai';
const district = 'huangpu';
export { city, district as dt };

export default () => {
  return `${city} ${district}`;
}
```

## import
__[import 语句 用于从一个已经导出的外部模块或另一个脚本中导入函数，对象或原始类型。](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/import)__  
类似于CommonJS的`require`。  
结合ES6的语法，我们看看几个简单的例子。

```javascript
// import.js
import getAddress, { getName } from 'export.js';
```

## re-export
export和import的复合用法，就是本次文章的主题。常用的几种re-export方式如下:  

### re-export外部模块中的成员，作为本模块的成员

```javascript
export { getName } from 'export.js';

export { getName as getname } from 'export.js';
```

### re-export外部模块中的全部成员，作为本模块的成员
```javascript
export * as myexport from 'export.js';
```

### re-export外部模块中的成员，作为本模块的default
```javascript
export { getAddress as default } from 'export.js';

```

### re-export外部模块中的default，作为本模块的成员
```javascript
export getAddress from 'export.js';

export { default as getAddress } from 'export.js';

```

### re-export外部模块中的default，作为本模块的default
```javascript
export { default } from 'export.js';

```













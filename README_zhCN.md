# H5 Pages
![][workflows-badge-image]
[![build status][travis-image]][travis-url]
[![libraries dependency status][libraries-status-image]][libraries-status-url]
[![libraries sourcerank][libraries-sourcerank-image]][libraries-sourcerank-url]
[![Coverage Status][coverage-image]][coverage-url]
[![Release date][release-date-image]][release-url]
[![rollup][rollup-image]][rollup-url]
[![semantic-release][semantic-image]][semantic-url]
[![jest][jest-image]][jest-url]
[![npm license][license-image]][download-url]

* H5 Pages 基于 swiper5+. ([Demo][github-pages-url])

语言: [En][Readme-url-En] | [中文][Readme-url-ZhCN]
***

## Install
[![NPM version][npm-image]][npm-url]
[![NPM bundle size][npm-bundle-size-image]][npm-url]
[![npm download][download-image]][download-url]

```shell
# via npm
$ npm install @cycjimmy/h5-pages --save

# or via yarn
$ yarn add @cycjimmy/h5-pages
```

## 使用
**h5-pages 基于 [Swiper5+](https://github.com/nolimits4web/Swiper). 首先将 swiper 加入你的工程**

### 函数 
#### `init`: 初始化函数
```javascript
import Swiper from 'swiper';
import {init} from '@cycjimmy/h5-pages';

init({
  Swiper,                                                       // Swiper的构造函数
  pages: [page1, page2],                                        // Page实例组成的数组
  containerExtraHtml: `<div class="swiper-pagination"></div>`,  // swiper-container下额外的Html，比如导航器等
  swiperOptions: {                                              // swiper的配置项
    direction: 'vertical',
    pagination: {
      el: '.swiper-pagination',
    },
  },
})
```

#### `Page`: 单页构造函数
##### 直接使用默认Page进行构建
```javascript
import {Page} from '@cycjimmy/h5-pages';

const page = new Page({
  name: 'page',                                         // 页面名称
  renderHtml: `<div class="page-wrapper">page</div>`,   // swiper-slide内的Html结构
  pageEnter: () => console.log('进入页面'),              // 进入页面的钩子函数
  pageLeave: () => console.log('离开页面'),              // 离开页面的钩子函数
});
```

##### 使用Page扩展(推荐)
```javascript
import {Page} from '@cycjimmy/h5-pages';

const page = new class extends Page {
  constructor() {
    super({
     name: 'page',
     renderHtml: `<div class="page-wrapper">page</div>`,
    });
  }

  // extraRender: 当页面加载完毕时，增加你自定义的操作
  extraRender() {
    console.log('pageLoaded');
  }

  // 其他你自定义的扩展
  // ... 
};
```

#### `singleton`: 将Page实例转化为单例模式(推荐)
```javascript
import {Page, singleton} from '@cycjimmy/h5-pages';

const page = singleton(class extends Page {
  constructor() {
    super({
     name: 'page',
     renderHtml: `page`,
    });
  }
});
```

### 可获取的
* `h5Pages.root`: 页面根元素，添加弹窗之类的页面请不要直接写在body里，推荐以root作为父级
* `h5Pages.swiper`: 页面主swiper实例 

## CDN
[![jsdelivr][jsdelivr-image]][jsdelivr-url]

To use via a CDN include this in your HTML:
```text
<script src="https://cdn.jsdelivr.net/npm/h5-pages@1/dist/h5-pages.umd.min.js"></script>
```

<!-- Links: -->
[npm-image]: https://img.shields.io/npm/v/@cycjimmy/h5-pages
[npm-url]: https://npmjs.org/package/@cycjimmy/h5-pages
[npm-bundle-size-image]: https://img.shields.io/bundlephobia/min/@cycjimmy/h5-pages

[download-image]: https://img.shields.io/npm/dt/@cycjimmy/h5-pages
[download-url]: https://npmjs.org/package/@cycjimmy/h5-pages

[jsdelivr-image]: https://img.shields.io/jsdelivr/npm/hy/@cycjimmy/h5-pages
[jsdelivr-url]: https://www.jsdelivr.com/package/npm/@cycjimmy/h5-pages

[workflows-badge-image]: https://github.com/cycjimmy/h5-pages/workflows/Test%20CI/badge.svg
[travis-image]: https://img.shields.io/travis/cycjimmy/h5-pages
[travis-url]: https://travis-ci.org/cycjimmy/h5-pages

[libraries-status-image]: https://img.shields.io/librariesio/release/npm/@cycjimmy/h5-pages
[libraries-sourcerank-image]: https://img.shields.io/librariesio/sourcerank/npm/@cycjimmy/h5-pages
[libraries-status-url]: https://libraries.io/github/cycjimmy/h5-pages
[libraries-sourcerank-url]: https://libraries.io/npm/@cycjimmy%2Fh5-pages

[coverage-image]: https://img.shields.io/coveralls/github/cycjimmy/h5-pages
[coverage-url]: https://coveralls.io/github/cycjimmy/h5-pages

[release-date-image]: https://img.shields.io/github/release-date/cycjimmy/h5-pages
[release-url]: https://github.com/cycjimmy/h5-pages/releases

[rollup-image]: https://img.shields.io/github/package-json/dependency-version/cycjimmy/h5-pages/dev/rollup
[rollup-url]: https://github.com/rollup/rollup

[semantic-image]: https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg
[semantic-url]: https://github.com/semantic-release/semantic-release

[jest-image]: https://img.shields.io/badge/tested_with-jest-99424f.svg
[jest-url]: https://github.com/facebook/jest

[license-image]: https://img.shields.io/npm/l/@cycjimmy/h5-pages

[github-pages-url]: https://cycjimmy.github.io/h5-pages/

[Readme-url-En]: https://github.com/cycjimmy/h5-pages/blob/master/README.md
[Readme-url-ZhCN]: https://github.com/cycjimmy/h5-pages/blob/master/README_zhCN.md
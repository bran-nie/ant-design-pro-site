---
order: 12
title: BIZ Icon
type: Advanced
---

You can use [Ant Design official icons](https://ant.design/components/icon/) with the `<Icon />` component. The basic usage is as follows.

```jsx
<Icon type="heart" style={{ fontSize: '16px', color: 'hotpink' }} />
```

If there is no icon you need in the Ant Design official icons, you can collect and generate your own icon library in the [iconfont.cn](http://iconfont.cn/).

## Generate the code from the icon library

First, search icons what you need, and add these icons into your shop bag. You can add these icons which you have selected to your project(if you don't have, just create one). All of resources and code are project-based in future.

> If you get a design spec, and just want to generate the code, you can do these steps above after uploading this icons to [iconfont.cn](http://iconfont.cn/).

<img width="600" alt="layout-on-account" src="https://gw.alipayobjects.com/zos/rmsportal/jJQYzRyqVFBBamUOppXH.png" />

<br />

In your project page, click the link『Click to generating Code, and it will automatically generate different codes.

<img width="600" alt="layout-on-account" src="https://gw.alipayobjects.com/zos/rmsportal/DbDSgiRukSANKWyhULir.png" />

## Quote icons

There're three different ways to Quote icons: SVG Symbol(Recommended), Unicode and Font class.

### SVG Symbol

It’s a new way of usage we recommend and will be the main trend in future. This usage is a collection of SVG and its characteristics as following:

- It supports multi-color and get rid of the limitation of monochrome.
- It could adjust the style by some technique just like font.
- It supports IE 9+ and modern browsers only.

General steps are as follows:

1. Switch to the page "Symbol", click to generating code and copy it：

```
//at.alicdn.com/t/font_405362_lyhvoky9rc7ynwmi.js
```

2. Add a common CSS code

```css
.icon {
  width: 1em;
  height: 1em;
  fill: currentColor;
  vertical-align: -0.125em;
}
```

3. Copy the individual code of icons into pages.

```html
<svg class="icon" aria-hidden="true">
  <use xlink:href="#icon-ali-pay"></use>
</svg>
```

You can also use the method `Icon.createFromIconfontCN({...})` to use icons more conveniently. The usage is as follows:

1. Set `scriptUrl` field and create icon component. See [usage](https://ant.design/components/icon/#API) for more detail.

```jsx
import { Icon } from 'antd';

const IconFont = Icon.createFromIconfontCN({
  scriptUrl: '//at.alicdn.com/t/font_405362_lyhvoky9rc7ynwmi.js',
});

export default IconFont;
```

2. It's easy to use like `<Icon />` component, and support inline style.

```jsx
<IconFont type="icon-ali-pay" style={{ fontSize: '16px', color: 'lightblue' }} />
```

### Unicode

Unicode is the most primitive way of font’s application. Its application steps as follows:

1. Copy the code generated by the icon project. You can create a new stylesheet file. The content is as follows:

   ```css
   @font-face {
     font-family: 'iconfont';
     src: url('//at.alicdn.com/t/font_405362_lyhvoky9rc7ynwmi.eot');
     src: url('//at.alicdn.com/t/font_405362_lyhvoky9rc7ynwmi.eot?#iefix') format('embedded-opentype'),
       url('//at.alicdn.com/t/font_405362_lyhvoky9rc7ynwmi.woff') format('woff'),
       url('//at.alicdn.com/t/font_405362_lyhvoky9rc7ynwmi.ttf') format('truetype'), url('//at.alicdn.com/t/font_405362_lyhvoky9rc7ynwmi.svg#iconfont')
         format('svg');
   }
   ```

2. Define the style of iconfont usage.

   ```css
   .iconfont {
     display: inline-block;
     font-style: normal;
     vertical-align: baseline;
     text-align: center;
     text-transform: none;
     line-height: 1;
     text-rendering: optimizeLegibility;
     -webkit-font-smoothing: antialiased;
     -moz-osx-font-smoothing: grayscale;
     &:before {
       display: block;
       font-family: 'iconfont' !important; /* 注意与 font-face 中的匹配 */
     }
   }
   ```

3. Copy the individual code of icon into pages.

   ```html
   <i class="iconfont">&#xe66b;</i>
   ```

### Font Class

Font-class is one kind of derived usage of Unicode, which solved the problems of intuitive writing and semantic ambiguity.

1. Switch to the page "Font class". Click to generating code and copy it.

```html
//at.alicdn.com/t/font_405362_lyhvoky9rc7ynwmi.css
```

> You can copy the content of the file in the link above to your own stylesheet file. You can also rewrite the class names if you don't like the default class names.

    ```diff
    - .icon-ali-pay:before { content: "\e66b"; }              // Before
    + .monitor-icon-alipay:before { content: "\e66b"; }       // After
    ```

2. Copy the individual code of icon into pages.

```html
<i class="iconfont icon-ali-pay"></i>
```

We recommend to package it as a component：

```js
import React from 'react';

const BizIcon = (props) => {
  const { type } = props;
  return <i className={`iconfont icon-${type}`} />;
};
export default BizIcon;
```

It's easy to use:

```jsx
<BizIcon type="ali-pay" />
```

Unicode and Font Class are font in essence. It's easy to adjust the style, and has good compatibility, but not support multi-color.

> More references:
>
> - [iconfont.cn Guide](http://iconfont.cn/help/detail?spm=a313x.7781069.1998910419.d8d11a391&helptype=code)
> - [New Web trend: use SVG instead of Web Icon Font](https://io-meter.com/2014/07/20/replace-icon-fonts-with-svg/)

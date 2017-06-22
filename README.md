# baseCss

### 意义

统一各个浏览器差异、统一团队开发起始标准、弥补浏览器的「缺点」、提供频繁使用的原子类名

### cdn 链接

[https://cdn.rawgit.com/hangyangws/baseCss/master/src/base.css](https://cdn.rawgit.com/hangyangws/baseCss/master/src/base.css)

### 友情提示

前端开发中如果不是 UI 特别要求，颜色值采用 web 安全色最佳，像素以偶数最佳  
移动端开发，量度可以尝试 rem 为单位「什么是 rem，请自行 Google」  
使用 rem 为量度单位时，浏览器会是基于 html 节点而不是 body 节点计算大小

### 代码解释

```css
/**
 * base.css
 * 航洋无声「hangyangws@foxmail.com、weibo.com/hangyangws」
 */


/**
 * 标准字体大小设置 14 像素（rem 参照对象）
 * html 根节点设置和浏览器一样高
 * 如果内容操作，滚动事件发生在 html 元素上
 * 背景颜色为白色
 */

html {
  font-size: 14px;
  overflow-y: auto;
  height: 100%;
  background-color: #fff;
}


/**
 * `body` 度大 `html` 度时，某些浏览器会出现内部滚动条，所以 `html、body` 置宽度100%
 * 给 html，body 一样的高度，防止 html 高度小于 body
 * 取消部分浏览器点击有阴影
 * 优化移动端滚动事件
 */

html,
body {
  overflow-x: hidden;
  width: 100%;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  -webkit-overflow-scrolling: touch;
  overflow-scrolling: touch;
}


/**
 * 设置基本字体配置
 * 如果绝对定位元素找不到被设置过定位信息的上级元素，那么此元素基于根节点定位，所以 `body` 置相对定位，让这些元素基 `body` 位
 * 默认 body 为 Y 轴自动滚动
 * 设置网页基本字体颜色 `#666`
 * 使字体渲染更顺滑
 */

body {
  font: 1rem 'Helvetica Neue', Helvetica, 'PingFang SC', 'Hiragino Sans GB', 'Microsoft Yahei', Arial, sans-serif;
  position: relative;
  color: #666;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
}


/**
 * 移除常用标签的浏览器默认 `margin、padding`
 * pre、code、legend、fieldset、blockquote ……等其他标签不是很常用，所以本 css 都不会一一列举出来，为了简化如果项目中用到，可以自己单独写
 */

body,
p,
h1,
h2,
h3,
h4,
h5,
h6,
dl,
dd,
ul,
ol,
th,
td,
button,
figure,
input,
textarea,
form {
  margin: 0;
  padding: 0;
}


/*不同浏览器的 input、select、textarea 的盒子模型宽度计算方式不通，统一为最常见的 content-box*/

input,
select,
textarea {
  -webkit-box-sizing: content-box;
  -moz-box-sizing: content-box;
  box-sizing: content-box;
}


/**
 * `table` 邻单元格的边框间的距离设置为0
 * 设 `table` 边框为合并模式
 */

table {
  border-spacing: 0;
  border-collapse: collapse;
}


/**
 * 移除浏览器部分元素的默认边框
 * acronym、fieldset … 等其他标签不是很常用，所以本 css 都不会一一列举出来，为了简化如果项目中用到，可以自己单独写
 */

img,
input,
button,
textarea {
  border: none;
  -webkit-appearance: none;
}


/*因 `input` 认不继承父元素的居中样式，所以 `input` 素继承父元素的文本居中方式*/

input {
  text-align: inherit;
}


/* `textarea` 认不可以放缩*/

textarea {
  resize: none;
}


/**
 * 由于以下元素的部分属性没有继承父节点样式，所以声明这些元素的这些属性为父元素的属性
 * 取消这些元素 `outline` 式
 */

a,
h1,
h2,
h3,
h4,
h5,
h6,
input,
select,
button,
option,
textarea,
optgroup {
  font-family: inherit;
  font-size: inherit;
  font-weight: inherit;
  font-style: inherit;
  line-height: inherit;
  color: inherit;
  outline: none;
}


/**
 * 取消超链接元素的默认文字装饰
 * 另外 del、ins 标签的中划线、下划线还是挺好的，就不去掉
 */

a {
  text-decoration: none;
}


/**
 * 开发中 UI 设计的列表都是和原生的样式差太多，所以直接给取消 ol，ul 默认列表样式
 */

ol,
ul {
  list-style: none;
}


/*使如下元素默认鼠标经过是 `小手` 形状「表示可以点击」*/

button,
input[type='submit'],
input[type='button'] {
  cursor: pointer;
}


/*取消火狐浏览器部分版 `input` 焦的时候默认 `padding、border`*/

input::-moz-focus-inner {
  padding: 0;
  border: 0;
}


/*取消部分浏览 `input[type='number']` 默认样式*/

input[type='number'] {
  -moz-appearance: textfield;
}

input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
  margin: 0;
  -webkit-appearance: none;
}


/*输入控件 `placeholder` 色设置 `#999`*/

input::-webkit-input-placeholder,
textarea::-webkit-input-placeholder {
  color: #999;
}

input:-moz-placeholder,
textarea:-moz-placeholder {
  color: #999;
}

input::-moz-placeholder,
textarea::-moz-placeholder {
  color: #999;
}

input:-ms-input-placeholder,
textarea:-ms-input-placeholder {
  color: #999;
}


/*由于部分浏览 `template` 接显示出来，所以要隐 `template` 素*/

template {
  display: none;
}
```

# public.css

项目中的公共样式，仅供参考

```css
/**
 * base.css
 * 航洋无声「hangyangws@foxmail.com、weibo.com/hangyangws」
 */


/**
 * 标准字体大小设置 14 像素（rem 参照对象）
 * html 根节点设置和浏览器一样高
 * 如果内容操作，滚动事件发生在 html 元素上
 * 背景颜色为白色
 */

html {
  font-size: 14px;
  overflow-y: auto;
  height: 100%;
  background-color: #fff;
}


/**
 * `body` 度大 `html` 度时，某些浏览器会出现内部滚动条，所以 `html、body` 置宽度100%
 * 给 html，body 一样的高度，防止 html 高度小于 body
 * 取消部分浏览器点击有阴影
 * 优化移动端滚动事件
 */

html,
body {
  overflow-x: hidden;
  width: 100%;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  -webkit-overflow-scrolling: touch;
  overflow-scrolling: touch;
}


/**
 * 设置基本字体配置
 * 如果绝对定位元素找不到被设置过定位信息的上级元素，那么此元素基于根节点定位，所以 `body` 置相对定位，让这些元素基 `body` 位
 * 默认 body 为 Y 轴自动滚动
 * 设置网页基本字体颜色 `#666`
 * 使字体渲染更顺滑
 */

body {
  font: 1rem 'Helvetica Neue', Helvetica, 'PingFang SC', 'Hiragino Sans GB', 'Microsoft Yahei', Arial, sans-serif;
  position: relative;
  color: #666;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
}


/**
 * 移除常用标签的浏览器默认 `margin、padding`
 * pre、code、legend、fieldset、blockquote ……等其他标签不是很常用，所以本 css 都不会一一列举出来，为了简化如果项目中用到，可以自己单独写
 */

body,
p,
h1,
h2,
h3,
h4,
h5,
h6,
dl,
dd,
ul,
ol,
th,
td,
button,
figure,
input,
textarea,
form {
  margin: 0;
  padding: 0;
}


/*不同浏览器的 input、select、textarea 的盒子模型宽度计算方式不通，统一为最常见的 content-box*/

input,
select,
textarea {
  -webkit-box-sizing: content-box;
  -moz-box-sizing: content-box;
  box-sizing: content-box;
}


/**
 * `table` 邻单元格的边框间的距离设置为0
 * 设 `table` 边框为合并模式
 */

table {
  border-spacing: 0;
  border-collapse: collapse;
}


/**
 * 移除浏览器部分元素的默认边框
 * acronym、fieldset … 等其他标签不是很常用，所以本 css 都不会一一列举出来，为了简化如果项目中用到，可以自己单独写
 */

img,
input,
button,
textarea {
  border: none;
  -webkit-appearance: none;
}


/*因 `input` 认不继承父元素的居中样式，所以 `input` 素继承父元素的文本居中方式*/

input {
  text-align: inherit;
}


/* `textarea` 认不可以放缩*/

textarea {
  resize: none;
}


/**
 * 由于以下元素的部分属性没有继承父节点样式，所以声明这些元素的这些属性为父元素的属性
 * 取消这些元素 `outline` 式
 */

a,
h1,
h2,
h3,
h4,
h5,
h6,
input,
select,
button,
option,
textarea,
optgroup {
  font-family: inherit;
  font-size: inherit;
  font-weight: inherit;
  font-style: inherit;
  line-height: inherit;
  color: inherit;
  outline: none;
}


/**
 * 取消超链接元素的默认文字装饰
 * 另外 del、ins 标签的中划线、下划线还是挺好的，就不去掉
 */

a {
  text-decoration: none;
}


/**
 * 开发中 UI 设计的列表都是和原生的样式差太多，所以直接给取消 ol，ul 默认列表样式
 */

ol,
ul {
  list-style: none;
}


/*使如下元素默认鼠标经过是 `小手` 形状「表示可以点击」*/

button,
input[type='submit'],
input[type='button'] {
  cursor: pointer;
}


/*取消火狐浏览器部分版 `input` 焦的时候默认 `padding、border`*/

input::-moz-focus-inner {
  padding: 0;
  border: 0;
}


/*取消部分浏览 `input[type='number']` 默认样式*/

input[type='number'] {
  -moz-appearance: textfield;
}

input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
  margin: 0;
  -webkit-appearance: none;
}


/*输入控件 `placeholder` 色设置 `#999`*/

input::-webkit-input-placeholder,
textarea::-webkit-input-placeholder {
  color: #999;
}

input:-moz-placeholder,
textarea:-moz-placeholder {
  color: #999;
}

input::-moz-placeholder,
textarea::-moz-placeholder {
  color: #999;
}

input:-ms-input-placeholder,
textarea:-ms-input-placeholder {
  color: #999;
}


/*由于部分浏览 `template` 接显示出来，所以要隐 `template` 素*/

template {
  display: none;
}
```

**感谢阅读**

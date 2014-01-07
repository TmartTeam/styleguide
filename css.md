# Tamrt.com 样式规范

---

## 目录

* [总则] (#总则)
* [文件结构] (#文件结构)
* [书写规范] (#书写规范)
  * [代码顺序] (#代码顺序)
  * [HTML 中的 class] (#HTML 中的 class)
  * [JavaScript 钩子] (#JavaScript 钩子)
 
---
### 总则

尽量将行宽控制在 80 字节以下。渐变（gradient）相关的语法以及注释中的 URL 等可以算作例外。

* 用 4 个空格而非 Tab 缩进，并且将声明拆分成多行。
* class 名称以连字符（-）连接，除了下文提到的 BEM 命名法；
* 声明拆分成多行；
* 声明以相关性顺序排列，而非字母顺序；
* 有前缀的声明适当缩进，从而对齐其值；
* 缩进样式从而反映 DOM；
* 保留最后一条声明结尾的分号。
* 在属性申明```:```之后用一个空格
* 在```{``` 之前用空格

比如:
```css
/* format style */
.styleguide-format {
  border: 1px solid #0f0;
  color: #000;
  background: rgba(0,0,0,0.5);
}
```
## 文件结构
  所有的CSS分为两大类：通用类和业务类
  *通用的CSS文件，放在如下目录中:
  <table width="300" style="margin-left:60px;">
  <tbody><tr><td> 基本样式库 </td><td style="text-align: left"> /css/core 
  </td></tr><tr><td> 通用UI元素样式库 </td><td style="text-align: left"> /css/lib
  </td></tr><tr><td> JS组件相关样式库 </td><td style="text-align: left"> /css/ui
  </td></tr></tbody>
  </table>
  <table width="300" style="margin-left:60px;">
  <tbody>
  <tr>
  <td> /css/core <br>
  [参考github文件命名](https://github.com/styleguide/css)</td>
  <td style="text-align: left"> 
* [rest.css]
* [bottons.css](https://github.com/styleguide/css/1.0)
* [forms.css](https://github.com/styleguide/css/2.0)
* [color.css](https://github.com/styleguide/css/11.0)
* [alert.css](https://github.com/styleguide/css/15.0)
* [navigation.css](https://github.com/styleguide/css/8.0)
  </td>
  </tr><tr><td> /css/lib </td><td style="text-align: left"> 
  </td></tr><tr><td>  /css/ui </td><td style="text-align: left"> 
  </td></tr></tbody>
  </table>
 
## 书写规范
### 代码顺序
1. **元素类型** 没有 class 的 `h1`、`ul` 等
2. **对象以及抽象内容** 最一般、最基础的设计模式
3. **子元素** 由对象延伸出来的所有拓展及其子元素
4. **修补** 针对异常状态
### 命名规范
一般情况下我都是以连字符（-）连接 class 的名字（例如 `.foo-bar` 而非 `.foo_bar` 或 `.fooBar`），不过在某些特定的时候我会用 BEM（Block, Element, Modifier）命名法。

<abbr title="Block, Element, Modifier">BEM</abbr> 命名法可以使得选择器更规范，更清晰，更具语义。

该命名法按照如下格式：

    .block{}
    .block__element{}
    .block--modifier{}

其中：

* `.block` 代表某个基本的抽象元素；
* `.block__element` 代表 `.block` 这一整体的一个子元素；
* `.block--modifier` 代表 `.block` 的某个不同状态。

### HTML 中的 class

为了确保易读性，在 HTML 标记中用两个空格隔开 class 名，例如：

    <div class="foo-bar  bar-baz">

增加的空格应当可以使得在使用多个 class 时更易阅读与定位。

### JavaScript 钩子

**千万不要把 CSS 样式用作 JavaScript 钩子。**把 JS 行为与样式混在一起将无法对其分别处理。

如果你要把 JS 和某些标记绑定起来的话，写一个 JS 专用的 class。简单地说就是划定一个前缀 `.js-` 的命名空间，例如 `.js-toggle`，`.js-drag-and-drop`。这意味着我们可以通过 class 同时绑定 JS 和 CSS 而不会因为冲突而引发麻烦。

    <th class="is-sortable  js-is-sortable">
    </th>

上面的这个标记有两个 class，你可以用其中一个来给这个可排序的表格栏添加样式，用另一个添加排序功能。

### I18n
为了统一，把所有的 class 与变量都以你参与的项目的惯用拼法命名即可。

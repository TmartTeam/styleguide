# Tamrt 样式规范

---

## 目录

* [总则] (#总则)
* [文件结构] (#文件结构)
* [书写规范] (#书写规范)
  * [代码顺序] (#代码顺序)
  * [HTML 中的 class] (#HTML 中的 class)
  * [JavaScript 钩子] (#JavaScript 钩子)
* [编写CSS] (#编写 CSS)

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
    .block-element{}
    .block-modifier{}

其中：

* `.block` 代表某个基本的抽象元素；
* `.block-element` 代表 `.block` 这一整体的一个子元素；
* `.block-modifier` 代表 `.block` 的某个不同状态。

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

## 编写 CSS

### 编写新组件

编写新组件时，要在着手处理 CSS <strong>之前</strong>写好 HTML 部分。这可以令你准确判断哪些 CSS 属性可以继承，避免重复浪费。

先写标记的话，你就可以关注数据、内容与语义，在这之后再添加需要的 class 和 CSS 样式。

### 面向对象 CSS

以面向对象 CSS 的方式写代码。我把组件分成结构（对象）与外观（拓展）。正如以下分析：

    .room{}
    
    .room--kitchen{}
    .room--bedroom{}
    .room--bathroom{}

共同的部分：ch抽象到 `.room{}` class 中。其中它包含了`kitchen`,`bedroom`, `bathroom`
**向对象 CSS 的思路使得我们把相同部分抽象出来组成结构部分，然后用更具体的 class 来拓展这些特征并添加特殊的处理方法。**

所以比起编写大量的特殊模块，应当努力找出这些模块中重复的设计模式并将其抽象出来，写成一个可以复用的 class，将其用作基础然后编写其它拓展模块的特殊情形。

当你要编写一个新组件时，将其拆分成结构和外观。编写结构部分时用最通用 class 以保证复用性，编写外观时用更具体的 class 来添加设计方法。

### 布局

所有组件都不要声明宽度，而由其亲元素或格栅系统来决定。

**坚决不要**声明高度。高度应当仅仅用于尺寸已经固定的东西，例如图片和 CSS Sprite。在 `p`，`ul`，`div` 等元素上不应当声明高度。如果需要的话可以写 `line-height`，这个更加灵活。

格栅系统应当当作书架来理解。是它们容纳内容，而不是把它们本身当成内容装起来，正如你先搭起书架再把东西放进去。比起声明它们的尺寸，把格栅系统和元素的其它属性分来开处理更有助于布局，也使得我们的前端工作更高效。

你在格栅系统上不应当添加任何样式，他们仅仅是为布局而用。在格栅系统内部再添加样式。在格栅系统中任何情况下都不要添加盒模型相关属性。

### UI 尺寸
使用`px` 作为统一的尺寸，因为他提供了对文本的的绝对控制


### 简写

**CSS 简写应当谨慎使用。**
    
编写像 `background:red;` 这样的属性的确很省事，但是你这么写的意思其实是同时声明 `background-image:none; background-position:top left; background-repeat: repeat; background-color:red;`。虽然大多数时候这样不会出什么问题，但是哪怕只出一次问题就值得考虑要不要放弃简写了。这里应当改为 `background-color:red;`。

类似的，像 `margin:0;` 这样的声明的确简洁清爽，但是还是应当<strong>尽量写清楚</strong>。如果你只是想修改底边边距，就要具体一些，写成 `margin-bottom:0;`。

反过来，你需要声明的属性也要写清楚，不要因为简写而波及其它属性。例如如果你只想改掉底部的 `margin`，那就不要用会把其它边距也清零的 `margin:0`。

简写虽然是好东西，但是注意切勿滥用。

### ID

在我们开始处理选择器之前，牢记这句话：

**在 CSS 里坚决不要用 ID。**

在 HTML 里 ID 可以用于 JS 以及锚点定位，但是在 CSS 里只要用 class，一个 ID 也不要用。

Class 的优势在于复用性，而且私有度也并不高。私有度非常容易导致问题，所以将其降低就尤为重要。ID 的私有度是 class 的 **255** 倍，所以在 CSS 中坚决不要使用。

### 选择器

务必保持选择器简短高效。

通过页面元素位置而定位的选择器并不理想。例如 `.sidebar h3 span{}` 这样的选择器就是定位过于依赖相对位置，所以把 span 移到 h3 和 sidebar 外面时就很难保持其样式。

结构复杂的选择器将会影响性能。选择器结构越复杂（如 `.sidebar h3 span` 为三层，`.content ul p a` 是四层），浏览器的消耗就越大。

尽量使得样式不依赖于其定位，尽量保持选择器简洁清晰。

作为一个整体，选择器应当尽量简短（例如只有一层结构），但是 class 名则不应当过于简略，例如 `.user-avatar` 就远比 `.usr-avt` 好。

**牢记：**class 无所谓是否语义化；应当关注它们是否合理。不要强调 class 名要符合语义，而要注重使用合理且不会过时的名称。

### 过度修饰的选择器

由前文所述，过度修饰的选择器并不理想。

过度修饰的选择器是指像 `div.promo` 这样的。很可能你只用 `.promo` 也能得到相同的效果。当然你可能偶尔会需要用元素类型来修饰 class（例如你写了一个 `.error` 而且想让它在不同的元素类型中显示效果不一样，例如 `.error{ color:red; }` `div.error{ padding:14px;}`），但是大多数时候还是应当尽量避免。

再举一个修饰过度的选择器例子，`ul.nav li a{}`。如前文所说，我们马上就可以删掉 `ul` 因为我们知道 `.nav` 是个列表，然后我们就可以发现 `a` 一定在 `li` 中，所以我们就能将这个选择器改写成 `.nav a{}`。

### 选择器性能

虽然浏览器性能日渐提升，渲染 CSS 速度越来越快，但是你还是应当关注效率。使用间断、没有嵌套的选择器，不把全局选择器（`*{}`）用作核心选择器，避免使用日渐复杂的 CSS3 新选择器可以避免这样的问题。

*核心选择器：浏览器解析选择器为从右向左的顺序，最右端的元素是样式生效的元素，是为核心选择器。

### 使用 CSS 选择器的目的

比起努力运用选择器定位到某元素，更好的办法是直接给你想要添加样式的元素直接添加一个 class。我们以 `.header ul{}` 这样一个选择器为例。

假定这个 `ul` 就是这个网站的全站导航，它位于 header 中，而且目前为止是 header 中唯一的 `ul` 元素。`.header ul{}` 的确可以生效，但是这样并不是好方法，它很容易过时，而且非常晦涩。如果我们在 header 中再添加一个 `ul` 的话，它就会套用我们给这个导航部分写的样式，哪怕我们设想的不是这个效果。这意味着我们要么要重构许多代码，要么给后面的 `ul` 新写许多样式来抵消之前的影响。

你的选择器必须符合你要给这个元素添加样式的原因。思考一下，<strong>「我定位到这个元素，是因为它是 `.header` 下的 `ul`，还是因为它是我的网站导航？」</strong>这将决定你应当如何使用选择器。

确保你的核心选择器不是类型选择器，也不是高级对象或抽象选择器。例如你在我们的 CSS 中肯定找不到诸如 `.sidebar ul{}` 或者 `.footer .media{}` 这样的选择器。

表达清晰：直接找到你要添加样式的元素，而非其亲元素。不要想当然地认为 HTML 不会改变。<strong>用 CSS 直接命中你需要的元素，而非投机取巧。</strong>


### `!important`

只在起辅助作用的 class 上用 `!important`。用 `!important` 提升优先级也可以，例如如果你要让某条规则<strong>一直</strong>生效的话，可以用 `.error{ color:red!important; }`。

避免主动使用 `!important`。例如 CSS 写得很复杂时不要用它来取巧，要好好整理并重构之前的部分，保持选择器简短并且避免用 ID 将效果拔群。

### 魔数与绝对定位

魔数（Magic Number）是指那些「凑巧有效果」的数字，这东西非常不好，因为它们只是治标不治本而且缺乏拓展性。

例如 `.dropdown-nav li:hover ul{ top:37px; }` 把下拉菜单移动下来远非良策，因为这里的 37px 就是个魔数。37px 会生效的原因是因为这时 `.dropbox-nav` 碰巧高 37px 而已。

这时你应该用 `.dropdown-nav li:hover ul{ top:100%; }`，也即无论 `.dropbox-down` 多高，这个下拉菜单都会往下移动 100%。

每当你要在代码中放入数字的时候，请三思而行。如果你能用一个关键字（例如  `top:100%` 意即「从上面拉到最下面」）替换之，或者有更好的解决方法的话，就尽量避免直接出现数字。

你在 CSS 中留下的每一个数字，都是你许下而不愿遵守的承诺。

### 条件判断

专门为 IE 写的样式基本上都是可以避免的，唯一需要为 IE 专门处理的是为了处理 IE 不支持的内容（例如 PNG）。

简而言之，如果你重构 CSS 的话，所有的布局和盒模型都不用额外兼容 IE。也就是说你基本上不用 `<!--[if IE 7]> element{ margin-left:-9px; } < ![endif]-->` 或者类似的兼容 IE 的写法。 

### Debugging

如果你要解决 CSS 问题的话，<strong>先把旧代码拿掉再写新的</strong>。如果旧的 CSS 中有问题的话，写新代码是解决不了的。

把 CSS 代码和 HTML 部分删掉，直到没有 BUG 为止，然后你就知道问题出在哪里了。

有时候写上一个 `overflow:hidden` 或者其它能把问题藏起来的代码的确效果立竿见影，但是 overflow 方面可能根本就没问题。所以<strong>要治本，而不是单纯治标</strong>。

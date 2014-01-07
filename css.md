# Tamrt.com 样式规范

---

## 目录

* [总则] (#总则)
* [文件结构] (#文件结构)
* [书写规范]
  * [注解]
  * [代码顺序]
  * [命名规范]
 
---
### 总则

尽量将行宽控制在 80 字节以下。渐变（gradient）相关的语法以及注释中的 URL 等可以算作例外。

用 4 个空格而非 Tab 缩进，并且将声明拆分成多行。

### 文件结构
  所有的CSS分为两大类：通用类和业务类
  *通用的CSS文件，放在如下目录中:
  <table width="300" style="margin-left:60px;">
  <tbody><tr><td> 基本样式库 </td><td style="text-align: left"> /css/core 
  </td></tr><tr><td> 通用UI元素样式库 </td><td style="text-align: left"> /css/lib
  </td></tr><tr><td> JS组件相关样式库 </td><td style="text-align: left"> /css/ui
  </td></tr></tbody>
  </table>
  * [/css/core/rest.css]
  * [/css/core/bottons.css]
  * [/css/core/forms.css]
  * [/css/core/color.css]
  * [/css/core/alert.css]
  * [/css/core/navigation.css]
  
